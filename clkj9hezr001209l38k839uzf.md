---
title: "[CSS] Box Model"
seoTitle: "[CSS] Box Model"
seoDescription: "This article will introduce the CSS box model, which we can use when designing the website layout. Also, we will talk about box-sizing CSS property."
datePublished: Wed Jul 26 2023 05:04:39 GMT+0000 (Coordinated Universal Time)
cuid: clkj9hezr001209l38k839uzf
slug: css-box-model
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690340719595/8607e2b0-7697-40d3-9781-5a4538d6144d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690347838764/5c41c406-19ce-493d-b7f8-da261ddeadaa.png
tags: css, web-development, html5, box-model, box-sizing

---

---

## Introduction

This article will introduce the CSS box model, which we can use when designing the website layout.

Every HTML element, such as `<div>` is wrapped around the box, which consists of padding, border and margin.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690344363782/d9045a0a-fdb5-4852-b291-fca58ca367f2.png align="center")

---

## Box Model - Padding, Border, Margin

As said earlier, the box model consists of padding, border, margin and content. Content is basically where the content of an element goes in.

**Content**

* The content of the box, where text and images appear.
    

**Padding**

* Clears an area around the content.
    
* The padding is transparent.
    

**Border**

* A border that goes around the padding and content.
    

**Margin**

* Clears an area outside the border.
    
* The margin is transparent
    

---

## Example

CSS:

```css
.box1 {
    padding: 10px;
    border: 10px solid green;
    margin: 10px;
}

.box2 {
    padding: 5px;
    border: 5px solid red;
    margin: 5px;
}
```

HTML:

```xml
<div class="box1">
    <div class="box2">CSS box model</div>
</div>
```

Result:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690345828973/8271b705-bf86-4562-a77e-65af328a7bfb.png align="center")

---

## Playing with Box Model

To help you to better understand the box model, open the developer tool on the Chrome browser by pressing F12. Then, go to elements.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690345988979/603ab1c5-2d9f-4e48-8adf-bb79792e2e11.png align="center")

Internet browsers provide you with the box model for each HTML element. Simply just select the HTML element you want, then put your mouse cursor on the box model. It will highlight the part you have chosen.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690346124105/59e193b1-b1f8-48bc-b1ec-17d1a853d363.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690346140328/e04aeeb2-79dd-48a6-ac4f-54f2577f2fa0.png align="center")

---

## Box-Sizing

`box-sizing` CSS property sets how the total width and height of an element is calculated. If you were to give a width of 200px on a certain element, the width is only applied to the content box.

For example:

```css
div {
    width: 400px;
    border: 5px dashed black;
    margin: 10px;
    padding: 30px;
    background-color: lightgreen;
}
```

```xml
<body>
    <div>Some content</div>
</body>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690347525002/421db3bd-2c0e-4660-909d-831c89368650.png align="center")

The total width of this box model is 470 px because...

```css
400px + (30px  2) + (5px * 2) = 470px
```

As I said before, the width is only applicable to the content box, which makes us confusing. We would have to calculate the total width every time.

To solve this problem, we can use `box-sizing` CSS property.

```css
div {
    width: 400px;
    border: 5px dashed black;
    margin: 10px;
    padding: 30px;
    background-color: lightgreen;
    box-sizing: border-box; /* new!!! */
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690347354783/88272e17-7490-46ec-a2e6-b75ce575b244.png align="center")

The total width is now 400px, which includes the border and padding. With this, it is much easier to work on the design and layout of a web page.

---

## Reference

[https://www.w3schools.com/css/css\_boxmodel.asp](https://www.w3schools.com/css/css_boxmodel.asp)

[https://developer.mozilla.org/en-US/docs/Learn/CSS/Building\_blocks/The\_box\_model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model)