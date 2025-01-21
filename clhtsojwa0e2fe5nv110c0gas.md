---
title: "[JavaScript] Understanding Hoisting - Common Interview Question"
seoTitle: "[JavaScript] What is Hoisting?"
seoDescription: "The term Hoisting in JavaScript is moving the declarations to the top of the scope. Hoisting can happen to any kind of declaration in JavaScript."
datePublished: Fri May 19 2023 00:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clhtsojwa0e2fe5nv110c0gas
slug: javascript-understanding-hoisting-common-interview-question
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684401037619/50ef8663-1b4e-4925-a76d-7d6ac0901f54.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684401059216/8771ebfa-a5ba-4a2c-b858-41210eda8f49.png
tags: programming-blogs, javascript, web-development, hoisting, temporal-dead-zone

---

---

## Introduction

Let's have a look at this code:

```javascript
console.log(a); // Reference Error and TDZ
let a = 10;
```

Reference error occurs because variable `a` is referenced before the declaration. Then, you might ask to put the declaration above the console.log() like this:

```javascript
let a = 10;
console.log(a); // 10
```

Yes, that's right. That is the best way to code, so do not struggle with hoisting while coding, just try to put the declarations at the top.

However, it is still important to know what hoisting is because there could be a circumstance where hoisting cannot be avoided. Moreover, hoisting is a quite common interview question.

If you do not know what Temporal Dead Zone is, please read this article before moving on:

> [\[JavaScript\] Deep Dive into Temporal Dead Zone (TDZ)](https://jaylog.hashnode.dev/javascript-deep-dive-into-temporal-dead-zone-tdz)

---

## Hoisting

The term "Hoisting" in JavaScript is:

> moving only the **declarations** to the top of the scope.

Take note that you are not physically moving the declarations to the top of the code. When your code executes, the declarations are evaluated/registered first by the JavaScript Engine, then the JavaScript engine will start reading your code.

For example:

```javascript
console.log(a); // undefined
var a = 10;
console.log(a); // 10
```

The error does not occur because the declaration and initialization happens at the same time for the `var` keyword.

The perspective of JS engine:

```javascript
var a; // declaration & initialization
console.log(a); // undefined
a = 10; // assignment
console.log(a); // 10
```

Do you notice that the variable declaration is at the top (not in the actual code, I am demonstrating how the JS engine would interpret the code)? This is hoisting.

---

Hoisting can happen to any kind of declaration in JavaScript, such as var, let, const, function and class. Many developers are misunderstanding that hoisting does not happen to `const` and `let` keywords. But, it is not true. As I said before, hoisting happens to any kind of declaration.

It might seem like hoisting does not happen to them because developers of JavaScript have put one more restriction on them.

> You cannot access the variables that are declared with the let or const keyword before a value is assigned to that variable.

For example:

```javascript
let foo = 1;
{
  console.log(foo); // ReferenceError
  let foo = 2;
}
```

ReferenceError occurs because the JS engine cannot refer to the variable `foo`.

**Why?** Because there is no value assigned to foo that is in the `{}` scope.

---

## Hoisting in Functions

Declaring functions can be done in two ways:

1. Function declaration
    
2. Function expression
    

As you would know, functions that are declared in the form of function declaration can be called anywhere.

For example:

```javascript
a();
function a() {
    console.log("No Error");
}
```

However, functions that are declared in the form of function declaration can only be called below the declaration.

For example:

```javascript
a(2); // ReferenceError & TDZ
const a = num => num * num; 
```

The variable a is declared as const, so the field above the declaration is said to be the temporal dead zone.

To avoid this, you can do this:

```javascript
const a = num => num * num; 
a(2); // 4
```

---

## Conclusion

Hoisting happens to any form of declaration in JavaScript. But, for const and let, it seems like that hoisting does not happen to them because JavaScript does not allow you to access the variable with let/const before a value is assigned.

So, keep in mind that hoisting happens to the let/const variable, and you cannot use the variable with let/const before the assignment phase.