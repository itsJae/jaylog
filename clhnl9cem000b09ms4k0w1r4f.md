---
title: "[CSS] Pseudo-Classes - Explained with Examples"
seoTitle: "[CSS] Pseudo Class - Explained with Examples"
seoDescription: "hover, link, focus, visited. CSS selectors."
datePublished: Sun May 14 2023 15:46:15 GMT+0000 (Coordinated Universal Time)
cuid: clhnl9cem000b09ms4k0w1r4f
slug: css-pseudo-classes-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684077528801/193cc536-9b07-47ed-b840-8e8f9ffed373.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684077576927/e0eb00f2-96c0-40a5-b1d3-c8a3736db6f7.jpeg
tags: programming-blogs, css, web-development, selectors, pseudo-classes

---

---

## Introduction

A pseudo-class is used to define a special state of an element. It is used to give a style to the element when a certain event happens. For example, you might have seen that a non-visited link is a blue color, but a visited link is a purple color

Example:

![✎ Technique: Visited links | Digital Accessibility​](https://accessibility.huit.harvard.edu/sites/hwpi.harvard.edu/files/styles/os_files_medium/public/online-accessibility-huit/files/visited_conventional.png?m=1515609185&itok=RKppNvDT align="left")

This can be done by using pseudo-classes which we will be introduced in this article.

Pseudo-classes that will be covered:

1. hover - when a user puts a mouse cursor on the selected area.
    
2. link - when there is an unvisited link.
    
3. visited - when there is a visited link.
    

\*These three(3) pseudo-classes except focus are mostly used with the &lt;a&gt; tag.

---

1. focus - when there is a focus by the user.
    
2. active - when an element is activated by the user.
    

\*focus is often used with an input box.

\*active is often used with a button.

---

1. nth-child(2n+1) & nth-child(2n) - gives a style to either odd or even child.
    
2. first-child - gives a style only to the first child.
    
3. last-child - gives a style only to the last child.
    

\*These three(3) pseudo-classes are often used with tables and lists (where there is a parent and child relationship)

---

## Anchor Pseudo-classes

HTML code:

```xml
<a href="https://google.com">Google</a>
<br />
<a href="https://exampleweb.com">Dummy Web</a>
```

CSS code:

```css
a:hover {
    background-color: greenyellow;
}

a:link {
    color: blue;
}

a:visited {
    color: purple;
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684079156394/e09d592f-89b2-4a6c-a420-403d1796a374.png align="left")

hover effect:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684079240038/285b836f-094b-468c-aa7c-75c60d9a0fd6.png align="left")

---

## :focus

focus effect occurs when a user gives a focus on a certain element.

HTML code:

```xml
<input type="text" name="" id="" />
```

CSS code:

```css
input:focus {
    border: 2px solid black;
}
```

When there is a focus:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684079508511/d533ede2-cf5f-47ff-b70f-e391a1866632.png align="left")

Without a focus effect:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684079487220/d103755e-c276-4d79-8445-715a9481da3c.png align="left")

Do you notice that the border is thicker when there is a mouse cursor focus?

---

## :active

active effect occurs when the user clicks a button or whenever the user activates the element.

HTML code:

```xml
<button>Subscribe Jay's Devlog!</button>
```

CSS code:

```css
button:active {
    border: 2px solid palevioletred;
    border-radius: 5px;
}
```

With active effect:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684079671475/9696ef88-e6b6-47a4-a3cf-ed756c2724fa.png align="left")

Without active effect:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684079762407/4a1b43a1-9d94-4a4a-8626-a5ce8a06dec1.png align="left")

---

## Child-related Pseudo-classes

:nth-child can receive four parameters:

1. 2n
    
2. 2n+1
    
3. even
    
4. odd
    

2n is the same as even, and 2n+1 is the same as odd. The result will be the same.

HTML code:

```css
<table>
      <thead>
        <tr>
          <th>Student ID</th>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Degree</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>1200</td>
          <td>John</td>
          <td>Doe</td>
          <td>Computer Science</td>
        </tr>
        <tr>
          <td>1300</td>
          <td>Mary</td>
          <td>Doe</td>
          <td>Business</td>
        </tr>
        <tr>
          <td>1400</td>
          <td>Jane</td>
          <td>Lee</td>
          <td>Accounting</td>
        </tr>
        <tr>
          <td>1500</td>
          <td>Jason</td>
          <td>Hamilton</td>
          <td>Psychology</td>
        </tr>
      </tbody>
    </table>
```

CSS code:

```css
table,
th,
td {
    border: 1px solid black;
    border-collapse: collapse;
}

tbody > tr:nth-child(2n) {
    background-color: lightsalmon;
}
```

Table:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684080754525/aefe5ba5-5980-4841-9e51-7c001eee80ec.png align="center")

Do you notice that only the even number of the &lt;tr&gt; has a pink background?

\*The (&gt;) symbol is called a combinator selector. It basically selects all the &lt;tr&gt; element that has a &lt;tbody&gt; tag as their parents.

There are other types of combinator selectors, such as (~) and (+). If you want to find out more about them, check out this article:

> [CSS Combinator Selector](https://jaylog.hashnode.dev/css-css-combinator-selector-explained-with-examples)

For the other two classes (first-child and last-child), the HTML code will be the same, so I will just share my CSS codes.

CSS code (first-child):

```css
table,
th,
td {
    border: 1px solid black;
    border-collapse: collapse;
}

tbody > tr:first-child {
    background-color: lightsalmon;
}
```

Table:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684081140873/90c5cae7-d65e-495f-a689-114306ee47c6.png align="center")

CSS code (last-child):

```css
table,
th,
td {
    border: 1px solid black;
    border-collapse: collapse;
}

tbody > tr:last-child {
    background-color: lightsalmon;
}
```

Table:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684081169606/5e1c60f1-f21a-4ffb-9627-9d0b74cdf964.png align="center")

---

## Conclusion

This is all I have for you today. The pseudo-classes are quite interesting, especially :hover in my opinion. If you use them when needed, you will be able to write your code more efficiently.