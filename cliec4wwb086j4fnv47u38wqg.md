---
title: "[TypeScript] Optional & Default Parameter"
seoTitle: "[TypeScript] Optional Parameter in TS"
seoDescription: "n this article, I will be covering what an optional parameter is, and talk a little bit about the difference between JavaScript and TypeScript."
datePublished: Fri Jun 02 2023 09:00:39 GMT+0000 (Coordinated Universal Time)
cuid: cliec4wwb086j4fnv47u38wqg
slug: typescript-optional-default-parameter
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685623812618/645f33dd-9139-49a9-97d8-9e8750951199.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685623817602/94b5c4b9-6566-4173-a375-749f492a97a8.webp
tags: tutorial, programming-blogs, web-development, typescript, optional-parameter

---

---

## Introduction

In this article, I will be covering what an optional parameter is, and talk a little bit about the difference between JavaScript and TypeScript.

Before moving on, if you do not know the basic types and how to assign types, check out this article:

> [Types in TypeScript](https://jaylog.hashnode.dev/typescript-types-in-typescript-why-typescript)

---

## Optional Parameter

Let's look at the difference between JS and TS first.

In **JavaScript:**

```javascript
function myFunc(name) {
    // your code
}
myFunc("John", "Mary", "Sarah");
```

You can pass as many parameters as you want. The rest (except John) will be ignored.

But in **TypeScript:**

```javascript
function myFunc(n1: string, n2?: string, n3?: string): void {
    // your code
}
myFunc("John", "Mary", "Sarah");
```

You can decide how many parameters you want to put in. In this case, the maximum number of parameters is 3.

Take note that the first parameter does not have the question mark(?) symbol. That means the first parameter must be given, but the other parameters with the (?) symbol are optional.

---

## Default Parameter

The default parameter is assigning a default value to a parameter. The assigned value is used if there is no parameter given.

Using a default parameter in TypeScript is the same as using it in JavaScript.

For example:

```javascript
function printName(name: string = "unnamed"): void {
    console.log(`Name: ${name}.`);
}
printName(); // Name: unnamed.
printName("John Doe") // Name: John Doe.
```

As you can see, if no parameter is given, the default value that is defined previously will be used. In this case, the default value is `unnamed`.

---

## Want More Articles about TypeScript?

Follow me and stay up-to-date with my new TypeScript articles. I will be posting them quite often :)