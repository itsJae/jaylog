---
title: "[JavaScript] Intermediately Invoked Function Expression (IIFE)"
seoTitle: "[JavaScript] Intermediately Invoked Function Expression (IIFE)"
seoDescription: "In this article, I will be talking about Intermediately Invoked Function Expression (IIFE), and why we need an IIFE."
datePublished: Tue Oct 24 2023 12:46:11 GMT+0000 (Coordinated Universal Time)
cuid: clo4blmpu000208k20wvn9v6n
slug: javascript-intermediately-invoked-function-expression-iife
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698145568729/8f46d8aa-c0e5-4b83-a63d-2c1b0084a8b2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698151543175/94ac011a-9198-4698-b803-ad452f242731.png
tags: functions, programming-blogs, javascript, web-development, iife

---

---

## Introduction

In this article, I will be talking about Intermediately Invoked Function Expression (IIFE), and why we need an IIFE.

---

## IIFE Syntax

Normally, we use a function like this in JavaScript:

```javascript
// function declaration
function add(a, b) {
    return a + b;
}
add(2, 10); // 12 

// function expression
let add = function (a, b) {
    return a + b;
}
add(2, 10); // 12
```

We typically use either function declaration or expression. We first declare a function, then call a function.

In IIFE, those two processes are combined into **one process.** As the name of IIFE tells you, it is immediately invoked when it is declared.

Syntax of IIFE:

```javascript
// anonymous IIFE
(function () {
    console.log("IIFE");
})();

// named IIFE
const greeting = "Hi";
(function sayHi(){
    console.log(greeting);    
})();
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698147351644/83b1e6b3-dbae-4359-9b9c-c81ebb87f3b8.png align="center")

The syntax is quite simple. You can start by writing two parentheses `()().` Then, put the function in the first parentheses. Now it's an IIFE!

---

## Naming in IIFE

Naming an IIFE is not necessary because the function will be invoked right away, so it's not gonna be re-used later, which is unlike general functions. However, some people argue that naming is still important because it is a way to help other team members understand what the function does.

In my opinion, if we can name it, we should name it for better readability and clarity in our code.

---

## When to use IIFE

There are three reasons:

1. **To prevent pollution of the global JS scope.**
    
    * General functions are defined/declared in a global scope, and they will remain unless you delete them. IIFEs are executed right after the function declaration, so they will not be in the global scope forever.
        
2. To make a private variable that is not accessible from the outer scope.
    
    * Similar concept to **closure** in JavaScript. We are intentionally closing the scope so that variables are not accessible. Variables declared inside IIFE can only be accessed inside the block scope of IIFE.
        
3. When you need a function that **executes only one time.**
    
    * This is an obvious reason.
        

---

## IIFE Assigned to Variable

What will happen if IIFE is assigned to a certain variable?

Let's have a look at an example:

```javascript
let name = "John Smith";
const storeIIFE = (function sayName() {
    return name
})();

console.log(storeIIFE);
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698151141606/249678e8-8853-4db5-afcc-116658b686dd.png align="center")

Unlike the previous example, I have stored the IIFE in a variable, and did `console.log(variable);` The name John Smith is printed out because I did `console.log()`.

What if I didn't `console.log()`? The name won't be printed out even though it is an **immediately invoked function**. So, the returned value is stored in the `storeIIFE` variable.

---

## Reference

[https://circleci.com/blog/ci-cd-for-js-iifes/](https://circleci.com/blog/ci-cd-for-js-iifes/)