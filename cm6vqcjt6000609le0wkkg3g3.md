---
title: "[Python Debugging] Beautiful Soup Error - AttributeError: 'NoneType' object has no attribute 'text'"
seoTitle: "[Python Debugging] Beautiful Soup Error - AttributeError: 'NoneType' o"
seoDescription: "The AttributeError occured because div does not exist in soup variable. So, why does soup not have div? It’s because the web server refused my request."
datePublished: Sat Feb 08 2025 05:03:31 GMT+0000 (Coordinated Universal Time)
cuid: cm6vqcjt6000609le0wkkg3g3
slug: beautifulsoup-debugging-none-type
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738988096239/1cf9887e-104f-4bde-927c-9b561af0831b.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1738990676269/cb2a6fd1-939c-4f07-92a8-f6282ee2ec31.png
tags: python, debugging, beautifulsoup, web-crawling, crawler, attributeerror

---

---

## Error

I was writing a code to crawl a website, and `AttributeError: 'NoneType' object has no attribute 'text'` occured.

My Code:

```python
import requests
from bs4 import BeautifulSoup

param = {
    'isDetailSearch': 'N',
    'searchGubun': 'true',
    'viewYn': 'OP',
    'order': '/DESC',
    'onHanja': 'false',
    'strSort': 'RANK',
    'iStartCount': 0,
    'fsearchMethod': 'search',
    'sflag': 1,
    'isFDetailSearch': 'N',
    'pageNumber': 1,
    'icate': 're_a_kor',
    'colName': 're_a_kor',
    'pageScale': 10,
    'isTab': 'Y'
}

response = requests.get("https://www.riss.kr/search/Search.do", params=param)
html = response.text
soup = BeautifulSoup(html, 'html.parser')
articles = soup.select('.srchResultListW > ul > li')

for article in articles:
    title = article.select_one('.title > a').text
    link = "https://www.riss.kr" + article.select_one('.title > a').attrs.get('href')

    response = requests.get(link)
    html = response.text
    soup = BeautifulSoup(html, 'html.parser')
    press = soup.select_one('.infoDetailL > ul > li:nth-of-type(2) > div').text
```

Error Message:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738988880726/9241263c-604a-4444-a234-b2b768f92d93.png align="center")

The message shows that 38th line, which is `press = soup.select_one()` got some problems.

---

## Solution

The `AttributeError` occured because `div` does not exist in `soup` variable. So, why does soup not have div? It’s because the web server refused my request.

There are three cases that the server refuses the request.

1. Status code 200 → BUT, returned HTML is not what we want
    
2. Status code 4xx
    
3. Infinite loop
    

To solve this issue, we can add a header, such as ***User-Agent*** or ***Referer***.

* User-Agent is to trick the website that this request is from the web browser.
    
* Referer tells the url that sent the request.
    

You can get the header by:

1. Open a devtools in your web browser
    
2. Go to the network tab.
    
3. Scroll to the top, and select the first.
    
4. Select “Headers”
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738990424371/679322d3-7f21-4d15-858c-9538637c75a8.png align="center")

5. Now you can check the ***User-Agent*** & ***Referer***.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738990494157/a7db5e10-3850-45cd-97b4-559d264d45cb.png align="center")

Solution Code:

```python
import requests
from bs4 import BeautifulSoup

param = {
    'isDetailSearch': 'N',
    'searchGubun': 'true',
    'viewYn': 'OP',
    'order': '/DESC',
    'onHanja': 'false',
    'strSort': 'RANK',
    'iStartCount': 0,
    'fsearchMethod': 'search',
    'sflag': 1,
    'isFDetailSearch': 'N',
    'pageNumber': 1,
    'icate': 're_a_kor',
    'colName': 're_a_kor',
    'pageScale': 10,
    'isTab': 'Y',
}

response = requests.get("https://www.riss.kr/search/Search.do", params=param)
html = response.text
soup = BeautifulSoup(html, 'html.parser')
articles = soup.select('.srchResultListW > ul > li')

# HEADER
header = {
    'User-Agent': 'Mozilla/5.0',
    'Referer': 'https://www.riss.kr/search/Search.do?isDetailSearch=N&searchGubun=true&viewYn=OP&queryText=&strQuery=%ED%8C%A8%EC%85%98+%EC%9D%B8%EA%B3%B5%EC%A7%80%EB%8A%A5&exQuery=&exQueryText=&order=%2FDESC&onHanja=false&strSort=RANK&p_year1=&p_year2=&iStartCount=0&orderBy=&mat_type=&mat_subtype=&fulltext_kind=&t_gubun=&learning_type=&ccl_code=&inside_outside=&fric_yn=&db_type=&image_yn=&gubun=&kdc=&ttsUseYn=&l_sub_code=&fsearchMethod=search&sflag=1&isFDetailSearch=N&pageNumber=1&resultKeyword=&fsearchSort=&fsearchOrder=&limiterList=&limiterListText=&facetList=&facetListText=&fsearchDB=&icate=re_a_kor&colName=re_a_kor&pageScale=100&isTab=Y&regnm=&dorg_storage=&language=&language_code=&clickKeyword=&relationKeyword=&query=%ED%8C%A8%EC%85%98+%EC%9D%B8%EA%B3%B5%EC%A7%80%EB%8A%A5'
}

for article in articles:
    title = article.select_one('.title > a').text
    link = "https://www.riss.kr" + article.select_one('.title > a').attrs.get('href')
    
    # Set headers=header
    response = requests.get(link, headers=header)
    html = response.text
    soup = BeautifulSoup(html, 'html.parser')

    press = soup.select_one('.infoDetailL > ul > li:nth-of-type(2) > div').text
```

I added a `header` including ‘User-Agent’ and ‘Referer‘, and set `response = requests.get(link, headers=header)`