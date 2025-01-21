---
title: "[JavaScript ES6] Map Object in JavaScript - How to Use It. Explained with Examples."
seoTitle: "Map Object in JavaScript - How to Use It. Explained with Examples."
seoDescription: "Explore how to use Map Object and its useful methods. With Map Object, you can program more efficiently when dealing with an object."
datePublished: Wed May 03 2023 22:59:49 GMT+0000 (Coordinated Universal Time)
cuid: clh8awj76000309mp4ql2cg4l
slug: javascript-es6-map-object-in-javascript-how-to-use-it-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683153403718/b993752f-33ac-413b-9f07-9b19f2833b25.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683154746157/36d83ddd-dcd2-456b-81ac-38656e60fb3b.png
tags: programming-blogs, javascript, web-development, es6, map

---

Explore how to use Map Object and its useful methods. With Map Object, you can program more efficiently when dealing with an object.

---

### Introduction

Even though Map Object does a similar thing as what an object does, it has distinct advantages.

1. It allows your key to hold any data type, such as an array, number and so on. On the other hand, an object only allows strings as a key.
    
2. It remembers the order of insertion order of the keys.
    
3. It has a property called size that represents the size of the map.
    

---

### Map Object

There are several methods/properties that you want to know when you use Map Object.

1. set() to add a key-value pair
    
2. get() to retrieve a value by using a key name.
    
3. has() to check if a certain key exists.
    
4. delete() to delete a key-value pair.
    
5. size property to check the size of your map.
    
6. clear() to clear out your map.
    

```javascript
let personMap = new Map();

// set()
personMap.set("name", "John");
personMap.set("email", "john@gmail.com");
personMap.set("gender", "male");
console.log(personMap);
// {'name' => 'John', 'email' => 'john@gmail.com', 'gender' => 'male'}

// get()
console.log(personMap.get("name")); // John

// has()
console.log(personMap.has("email")); // true
console.log(personMap.has("address")); // false

// delete() if no key is found, it returns false. If found, returns true.
console.log(personMap.delete("gender")); // true
console.log(personMap.delete("address")); // false
console.log(personMap); // {'name' => 'John', 'email' => 'john@gmail.com'}

// size
console.log(personMap.size); // 2

// clear()
personMap.clear(); // clears out everything.
```