---
title: "[TypeScript] Understanding <Generics>"
seoTitle: "[TypeScript] Generics for Modularization"
seoDescription: "In this article, I will be talking about the generics in TypeScript, which is an important concept you need to know."
datePublished: Wed Jun 07 2023 01:01:39 GMT+0000 (Coordinated Universal Time)
cuid: clil086gd046fptnvdffu81pf
slug: typescript-understanding-generics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1686019104417/d0b0e5b2-6d88-4812-998c-47235c00ca31.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1686019111782/e65af5fb-c0b6-4197-bfec-31fdb2ce0027.jpeg
tags: programming-blogs, web-development, typescript, generics, typescript-generics

---

---

## Introduction

In this article, I will be talking about the generics in TypeScript, which is an important concept you need to know. If you know programming languages like Java, C# and GO, you might have heard of it.

> Generics allow creating 'type variables' which can be used to create classes, functions & type aliases

Generics are not much different from a parameter. You will be able to see the similarity as we go through the example code.

---

## Why Do We Use Generics?

We use generics to avoid repeating blocks of code. Let's say we need to create a function that requires user input with many different types.

```javascript
function log(userInput: string) {
    console.log(userInput);    
}

function log(userInput: number) {
    console.log(userInput);    
}

function log(userInput: boolean) {
    console.log(userInput);    
}
// and so on..
```

OR:

```javascript
function log(userInput: string | number | boolean | Array<string> | Array<number>) {
    console.log(userInput);    
}
// Code gets messier
```

OR:

```javascript
function log(userInput: any) {
    console.log(userInput);
}
// might cause an error
```

If you are using `any`, your code more likely causes an error. We are using TypeScript to make JS code more straightforward and less subject to an error.

**Generics can solve the problem:**

```javascript
function log<T>(userInput: T): T {
    console.log(userInput);
}
// T is similar to a parameter
log<string>("String type");
log<number>(1004);
log<boolean>(true);
```

Now the code is much simpler and straightforward. The `T` (stands for Type) doesn't have to be `T`, but using `T` is conventional, which is what everyone does.

---

## Understanding Generics

Let's look at this example again:

```javascript
function log<T>(userInput: T): T {
    console.log(userInput);
}
// T is similar to a parameter
log<string>("String type");
```

When you do log&lt;string&gt;, TypeScript reads it in this way:

```javascript
function log<string>(userInput: string): string {
    //.. 
}
```

> When you use generics, the type is determined when the function is called.

---

## Generics in Interface & Class

Generics in Interface:

```javascript
interface Student<T> {
    ID: 10245845;
    name: T;
    school: T;
    facalty: T;  
}

let stu: Student<string>;
```

Generics in Class:

```javascript
class Movie<T> {
    title: T;
    runningTime: number;
    constructor(title: T, runningTime: number) {
        this.title = title;
        this.runningTime = runningTime;
    }        
}

let movie = new Movie<string>();
```

Similarly, in class, generics are defined when you create a new instance, just like you gave a type when you call the function.

Note that generic classes are only generic over their instance side rather than their static side, so when working with classes, static members can not use the class’s type parameter.

---

## Length Property

Let's have a look at this code:

```javascript
function logLength<T>(param: T): void {
    console.log(param.length); // Error!    
}
```

This code causes an error. TypeScript does not know which type `param` will be. If `param` is a number, `param.length` is an error. Therefore, only string, object and array are valid options.

There are two ways to solve this problem

**Solution 1:** Using an array

```javascript
function logLength<T>(param: T[]): void {
    console.log(param.length); 
}

logLength<number>([1, 2, 3]) // 3
```

**Solution 2:** Using a pre-defined type

```javascript
interface Length {
    length: number;        
}

function logLength<T extends Length>(param: T): void {
    console.log(param.length); 
}
```

---

## Reference

[https://www.w3schools.com/typescript/typescript\_basic\_generics.php](https://www.w3schools.com/typescript/typescript_basic_generics.php)