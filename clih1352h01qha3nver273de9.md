---
title: "[TypeScript] Mastering Interface & Type Aliases"
seoTitle: "[TypeScript] Mastering Interface & Type Aliases"
seoDescription: "In this article, I will be talking about the differences between type and interface in TypeScirpt."
datePublished: Sun Jun 04 2023 06:14:39 GMT+0000 (Coordinated Universal Time)
cuid: clih1352h01qha3nver273de9
slug: typescript-interface
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685718391520/fc123112-de3d-49c0-9591-93c5e1e13f29.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685718400042/dc42eb33-f26a-4aeb-b6d0-5c668b28ea5c.png
tags: web-development, typescript, inheritance, interface, type-aliases

---

---

## Introduction

In this article, I will be talking about the differences between type and interface in TypeScirpt.

It is important to make use of either type or interface (mostly interface) when you write code in TypeScript. Using them will make your code look more organized, which is beneficial when working with a team. Moreover, they are used for modularization, which means reducing repeated code.

---

## Type Aliases

TypeScript allows you to define the types separately from the variables that use them.

Let's see how we can modularize our code by using type aliases.

Bad example (without type aliases):

```javascript
function addItem( item: { name: string; price: number; isFresh: boolean } ) {
    //..
}

function deleteItem( item: { name: string; price: number; isFresh: boolean } ) {
    //..
}

function completeItem( item: { name: string; price: number; isFresh: boolean } ) {
    //..
}
```

For each function, the parameters receive an object with the same structure. We can clearly see that a certain part is repeating. By using `type` keyword, you can avoid this.

Good example (with type aliases):

```javascript
type Item = {
    name: string; 
    price: number; 
    isFresh: boolean
}
function addItem(item: Item) {
    //..
}

function deleteItem(item: Item) {
    //..
}

function completeItem(item: Item) {
    //..
}
```

Now, the code is more precise and readable because we have used type aliases.

> Type Aliases allow defining types with a custom name (an Alias).

You can implement type aliases on the variables.

For example:

```javascript
type PersonName = string;
let john: PersonName = "John";
```

---

## Interface

Interfaces are not very different from the type aliases and do the same job just like the type aliases. Actually, the interface is used a lot more than the type aliases. I will be talking about why we use the interface instead of type aliases later on.

> A characteristic of an interface is that it only allows an object type.

For example:

```javascript
interface Person {
    name: string;
    age: number;
}

// using with a variable
let john: Person = {
    name: "John Doe",
    age: 34,
}

// using with a function
function myFunc(person: Person) {
    console.log(person.name);
    console.log(perosn.age);
} 
```

---

### Inheritance

You can also inherit the interface. If you have learned object-oriented programming before, it would be more familiar.

> You want to use an interface instead of type aliases because the interface allows inheritance.

For example:

```javascript
// Inheritance
interface Developer extends Person {
    // name: string;
    // age: number;
    job: "Developer";
    skill: "TypeScript";
}
```

---

### Readonly

Read-only in TypeScript means that the value cannot be modified once it is defined.

For example:

```javascript
interface Person {
    readonly name: string;
}

let john: Person = {
    name: "John Doe"; // defined. Now it cannot be modified.
}
john.name = "Rylee Lee"; // error
```

Read-only Array:

```javascript
let brands: ReadonlyArray<string> = ["Google", "Microsoft", "Meta"];
brands.push("Netflix"); // error
brands.splice(2, 1); // error  
```

---

### Indexing

You can specify the type when you use an index number to get an item from an array.

For example:

```javascript
interface StringArray {
    [index: number]: string; 
}

let brands: StringArray = ["Google", "Microsoft", "Meta"];
arr[0]; // Google, which is string.
arr[0] = 10 // error
```

The last line of code is an error because we have previously defined the interface called `StringArray`. So, we cannot assign a number in the `brands` array.

---

### Function

You can use an interface when you declare a function.

```javascript
interface Student {
    (id: number, school: string): boolean
}

let attendance: Student;
attendance = function(studentID: number, schoolName: string) {
    return true;
}
```

---

### Dictionary Pattern

```javascript
interface StringRegexDictionary {
    [key: string]: RegExp;
}

let regexps: StringRegexDictionary {
    something: /abc/; 
}
```

`something` is relevant to `[key: string]`

`/abc/` is relevant to `RegExp`.

---

## Reference

[https://www.typescriptlang.org/docs/handbook/interfaces.html](https://www.typescriptlang.org/docs/handbook/interfaces.html)

[https://www.w3schools.com/typescript/typescript\_aliases\_and\_interfaces.php](https://www.w3schools.com/typescript/typescript_aliases_and_interfaces.php)