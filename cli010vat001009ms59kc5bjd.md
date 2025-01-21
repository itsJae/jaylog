---
title: "[JavaScript] Understanding Function Declaration vs Function Call"
seoTitle: "[JavaScript] Understanding Function Declaration vs Function Call"
seoDescription: "I will talk about common mistakes that people come across when they do not know the difference between function declaration and function call."
datePublished: Tue May 23 2023 08:40:48 GMT+0000 (Coordinated Universal Time)
cuid: cli010vat001009ms59kc5bjd
slug: javascript-understanding-function-declaration-vs-function-call
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684826126945/5fa2587f-45e5-4290-b1c6-a2e83649df30.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684831193118/9549460e-7d36-40d1-aa8c-ef27dab37d65.jpeg
tags: functions, programming-blogs, javascript, web-development, higher-order-functions

---

---

## Introduction

In this article, I will talk about common mistakes that people come across when they do not know the difference between function declaration and function call. More importantly, I will introduce a little tip&trick for you to avoid that mistake.

I will be covering these sub-topics:

1. Function Declaration vs Call
    
2. Common mistakes due to misunderstanding the function declaration and call.
    
3. Higher-order function
    

Before moving on, let me ask a question

```javascript
const add = (a, b) => a + b;
function myFunc(func, num1, num2) {
    return func(num1, num2)
}
myFunc(add, 3, 5); // is this correct?
myFunc(add(), 3, 5); // or is this correct?
```

Which is the right way to call myFunc()? The answer is `myFunc(add, 3, 5)` . If you guessed it or are unsure how to determine it, this article would be helpful for you.

---

## Declaration vs Call

Declaring a function can be done in two ways:

1. Function declaration
    
2. Function expression
    

**Function Declaration:**

```javascript
function myFunc() {
    // your code
}
```

**Function Expression:**

```javascript
const myFunc = a => console.log(a);
```

These are called function declarations. You have created a new function, and you are ready to use it, but you haven't used it yet.

If you want to use the function, you need to **call** the function.

**Function Call:**

```javascript
function myFunc() {
    console.log("Use parentheses to call the function.");
}
myFunc(); // Use parentheses to call the function.
```

You can do `functionName()` to call the function.

---

## Common Mistakes

```javascript
const add = (a, b) => a + b;
function myFunc(func, num1, num2) {
    return func(num1, num2)
}
myFunc(add, 3, 5); // is this correct?
myFunc(add(), 3, 5); // or is this correct?
```

The first parameter of the myFunc() function should not have parentheses as the return value is `func(num1, num2)` . func will be replaced with add (or any other parameters that go in).

You might wonder why add() is a wrong answer because we usually invoke the function like that when we want to use it.

> When you **call** the function, simply just replace the function in the parameter with the return value of that function.

Example:

```javascript
const add = (a, b) => a + b;
// myFunc(add(), 3, 5);
// is equivalent to
myFunc(undefined + undefined, 3, 5);
```

add() would have a return value of undefined + undefined because nothing was given in the parameter.

Therefore, the last line makes no sense. Therefore, it is very clear to see why we should put add instead of add().

You can use this technique to figure out if your code is correct. However, there is an exception, which is the higher-order function.

---

## Higher-Order Function

Example:

```javascript
const f1 = () => () => console.log("example");
```

This is an example of a higher-order function in JavaScript. If you cannot understand this code, the code below would be helpful. Please note that each block is for each function.

HTML code:

```javascript
const onClick => () => (event) => {
    console.log("Welcome to our website!");
}

document.querySelector("#header").addEventListener("click", onClick());
```

This is an example of a higher-order function in JavaScript. Unlike the earlier examples, I called the function onClick. It is because onClick is a higher-order function, which means a function inside a function.

So, let's replace the function call in the parameter with its return value.

```javascript
document.querySelector("#header").addEventListener("click", (event) => {
    console.log("Welcome to our website!");
});
```

It might be confusing to figure out where to put the "event" parameter. To solve that issue, you can just put the event in both parameters.

Example:

```javascript
document.querySelector("#header").addEventListener("click", () => {
    console.log("Welcome to our website!");
});

document.querySelector("#header").addEventListener("click", (event) => {
    console.log("Welcome to our website!");
});
```

The second statement is correct because we will need to receive an event, and if the onclick event happens, we will print out the welcome message to the user.

---

## Conclusion

Use the tip&trick that I gave you in this article when you need it. Just replace the parameter with the return value of that function! Be careful of higher-order functions as well.