---
title: "[JavaScript] Mastering Scope - for Beginners"
seoTitle: "[JavaScript] Mastering Scope - for Beginners"
seoDescription: "In this article, we will cover Understanding Scope, Lexical Scope and Scope Chain"
datePublished: Mon May 22 2023 06:35:59 GMT+0000 (Coordinated Universal Time)
cuid: clhyh4i9o000109mq8q3q5vw8
slug: javascript-mastering-scope-for-beginners
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684660652423/10655c70-40c0-45e9-b51b-639a09ccbb7a.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684665296273/d578e5fe-b735-426d-8fae-74634e6302d5.jpeg
tags: javascript, web-development, scope, lexical-scope, scope-chain

---

---

## Introduction

When I just started learning how to write code, the scope was very confusing and difficult to understand. However, It is essential to understand the scope and know how to determine whether you can access a certain variable or function. Without knowing the scope, you would face many errors, such as `______ is not defined`.

In this article, we will cover:

1. Understanding Scope
    
2. Scope block
    
3. Lexical Scope
    
4. Scope Chain
    

---

## Understanding Scope

**What is Scope?**

> The scope is the area that a function or variable is accessible by other functions or variables.

Global Scope - The scope that is accessible by all.

Local Scope - The range is restricted. Usually variables or functions that are declared inside the function have a local scope.

> IMPORTANT: The scope is determined when the function is declared, not when the function is called.

To understand the scope, let's have a look at the example below.

Scope example:

```javascript
function myFunc() {
    const a = "not accessible outside myFunc()";
}
console.log(a); // ReferenceError: a is not defined
```

You cannot access the variable `a` because its scope is within the `myFunc()`. This means that you can only access it inside the `myFunc()`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684662518506/cb4e7ea5-27fa-4897-953e-ea64f800197d.png align="left")

This is what's happening. Treat the rectangle as field fences on the farm. When you declare a new function, there will be new fences on each side. Therefore, variable `a` must be inside the fence of myFunc().

\*Side Note: anonymous function is not visible, but it is the most outer function in JavaScript.

```javascript
const a = "outside the function";
function myFunc() {
    const a = "inside the function";
    console.log(a);
}
myFunc(); // inside the function
```

You can declare the same variable name if the scope of those variables is different. In the example, variable `a` in the first line has a different scope from the variable inside the `myFunc()`. The JavaScript Engine will refer to the closest variable or function in the accessible scope.

---

## Scope Block

If you declare a variable or function in the block, that variable or function has a local scope. So, the variables declared in the block are not accessible outside the block.

Example:

```javascript
let a = 1; // global
{
    let a = 1; // local
}

for (let i = 0; i < 5; i++) {
    console.log(i); // local
}

if (condition) {
    let a = 1; // local
}
```

For the for-loop, the variable i should be treated as declared in the for-loop block.

Like this:

```javascript
for (i < 5) {
    let i = 0;
    i++;   
}
```

This code snippet is just to illustrate and help you to understand what I mean.

---

## Lexical Scope

Lexical Scope is also known as static scope. In programming, the term static generally means "constant" or "no change".

> Lexical Scope means the scope is determined based on where the function is declared.

In the earlier section, I emphasized that the scope is determined when the function is declared, not when the function is called. Moreover, when the function is declared, the scope does not change, which is relevant to the term "static". So, this is what lexical scope is all about. Let's have a look at an example to understand this better.

Example:

```javascript
 var name = "John Doe";

// function declaration. The scope is determined
function myFunc() {
    var name = "Jane Doe";
    printName();
}

// function declaration. The scope is determined
function printName() {
    console.log(name);
}

myFunc() // What is the output??
```

Can you guess the output when I call the myFunc()?

The output is John Doe, not Jane Doe which is declared inside the myFunc(). Why?

When myFunc() and printName() are declared, they are declared in the global field, which means their scope is global, not local. This means that they will refer to the name variable in the first line.

---

## Scope Chain

Scope chain is a set of functions in different scopes linked together, so it looks like a chain.

Example:

```javascript
function f1() {
    function f2() {
        function f3() {
        }
    }
}
```

scope chain looks like this:

f3 -&gt; f2 -&gt; f1 -&gt; anonymous. I mentioned the anonymous function earlier. It is the most outer function and is not visible.