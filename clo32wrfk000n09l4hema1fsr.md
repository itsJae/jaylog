---
title: "[JavaScript] Deep Dive Into Event Loop - How JavaScript Works"
seoTitle: "[JavaScript] Deep Dive Into Event Loop - How JavaScript Works"
seoDescription: "In this article, I will talk about call stack, call back queue, web APIs and event loop. After reading this article, you should be able to think how JS runs"
datePublished: Mon Oct 23 2023 15:55:08 GMT+0000 (Coordinated Universal Time)
cuid: clo32wrfk000n09l4hema1fsr
slug: javascript-deep-dive-into-event-loop-how-javascript-works
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698075177044/f8dcbccb-38ee-4f4c-b530-f0b457dc0f74.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698076462295/084236ed-4e89-43fb-a942-c96527926606.gif
tags: javascript, asynchronous, queue, event-loop, callstack

---

---

## Introduction

In this article, I will talk about call stack, call back queue, web APIs and event loop. After reading this article, you should be able to think how javascript runs in your head.

This website is really helpful to understand and visualize what I am talking about in this article.

> [JELoop Visualizer](https://kamronbekshodmonov.github.io/JELoop-Visualizer/)

---

## JavaScript is Synchronous

Some people think that JavaScript is asynchronous because we send GET, POST requests to the server, and fetch data from the server. However, JavaScript is not asynchronous.

To understand what is synchronous and what is asynchronous, let's have a look at this example:

Synchronous

* In University, there are four steps to graduate.
    
    1. Freshman
        
    2. Sophomore
        
    3. Junior
        
    4. Senior
        

Asynchronous

* To become a front-end developer,
    
    * You need to study HTML, CSS, JavaScript, SPA framework, etc.
        
    * You need to build a personal website or a program or a service as your portfolio.
        
    * You need to obtain some IT-related certifications.
        
    * You need to build your Github.
        

In synchronous, events happen in sequence. You become a freshman, then sophomore, then junior, then senior, then you finally graduate.

In asynchronous, events can happen anytime and at the same time. You can study JavaScript while preparing for the certification.

![Synchronous vs. Asynchronous JavaScript | by Vivian Yim | Medium](https://miro.medium.com/v2/1*V5syja2casc0gCuu9zKV5g.png align="left")

But then, how does JavaScript handle asynchronous communications, such as `setTimeout()`? The answer is - Web API helps JavaScript to handle it. That's why we can use JS as if JS is asynchronous. JS gets external help from Web API.

---

## JavaScript Engine

To run a JavaScript code snippet, a JavaScript engine is required. The JS engine consists of two parts.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698074767099/e4fdaf86-149b-4b7d-834f-facf1f42e09c.png align="center")

1. Heap Memory
    
    * Simply, heap memory is a data storage.
        
    * This is where data is stored. For example, let's declare a variable. `var a = 10;` will be stored in the heap memory.
        
    * When `var a = 15;` is assigned with a new value, the old value (10) is useless. So, the garbage collector will collect this data from the heap memory.
        
2. Call Stack
    
    * Call stack has a characteristic of Last-In-First-Out (**LIFO**).
        
        * The last function that gets pushed into the stack is the first to be pop out, when the function returns.
            
        * Think of this as a pringles.
            
            ![Promo Pringles Cans](https://www.rushimprint.com/ajax_handler.php?page=get_product_image&dimensions=600&pID=50385 align="left")
            
        * The first chip that you will get is the one at the top.
            
        * The last chip that you will get is the one at the bottom.
            
    * When the function is called, that function goes into the call stack, and gets out of the call stack once it is returned or finished.
        

### Call Stack Example

```javascript
function A() {
    console.log("A-1...");
    B();
    console.log("A-2...");
}

function B() {
    setTimeout(function () {
        console.log("B-1...");
    }, 1500);
}

A();
// A-1...
// A-2...
// B-1...
```

Now, let me help you to visualize what is happening.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698075322650/0cc2b19e-5770-4ea8-b8a2-46820e247e33.png align="center")

`setTimeout()` suddenly disappears in number 5, and then comes back in number 11. It is because `setTimeout()` is moved to **Web API** so that Web API can handle asynchronous things, and then, `setTimeout()` will be moved to the callback queue. **Callback queue** is where the callback functions of Web API wait to be moved to the **call stack** by the **event loop**.

The **event loop** will check if the stack is empty. If it is empty, and there are callback functions waiting in the queue, the event loop will move those functions to the stack, just like the above example. The `setTimeout()` was moved to Web API, then to the callback queue, and then to the stack once the stack was empty.

Queue has a characteristic of First-In-First-Out **(FIFO)**. First come first serve.

To summarize what I just said:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698075737468/09f99948-c893-4128-8a82-50c4ddb0df0b.png align="center")

Have a look at this website to help yourself visualize how JS works:

> [JELoop Visualizer](https://kamronbekshodmonov.github.io/JELoop-Visualizer/)

---

## Additional Thing

What if you do this in `setTimeout()`?

```javascript
console.log("1");

function myFunc() {
    setTimeout(() => {
        console.log("2");
    }, 0);
}

console.log("3");
```

I have set the second argument of `setTimeout()` as "0", which is 0 second. Then, `console.log("2");` should execute immediately right? What do you think? Is it gonna print 1, 2, 3 in sequence or not?

The answer is - no.

* It will print out 1, 3, 2 because `setTimeout()` is asynchronous.
    
* Still needs to do this: Web API -&gt; callback queue -&gt; event loop -&gt; call stack -&gt; console.log("2");
    
* While `setTimeout()` is being processed by Web API, console.log("3") is already be printed out.