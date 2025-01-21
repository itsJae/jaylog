---
title: "[TypeScript] Types in TypeScript & Why TypeScript"
seoTitle: "[TypeScript] Types in TypeScript & Why TypeScript"
seoDescription: "In this article, I will be talking about the types in TypeScript. I will be talking a little bit about what is TypeScript (TS), and why you need it."
datePublished: Thu Jun 01 2023 05:34:45 GMT+0000 (Coordinated Universal Time)
cuid: clicpc9wk000h0ajo5oxhdjhs
slug: typescript-types-in-typescript-why-typescript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685543619077/87a9a6a1-12df-4c2e-8c34-d109cce1da2f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685543658747/9ea4049d-c550-49df-80dd-c99a66d67441.png
tags: programming-blogs, web-development, typescript, ts, typescript-tutorial

---

---

## Introduction

In this article, I will be talking about the types in TypeScript. This is the first post in my TypeScript Series, so I will be talking a little bit about what is TypeScript (TS), and why you need it.

According to TypeScript's website,

> ### TypeScript is **JavaScript with syntax for types.**

If you have learned programming languages like Java, you would know that JavaScript is much easier but less straightforward. In Java, you need to set the data type when you declare a variable. On the other hand, JavaScript does not require you to do that.

```javascript
let str = "Type is not specified!";
```

In TypeScript, your code will be more specific and less subject to errors.

---

## Type List

**Basic Types in TypeScript:**

* String
    
* Number
    
* Boolean
    
* Object
    
* Array
    
* Tuple
    
* Any
    
* Enum
    
* Never
    
* Void
    

---

## Types

When you declare a variable in TypeScript, you will be assigning types as well. It is always a variable name followed by a colon (:), then followed by the type.

```javascript
let example: type = _____;
```

## String

```javascript
let str: string = "Hello TS!";
```

## Number

```javascript
let num: number = 10;
```

## Boolean Expression

```javascript
let isMarried: boolean = true;
```

## Object

There are two(2) ways when you declare an object in TypeScript.

```javascript
// Declaring an object type
let obj1: object = { name: "John Doe", age: 34 };

// Declaring an object type & giving types to each property. 
let obj2: { name: string, age: number} = {name: "John Doe", age: 34};
```

## Array

There are two3) ways when you declare an array in TypeScript

```javascript
// Assigning "string" type to all the elements
let brands: Array<string> = ["Goolge", "Microsoft", "Meta"];

// Another way of assigning the type
let brands: string[] = ["Goolge", "Microsoft", "Meta"];
```

## Tuple

```javascript
// Specifying each element's type
let address: [string, number] = ["New York", 5276];
```

## Any

```javascript
// "any" type is available
let str: any = "Any type is available.";
let num: any = 10;
let isMarried: any = true;
```

## Enum

You might have heard of this type if you have learned Java.

```javascript
enum Brands { "Google", "Microsoft", "Meta" }
let brand: enum = Brands.Google;
let brand: enum = Brands[0];
```

## Never

```javascript
function myFunc(): never {
    while (true) {
    }
}
```

You can give the return type of a function by putting the colon (:) followed by the type.

If you know Java:

```java
public int sum(int a, int b) {
    return a + b;
}
```

`sum()` must return an integer.

## Void

A void type can be assigned when you declare a variable or function, but it has different usages.

**Variable Declaration:**

```javascript
let var1: void = undefined;
let var2: void = null;
```

Void type can only contain either `undefined` or `null`.

**Function Declaration:**

```javascript
function myFunc(): void {
    console.log("No return value.");
}
```

When you use it for the function's return type, void type means that you will not return anything.

In Java, you would do:

```java
public void sayName() {
    console.log("John Doe");
}
```