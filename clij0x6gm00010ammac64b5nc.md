---
title: "[TypeScript] Union & Intersection Type"
seoTitle: "[TypeScript] Union & Intersection Type"
seoDescription: "We will be talking about the union and intersection type in TypeScript. I will be talking about the downside of using a union type and introduce generics"
datePublished: Mon Jun 05 2023 15:45:33 GMT+0000 (Coordinated Universal Time)
cuid: clij0x6gm00010ammac64b5nc
slug: typescript-union-intersection-type
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685777488175/5f8c9d1d-25d7-4fd6-92ef-93de96c3d1ac.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685777494104/19d65f36-e8c2-42a1-9510-4ab6a96a4629.png
tags: web-development, typescript, typescript-generics, union-type, intersection-types

---

---

## Introduction

In this article, we will be talking about the union and intersection type in TypeScript. Furthermore, I will be talking about the downside of using a union type and introduce generic a little bit.

If you want to know more about generics in TypeScript, an article with detailed explanations will be posted tomorrow, so stay tuned!

---

## Union Type ( | )

Union type uses OR ( | ) symbol. The OR symbol has the same meaning as JavaScript's logical OR ( || ) operator.

> **Union types** are used when a value can be more than a single type.

For example, a building's address can have a postal code, which is a number and a street name, which is a string.

```javascript
function printAddress(address: number | string) {
    //..  
}

printAddress(10245) // postal code
printAddress("Robson street") // street name
printAddress("Vancouver") // city name
```

You can use the union type ( | ) to separate the type. Now you can pass a number or string as the parameter of `printAddress()` function.

Now let's make it more straightforward:

```javascript
function printAddress(address: number | string) {
    if (typeof address === 'number') {
        address.toString();
        address.toFixed();
    } 

    if (typeof address === 'string') {
        address.replace();
        address.toLowerCase();
    }
    
    throw new TypeError("address must be a number or string.");     
}
```

By putting an if statement, when you put a dot(.) next to the address, the VSCode or your IDE will give you a list of methods you can use.

If it is a number, it gives a list of number methods, such as toString() and toFixed().

If it is a string, it gives a list of string methods, such as replace() and toLowerCase().

---

## The Downside of Union Type

1. TypeScript cannot predict which type you will be giving, so some elements are not accessible.
    
    ```javascript
    interface Developer {
        name: "Mary Doe"; 
        skill: "JavaScript";
    }
    
    interface Person {
        name: "John Doe";
        age: 34;
    }
    
    function myFunc(p: Developer | Person) {
        p.name // no error
        p.skill // error
        p.age // error
    }
    ```
    
    `p.name` is accessible, but others are not. Both interfaces, Developer and Person, have a `name` element in common, but not `skill` or `age`. An error will occur because TypeScript does not know which type you will be passing through as a parameter.
    
2. Using a union type might result in a repeating code.
    
    Let's say you want to make functions that print out a parameter. You might do:
    
    ```javascript
    function logText(text: string) {
        console.log(text);
    }
    
    function logNumber(num: number) {
        console.log(num);
    }
    ```
    
    OR:
    
    ```javascript
    function log(a: string | number) {
        console.log(a)
    }
    ```
    
    But in practice, you want to use "generic" when your code has a repeating component:
    
    ```javascript
     function log<T>(a: T): T {
        console.log(a);
    }
    // define the type when you call the function.
    log<string>("Generics make it easier to write reusable code.");
    log<number>(10);
    log<object>({ skill: "TypeScript" });
    ```
    
    This code might look more complex, but imagine using the generics when you are working with 10000 lines of code. Your code will be more modularized, and that's the job of generics.
    

The T in `log<T>` works the same as a parameter in a function. You can give it a string type by writing `log<string>` when you call the function

---

## Intersection Type (&)

For the intersection type, the parameter must have both types that are defined next to the (&) symbol.

For example:

```javascript
interface Developer {
    name: "Mary Doe"; 
    skill: "JavaScript";
}

interface Person {
    name: "John Doe";
    age: 34;
}

function myFunc(p: Developer & Person) {
    p.name; // no error
    p.skill; // no error
    p.age; // no error
}
```

Unlike the union type, you won't be having problems accessing the elements. By having the (&) symbol, TypeScript knows that the parameter will contain a value that has all the elements, such as:

```javascript
let person = {
    name: "John Doe",
    skill: "ReactJs",
    age: 29,
}
// this person is an intersection of Developer and Person.
```

---

## Next Article

The next article will be about generics in TypeScript. It will be posted tomorrow, so I will see you there!