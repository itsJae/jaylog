---
title: "[CSS] CSS Position Sticky - How It works (with Examples)"
seoTitle: "CSS Position Sticky - How It Works (with Examples)"
seoDescription: "CSS Position Sticky is one of the most interesting properties. Nowadays many websites use it as it enhances the user experience with the website."
datePublished: Sat Apr 29 2023 17:44:39 GMT+0000 (Coordinated Universal Time)
cuid: clh29vtvj001c09mjhx9hc7c6
slug: css-css-position-sticky-how-it-works-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682950288521/4722d985-b5c6-44f8-b3d3-ab3a7b0aaa76.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682790206940/81cbd176-f81a-40d2-8c23-2199b9870663.png
tags: programming-blogs, css, html5, css-position, position-property

---

---

### Introduction

CSS has a very interesting property called position: sticky. This allows certain content to be stuck to the webpage.

Sometimes, you want your main navigation, such as Home, About Us, Contact Us, etc to be shown even after users scroll down.

Position sticky allows you to do that, so let's dive into the syntanx and the actual example!

---

### Syntax:

```css
.example {
    position: sticky;
    top: 0;
}
```

The syntax is quite easy. In the selector, you can write position: sticky; and that's all.

In this case, I set the top as 0, which will make the navigation stuck to the top of the web page.

---

### Example:

```css
.navbar {
    position: sticky;
    top: 0;
}
```

```xml
<nav class="navbar">
      <a href="">Menu1</a>
      <a href="">Menu2</a>
      <a href="">Menu3</a>
      <a href="">Menu4</a>
      <a href="">Menu5</a>
</nav>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682789777188/6c77b08d-6183-4f17-ae1a-faea61464e66.png align="center")

This is before scrolling down.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682789828838/96893b28-1a0c-4c50-a399-71dcef262db6.png align="center")

Even after scrolling down, you can see that the Menus are stuck at the top.

Position Sticky property is interesting, and this will even enhance the user experience.

Give it a try!