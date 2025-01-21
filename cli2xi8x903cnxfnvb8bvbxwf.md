---
title: "[JavaScript] Tutorial for Moving Focus When Key Is Pressed"
seoTitle: "[JavaScript] Tutorial for Moving Focus When Key Is Pressed"
seoDescription: "In this article, I will be demonstrating how you can write code that makes the user's mouse focus move to the next button or input box when an enter key is"
datePublished: Thu May 25 2023 09:25:39 GMT+0000 (Coordinated Universal Time)
cuid: cli2xi8x903cnxfnvb8bvbxwf
slug: javascript-tutorial-for-moving-focus-when-key-is-pressed
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684947601540/62786e41-f147-457f-b03e-23dd3bdf62d9.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684947633975/4bbe2fc1-b75f-4ad1-a135-1b4974b13a36.png
tags: tutorial, javascript, web-development, crud, focus

---

---

## Introduction

In this article, I will be demonstrating how you can write code that makes the user's mouse focus move to the next button or input box when an enter key is pressed.

You can use this technique and use it for other situations. For example, moving the mouse focus automatically when the user inputs the first four digits of their card number.

This tutorial would be helpful for those who want to create a better website as this technique will enhance the user experience :)

---

## Tutorial

Let's say that we have this kind of page:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684948018847/67dcba37-93ce-489d-aa9d-4a05968e57d8.png align="left")

When users press an enter key, we want to make the cursor focus to go to the next input box. For example, when the user finishes entering their name, the cursor moves to the input box for a company.

**HTML code:**

```xml
<div>
    <label for="name">Name</label>
    <input type="text" id="name" onkeyup="checkEnter('company');">
</div>
<div>
    <label for="company">Company</label>
    <input type="text" id="company" onkeyup="checkEnter('email');">
</div>
<div>
    <label for="email">Email</label>
    <input type="email" id="email" onkeyup="checkEnter('phone');">
</div>
<!-- etc.. -->
```

**JS code:**

```javascript
function checkEnter(moveID) {
    if (event.keyCode === 13) {
        document.querySelector("#" + moveID).focus();
    }
}
```

If you test out this code, you will get this kind of page:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684948560941/9601c044-9f5f-409a-8ab5-94b662e2219f.png align="left")

Try to press an enter key and see if your cursor moves to the next box. It should work.

In `event.keyCode === 13`, 13 refers to the key code of the enter key. So, it will be true when the user press an enter key on the input box.

You can use apply this cool function on your website and add some styles to make it prettier.