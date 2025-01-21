---
title: "[JavaScript] Understanding Default Parameter - Explained with Examples."
seoTitle: "[JavaScript] Understanding Default Parameter - Explained with Examples"
seoDescription: "default parameter, JavaScript, function, input validation"
datePublished: Wed May 10 2023 08:10:16 GMT+0000 (Coordinated Universal Time)
cuid: clhhf7ivs000109ji4t8uhy4b
slug: javascript-understanding-default-parameter-explained-with-examples
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683706195086/0f1479bf-c3ee-448b-bdea-620e045dfe33.png
tags: programming-blogs, javascript, web-development, beginners, default-parameter

---

---

### Introduction

This article introduces a default parameter.

The default parameter basically prevents a situation where users enter nothing in the parameter when they are supposed to.

---

### Default Parameter

Syntax:

```javascript
function myFunction(parameter1 = value) {
    console.log(value);
}

myFUnction(); // value
```

Example:

```javascript
let defaultUserName = "strongjohn";
function myFunction(userName = defaultUserName) {
    console.log("Hello,", userName);
}

myFunction(); // Hello, strongjohn
myFunction("strawberry lover"); // Hello, strawberry lover
```

Do you notice that defaultUserName variable is printed even though the function received no parameter?

You can make your program better if you can use the default parameter correctly.