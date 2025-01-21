---
title: "[JavaScript] Pure Function for Clean Code"
seoTitle: "[JavaScript] Pure Function for Clean Code"
seoDescription: "in this article, I will be talking about pure vs impure function, and why it is a good practice to always try to use pure function if we can."
datePublished: Wed Oct 25 2023 15:04:19 GMT+0000 (Coordinated Universal Time)
cuid: clo5vz4fe000109l92dvrc86q
slug: javascript-pure-function-for-clean-code
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698236087289/8447281f-9b19-4c8f-a740-5997d5f24113.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698246244071/bb88da80-3107-497c-a2ea-0c80889afbb4.jpeg
tags: functions, programming-blogs, javascript, functional-programming, pure-functions

---

---

## Introduction

in this article, I will be talking about pure vs impure function, and why it is a good practice to always try to use pure function if we can. A pure function does not only exist in JavaScript. You can adopt this in almost every programming language if they provide a function.

---

## What Is Pure Function?

A pure function has **TWO(2)** rules.

1. Always returns the same result if the same arguments are passed.
    
2. Does not cause any side effects
    

A function that does not fit in any of these rules is called an impure function.

For example:

```javascript
// pure function
const add = (x, y) => {
    return x += y
}
add(3, 5); // 8 - always

// impure function
const x = 3;
const y = 5;
const add2 = () => {
    return x += y; // 8, 11, 14, 17, and so on
}
add2(); // result changes
```

Let's have a look at the impure function. Why is it impure -&gt; the second rule (no side effect) was not satisfied. The value of `x` will increase by 3 as you call the function.

Now, think about which one would be easier to debug, read, understand, and predict the result. It's obviosuly the first one, and that's why we want to use pure function if we can. Pure functions are **straightforward**. Furthermore, pure functions can minimize the impact that a certain function can give on other functions.