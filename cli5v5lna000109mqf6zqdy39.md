---
title: "[JavaScript] Object & Array Destructuring"
seoTitle: "[JavaScript] Object/Array Destructuring"
datePublished: Sat May 27 2023 10:43:08 GMT+0000 (Coordinated Universal Time)
cuid: cli5v5lna000109mqf6zqdy39
slug: javascript-object-array-destructuring
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685178771666/662fdc18-29cb-421e-87ae-eb6812ee3d1f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685178778875/7e4c3795-6f9b-4787-bc45-6c6f1945e7a1.png
tags: javascript, web-development, destructuring, object-destructing, array-destructuring

---

---

## Introduction

In this article, we will be learning about object and array destructuring, which makes your code more readable and organized. Object & Array destructuring help you to avoid writing a long code to do a simple job.

For example:

```javascript
// Printing first two elements in an array
let arr = [10, 20, 30, 40, 50];
for (let i = 0; i < 2; i++) {
    console.log(arr[i]);
}
// =======================================
// Array Destructuring
let a, b;
[a, b] = arr;
console.log(a); // 10
console.log(b); // 20
```

It's called destructuring because you are distributing the data in an array/object and assign the elements to other variables.

With an array destructuring, you can declare a variable and store the data. This is also a benefit of destructuring because it allows you to store a specific value in a variable and you can use it later. If you are working with a team, more readable and organized code would be great.

---

## Array Destructuring

```javascript
let arr = [10, 20, 30, 40, 50];
let a, b, rest;
[a, b, ...rest] = arr
console.log(a); // 10
console.log(b); // 20
console.log(rest); // [30, 40, 50]
```

Variable `a` and `b` stores the first two elements of the array, and the rest is assigned to the `rest` variable.

You might get a **syntax error** if there is a comma at the end:

```javascript
let arr = [10, 20, 30, 40, 50];
let a, b, rest;
[a, b, ...rest,] = arr // SyntaxError: rest element may not have a trailing comma
```

---

## Object Destructuring

Object destructuring is the same as an array. Let's just have a look at the example.

**Object destructuring:**

```javascript
let person = {
    name: "John Doe",
    email: "john@gmail.com",
    gender: "male"
};
let {name, email, gender} = person;
console.log(name); // John Doe
console.log(email); // john@gmail.com
console.log(gender); // male
```

---

## Reference

Reference: [https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring\_assignment](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)