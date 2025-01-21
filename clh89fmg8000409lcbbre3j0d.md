---
title: "[JavaScript] Set Object That You Want To Use for an Object With Unique Values - Explained with Examples."
seoTitle: "Set Object That You Want To Use for an Object With Unique Values."
seoDescription: "Beginner Friendly. Explore what Set Object in JavaScript is, and how they are used. Check out how they differentiate from the object."
datePublished: Wed May 03 2023 22:18:40 GMT+0000 (Coordinated Universal Time)
cuid: clh89fmg8000409lcbbre3j0d
slug: javascript-set-object-that-you-want-to-use-for-an-object-with-unique-values-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683152361359/e2aa4f0a-5a4c-4352-b195-cefc4ffd6ea3.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683152260607/d417ae2d-ba7e-4d7b-8314-0a63fea6101c.jpeg
tags: programming-blogs, javascript, web-development, frontend-development, javascript-object-methods

---

Beginner Friendly. Explore what Set Object in JavaScript is, and how they are used. Check out how they differentiate from the object.

---

### Introduction

What would you do if you want to have an array with unique values (no duplicated values)?

One way to do that is to use the characteristic of an object because the object's key cannot be duplicated.

However, JavaScript has an object called Set which allows for doing that task more efficiently.

---

### Set Object

Without Set Object, you might need to create an object and then create a new array with unique values.

```javascript
let foodArray = ["Burger", "Taco", "Burger", "Sandwich", "Pasta", "Pasta"];
let oFood = {};
for (const food of foodArray) {
    oFood[food] = ""; // creating unique key-value pairs.
}

let uniqueFood = [];
for (const food in oFood) {
    uniqueFood.push(food); // this wil create an array with no duplicated elements (or values)
}
```

But that involves 2-steps. We can use Set Object to make it easier.

add() and delete() method:

```javascript
let foodSet = new Set();
foodSet.add("Burger");
foodSet.add("Taco");
foodSet.add("Sandwich");
foodSet.add("Pasta");

foodSet.forEach(function(food) {
    console.log(food);
});

// Burger
// Taco
// Sandwich
// Pasta

foodSet.delete("Pasta");
foodSet.forEach(function(food) {
    console.log(food);
});

// Burger
// Taco
// Sandwich
```

has() method:

```javascript
let foodSet = new Set();
foodSet.add("Burger");
foodSet.add("Taco");
foodSet.add("Sandwich");
foodSet.add("Pasta");

console.log(foodSet.has("Burger")); // true
```

size property and clear() method:

```javascript
let foodSet = new Set();
foodSet.add("Burger");
foodSet.add("Taco");
foodSet.add("Sandwich");
foodSet.add("Pasta");

console.log(foodSet.size); // 4
console.log(clear()); // clears out everything
```