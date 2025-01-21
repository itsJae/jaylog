---
title: "[JavaScript] Deep Dive into the THIS Keyword"
seoTitle: "[JavaScript] Deep Dive into the THIS Keyword"
seoDescription: "In this article, I will talk about how you can determine where this keyword points to."
datePublished: Fri May 19 2023 22:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clhv3u2ow02lxsinv2j98gb90
slug: javascript-deep-dive-into-the-this-keyword
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684480201780/29f76356-e16e-4181-9888-f6f31ac04f77.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684494553024/341e7448-2725-425f-864c-7f0c44fcaf5c.jpeg
tags: programming-blogs, javascript, web-development, this, this-keyword

---

---

## Introduction

In this article, I will talk about how you can determine where `this` keyword points to. By default, `this` keyword points to the Window Object, but you can change where it refers to.

> Where this points to depends on when the function is called or this is invoked.

There are four(4)ways to change the referring object:

1. object.method()
    
2. new Object()
    
3. arrow function
    
4. bind(), call(), apply()
    

---

## Default

```javascript
console.log(this); // Window Object
```

If you console.log `this`, it prints out the window object.

In a strict mode, this is undefined:

```javascript
function stritctThis() {
    'use strict';
    console.log(this);   
}
strictThis(); // undefined
```

---

## Object.method()

```javascript
const obj = {
  name: "John Doe",
  printName() {
    console.log(this.name);
  },
};
obj.printName(); // John Doe
```

In the introduction, I emphasized this sentence:

> Where this points to depends on when the function is called or this is invoked.

In the code above, `this` keyword in the `printName()` function refers to obj when the function `printName()` is called. So, this keyword points to the `obj` object.

---

## new Object()

```javascript
class Stduent {
    constructor(name, studentID) {
        this.name = name;
        this.studentID = studentID;
    }
}
const stu = new Stduent("John Doe", 10245845);
console.log(stu.name); // John Doe
```

Now this refers to the Student object. In this case, the object that "this" keyword refers to is decided when the `new` keyword is used.

---

## Arrow Function

```javascript
const object = {
  name: "John Doe",
  printName() {
    const inner = () => {
      console.log(this.name);
    };
    inner();
  },
};
object.printName(); // John Doe
```

There is a difference between using a function like the earlier example and an arrow function. It changes which object this refers to. In the previous example, this.name inside the printName() function referred to the name in the obj. However, when you use an arrow function, the result is different.

The `this` keyword in the arrow function refers to the parent function. When the printName() is called (the last line), object.method() is used, and I mentioned earlier that it changes an object that this keyword refers to. So, printName() refers to `object`

Therefore, `this` in inner() is referring to the same object as the printName(), NOT the window object.

---

## bind(), call(), apply()

If you want to manually change which object this refers to, you can use either bind(), call() or apply().

```javascript
function printName(city, zipCode) {
    console.log(this.name, city, zipCode);
}

const person = { name: "John Doe" };

printName.bind(person)();
printName.call(person, "Burnaby", "V3A 7X7");
printName.apply(person, ["Vancouver", "V3A 9Z3"] );
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698072518098/10332133-42b9-485b-aa1e-96fb63e07346.png align="center")

apply() method requires you to put additional arguments in an array, whereas call() does not require you to do that.

Morevoer, you may wonder why bind() has one more bracket like bind()(). You need to add an additional bracket if you want to print it out. If you only want to change where this points to, you do not need to include it. So, bind() can be stored in a variable, and used later. However, call() and apply() returns a value immediately.

For example:

```javascript
// bind() example.
function myFunc(lang) {
    if (lang.toLowerCase() === "kor") {
        console.log(this.korGreeting);
    } else if (lang.toLowerCase() === "eng") {
        console.log(this.engGreeting);
    } else {
        console.log("Invalid input");
    }
}

const greeting = {
    korGreeting: "Annyeong!",
    engGreeting: "Hello!"
};

// stores in a separate variable.
const language = myFunc.bind(greeting);
language("kor"); // Annyeong
```

---

## Conclusion

The most important takeaway from today's article is this sentence:

> Which object this refers to depends on when the function is called or this is invoked.

And there are four(4) ways to change where this points to:

1. object.method() - points to an object
    
2. new keyword - points to a certain object, such as Student in the example.
    
3. arrow function - points to the parent function
    
4. bind, call, apply - to manually set it.
    
5. `this` keyword in the function - points to a window object.
    
6. `this` keyword in the constructor - points to an empty object.