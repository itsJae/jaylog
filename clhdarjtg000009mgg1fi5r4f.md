---
title: "[JavaScript] Async & Await - When to Use It. Explained with Examples."
seoTitle: "[JavaScript] Async & Await - Explained with Examples"
seoDescription: "Understand async and await in JavaScript. When to use async and await. Easy explanations and Beginner Friendly."
datePublished: Sun May 07 2023 10:54:47 GMT+0000 (Coordinated Universal Time)
cuid: clhdarjtg000009mgg1fi5r4f
slug: javascript-async-await-when-to-use-it-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683455317720/deb5b0c2-25dd-40df-9eab-c41080c9dc82.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683456846231/76af78f4-5584-4370-91e6-08f2e2bd58ca.png
tags: programming-blogs, javascript, web-development, beginners, asyncawait

---

---

### Introduction

This article will be exploring async / await in JavaScript, and the purpose of using them when you communicate with a server.

In asynchronous communication, the sequence of responses from the server is not known.

For example, you sent request A and then request B to the server. But, the response for B can be received earlier than the response for A.

It is one of the characteristics of the asynchronous communication.

By using async / await in JavaScript, you can ensure the response sequence.

> Check out this article: [Synchronous vs Asynchronous](https://jaylog.hashnode.dev/synchronous-vs-asynchronous-the-advantage-disadvantages-and-differences) if you want to find out more about asynchronous communication.

---

### Async / Await

```javascript
async function getData() {
    const response = await fetch("http://localhost:3000/posts");
    const json = await response.json();
    
    console.log("excuted second");
}
```

In the response variable, the response from the server is stored as a string type.

In the json variable, the response is converted from the string type to the json type.

Even though it is asynchronous communication, the server will wait until the response is sent, which makes it executed the first.

---

### Comparison with Fetch API

```javascript
function getData() {
    fetch("http://localhost:3000/posts")
    .then((response) => response.json)
    .then((json) => console.log(json));
    
    console.log("excuted first");
}
```

In this case, the console.log statement is executed first because the response has not been made yet.

We did not specify async / await.

> If you want to find out more about the Fetch API, check out this article: [\[JavaScript\] Fetch API](https://jaylog.hashnode.dev/javascript-fetch-api-get-post-put-delete-to-send-a-request-to-the-server-explained-with-examples).

---

### When Should You Use Async / Await? Is it Always Good to Use?

The advantage of async / await is quite straightforward. It ensures the order of response even though it is using asynchronous communication.

However, the disadvantage is that other responses cannot be made until the specified response is sent back to the client.

If you do not need to care about the ordered sequence, use fetch API.

Else, consider the advantages and disadvantages of async / await and see if they are necessary.