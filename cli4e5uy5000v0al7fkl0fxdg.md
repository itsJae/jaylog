---
title: "[JavaScript] Tutorial for Sorting Table by Column - CRUD"
seoTitle: "[JavaScript] Tutorial for Sorting Table by Column - CRUD"
seoDescription: "I will demonstrate how to sort your table by column. After reading this article, you will be able to sort your table when you click the header of column."
datePublished: Fri May 26 2023 09:59:40 GMT+0000 (Coordinated Universal Time)
cuid: cli4e5uy5000v0al7fkl0fxdg
slug: javascript-tutorial-for-sorting-table-by-column-crud
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685087876905/3a081488-9e06-4906-9445-4ed254daaf88.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685095149480/849025ef-b3e5-44ff-8a17-e2a853b98870.webp
tags: javascript, web-development, html5, sorting, crud

---

---

## Introduction

In this article, I will demonstrate how to sort your table by column. After reading this article, you will be able to sort your table when you click on the header of a column.

We will be making something similar to this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685088256658/2d66d933-6d52-4fdd-8c2e-30c0ecb45b6f.png align="center")

By clicking the **Name** header, the name of users is sorted in an ascendingder. If you click it one more time, it is in a descending order.

**Descending order:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685088343537/52cf5d80-ce38-412a-85e9-66a986be780d.png align="center")

---

## Creating Table

Before building a program to sort the data in ascending or descending order, we need to make a table. We will need json-server and connect to it to retrieve the data and create a table with those data.

You can go here: [https://json-generator.com/](https://json-generator.com/) to generate sample data. Or you can use copy and paste this:

```javascript
{
    "customer" = [
        {
          "name": "John Doe",
          "gender": "male",
          "company": "Netflix",
          "email": "johndoe@gmail.com",
          "phone": "010-0101-0101",
          "address": "Some address",
          "id": "YqTkBPE"
        },
        {
          "id": "646e1dc18a5dbc6d66aa0229",
          "name": "Mcclain Norris",
          "gender": "male",
          "company": "QUARMONY",
          "email": "mcclainnorris@quarmony.com",
          "phone": "+1 (923) 529-2472",
          "address": "781 McKibbin Street, Charco, Rhode Island, 6909",
        },
        {
          "id": "646e1dc17576baf35c19f84f",
          "name": "Macias Blankenship",
          "gender": "male",
          "company": "COMVERGES",
          "email": "maciasblankenship@comverges.com",
          "phone": "+1 (910) 403-3638",
          "address": "966 Hanover Place, Matheny, Connecticut, 3758",
        },
        {
          "id": "646e1dc1359ae85c57e78b7e",
          "name": "Mcdaniel Tucker",
          "gender": "male",
          "company": "ZEROLOGY",
          "email": "mcdanieltucker@zerology.com",
          "phone": "+1 (864) 583-2885",
          "address": "468 Forrest Street, Zeba, Tennessee, 8446",
        },
        {
          "id": "646e1dc197737d93271c044b",
          "name": "Melinda Lang",
          "gender": "female",
          "company": "JOVIOLD",
          "email": "melindalang@joviold.com",
          "phone": "+1 (890) 423-3207",
          "address": "850 Creamer Street, Independence, Ohio, 4421",
        },
    ]
}
```

Table:

```xml
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
        <style>
            .normal-table {
                border: 1px solid black;
                border-collapse: collapse;
                width: 100%;
            }

            .normal-table th,
            .normal-table td {
                border: 1px solid black;
                padding: 5px 10px;
            }

            .normal-table thead tr {
                background-color: yellow;
            }
        </style>
    </head>
    <body>
        <table class="normal-table">
            <thead>
                <tr>
                    <th><input type="checkbox" name="" id="" /></th>
                    <th data-sort-key="name">Name</th>
                    <th data-sort-key="company">Company</th>
                    <th data-sort-key="gender">Gender</th>
                    <th data-sort-key="email">Email</th>
                    <th data-sort-key="phone">Phone</th>
                    <th data-sort-key="address">Address</th>
                </tr>
            </thead>
        </table>
        <script></script>
    </body>
</html>
```

You will get this table:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685092205690/f15a0ffa-f452-4554-9ef8-70db279d8660.png align="center")

`data-sort-key` attribute in `<th>` tag is a custom data attribute. We will be using it to add an onclick event listener and sort the column the user clicks on the header of a column.

---

## Getting the Data from JSON Server

Now let's key in some values in the table:

```javascript
// JavaScript code
let customerData = [];
async function doSearch() {
    // GET Method
    const res = await fetch("http://localhost:3000/customers");
    const resJson = await res.json();
    customerData = resJson;
    renderTable(resJson);
}

function renderTable(data) {
    const users = [];
    for (const user of data) {
        users.push("<tr>");
        users.push(`<td><input type="checkbox" name="chk" value="${user.id}"</td>`);
        users.push(`<td>${data.name}</td>`);
        users.push(`<td>${data.company}</td>`);
        users.push(`<td>${data.gender}</td>`);
        users.push(`<td>${data.email}</td>`);
        users.push(`<td>${data.phone}</td>`);
        users.push(`<td>${data.address}</td>`);
        users.push("</tr>");
    }
    document.querySelector("#tableBody").innerHTML = users.join("");
}
```

`doSearch()` will be called when the `click` event happens on the Search button. The function will get all the users' data and pass it to the `renderTable()`.

Then, `renderTable()` draws a table on the webpage. I created an empty array and added the data to the array so that it can go into the HTML element with `id = "#tableBody"` .

Please make sure:

1. that you joined the table.
    
2. that you added customerData array - it will be used later on.
    

When you click the search button, you will get the data of each user in each row.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685092420642/906f928b-dc3a-41b4-bee0-2c78e9bc3b10.png align="center")

---

## Sorting Table by Column

```javascript
let lastSortKey = ""
let isAsc = true;
function sort(sortKey) {
    if (lastSortKey === sortKey) {
        isAsc = !isAsc; // true -> false & false -> true.
    }
    let sortValue = isAsc ? 1 : -1;

    const sortData = customerData.sort(function(a, b) {
        if (a[sortKey].toLowerCase() > b[sortKey].toLowerCase()) {
            return sortValue;
        } else if (a[sortKey].toLowerCase() < b[sortKey].toLowerCase()) {
            return sortValue * -1;
        } else {
            return 0;
        }
    });
    renderTable(sortData);
    lastSortKey = sortKey;
}
```

I declared two variables in the global scope, which are `lastSortKey` and `isAsc`.

The two variables are to allow users to sort the column by ascending or descending. Without them, users will only be able to sort it by ascending order.

```javascript
if (lastSortKey === sortKey) {
    isAsc = !isAsc; // true -> false & false -> true.
}
```

if the values are the same, that means the user has clicked on the header of the column again, which means we need to switch from ascending to descending **OR** from descending to ascending. `!isAsc` will give the opposite of the current value.

```javascript
lastSortKey = sortKey;
```

By doing this at the end of the function, we can check if the user has clicked the column header again.

For example:

1. Current sortKey is name
    
2. Then, lastSortKey = name
    
3. The user clicks on the company column -&gt; sortKey = company
    
    * if (lastSortKey === sortKey) is not true -&gt; displays data in ascending order.
        
4. Then lastSortKey = company
    
5. The user clicks on the company column **AGAIN** \-&gt; sortKey = company
    
    * if (lastSortKey === sortKey) is true -&gt; displays data in descending order.
        

---

## And...

If you are not sure about any codes in this article, please leave me a comment.