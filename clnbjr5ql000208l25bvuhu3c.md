---
title: "[HTML&CSS] Tutorial for Making <Scroll to Top> Button on Your Web Site"
seoTitle: "[HTML&CSS] Tutorial for Making <Scroll to Top> Button on Your Web Site"
seoDescription: "In this article, I will talk about how to make a top button on your website, and how to make it to be scrolled smoothly.

This tutorial doesn't introduce Ja"
datePublished: Wed Oct 04 2023 09:29:07 GMT+0000 (Coordinated Universal Time)
cuid: clnbjr5ql000208l25bvuhu3c
slug: htmlcss-tutorial-for-making-scroll-to-top-button-on-your-web-site
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696409865905/2dd08342-f520-4536-852d-43962634e3df.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696411650668/d013e2cb-ffb3-49bc-9ae0-cd4e9bd655d8.jpeg
tags: programming-blogs, css, web-development, html5, frontend-development

---

---

## Introduction

In this article, I will talk about how to make a top button on your website, and how to make it to be scrolled smoothly.

This tutorial doesn't introduce JavaScript code. Only HTML & CSS. You may go to the bottom of this page where I put the tutorial with JavaScript code.

---

## Making Top Button

Since it is a button, we need an &lt;a&gt; element outside, then we can put an &lt;img&gt; element inside the &lt;a&gt; element.

```xml
<div>
    <a>
        <img></img>
    </a>
</div>
```

Then, we can start writing some code

```xml
<!-- TOP BUTTON -->
<div>
    <a href="#site-header" id="top-button">
        <img src="src/assets/images/top-button.png" alt="Top Button" />
    </a>
</div>
```

```css
html {
	scroll-behavior: smooth;
}

#top-button {
	position: fixed;  /* IMPORTANT */
	right: 30px;
	bottom: 30px;
	width: 40px;
}

#top-button:hover {
    /* your code */
}
```

`href="#site-header"` is used to specify where to go when the button is clicked. In this example, the top button will direct users to the site header.

It is very important to put `position: fixed;` because the top button must not move although users scroll up or down the page.

Then, place the button where you want. Simply do it by giving CSS properties like top, bottom, right, and left.

To make the scroll more smooth. You can give `scroll-behavior: smooth;` to the `html` element.

Then, you may also add some more features, such as style changes when there is a hover event occurring.

---

## Additional Comment

This is not the only way to make the top button. You can refer to this tutorial, too.

[https://www.w3schools.com/howto/howto\_js\_scroll\_to\_top.asp](https://www.w3schools.com/howto/howto_js_scroll_to_top.asp)