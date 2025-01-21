---
title: "[JavaScript] Deep Dive into Temporal Dead Zone (TDZ)"
seoTitle: "[JavaScript] Temporal Dead Zone - TDZ"
seoDescription: "In this article, I will be talking about Hoisting and Temporal Dead Zone (TDZ) as well as the differences between var, let and const."
datePublished: Thu May 18 2023 09:06:16 GMT+0000 (Coordinated Universal Time)
cuid: clhswqd25000e09kxhgyz4o4i
slug: javascript-deep-dive-into-temporal-dead-zone-tdz
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684391989396/14dd02af-334f-403d-9539-1f58d57ca533.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684392001675/f2115292-85e2-4462-bd0a-686a3218ec18.jpeg
tags: programming-blogs, javascript, web-development, temporal-dead-zone, refrenceerror

---

---

## Introduction

Can you predict the output of these snippets of JavaScript code? Would the error occur?

```javascript
const hyundai = new Car();

class Car {
  constructor(color) {
    this.color = color;
  }
}
// Error or not?
```

```javascript
myFunc();

function myFunc() {
  console.log("a");
}
// Error or not?
```

```javascript
console.log(myFunc(3, 5));
let myFunc = (a, b) => a + b;
// Error or not?
```

```javascript
console.log(str);
let str = "JS"
// Error or not?
```

The answer is that the last two will have the ReferenceError. Even though your answer was correct, if you guessed it or if you do not know why the ReferenceError occurs, this article will be helpful to you.

In this article, I will be talking about Hoisting and Temporal Dead Zone (TDZ) as well as the differences between var, let and const.

---

## var, let, const, function Declaration

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684395629598/496db7d2-471c-426c-99b7-c978284a0fb2.png align="left")

Whenever you declare a variable, there will be three stages involved.

1. Declaration - Registering a variable in the scope.
    
2. Initialization - Allocating memory and creating a binding for the variable. In this phase, the variable is assigned a value `undefined`.
    
3. Assignment - Assigning a value by using the assignment operator(=).
    

---

![JavaScript Variables Lifecycle: Why let Is Not Hoisted](https://dmitripavlutin.com/static/112c5cd0c5bdd2897944d81c384a648f/76e9a/2.jpg align="left")

For the `var` variables, both the declaration and initialization phases occur at the same time, which means:

```javascript
var a; // declaration and initialization
console.log(a); // no error. prints undefined
```

Although I haven't assigned any values, it already has an undefined value.

You can do something like this:

```javascript
console.log(a); // prints undefined. no error.
var a;
```

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684397023557/161fffd5-0e16-4c07-9aea-49de8b84e6eb.png align="center")

When declaring a function, the stages are like this. All the three phases happen at the same time.

So there is no error when you do this:

```javascript
a(); // no error.
function a() {
    console.log("Jay's Dev Blog");
}
```

---

![JavaScript Variables Lifecycle: Why let Is Not Hoisted](https://dmitripavlutin.com/static/c707482b5c9368354684f45575d739d9/76e9a/4.jpg align="left")

Please have a look at the diagram above. Notice that the declaration and initialization phases do not happen at the same time. More importantly, there is something called Temporal Dead Zone between the two stages. It indicates that "Accessing variable throws ReferenceError".

\*Note. The life cycle diagram is the same for `const`, too.

Let's have a look at this code:

```javascript
console.log(letVar); // Temporal Dead Zone
console.log(constVar); // Temporal Dead Zone
let letVar;
const constVar;
```

Unlike `var`, this results in ReferenceError because the area above letVar and constVar are said to be a temporal dead zone. So, what is the temporal dead zone and why is it said to be the TDZ?

---

## Temporal Dead Zone

Unlike `var`, the declaration and initialization do not occur at the same time, which means there are no values (even undefined) assigned in the memory spaces for both `letVar` and `constVar` variables. Therefore, the JavaScript engine cannot refer to those two variables.

![Don't Use JavaScript Variables Without Knowing Temporal Dead Zone](https://dmitripavlutin.com/static/7973b25e51eb97f6d330c941600f7ad8/c2d7e/temporal-dead-zone-in-javascript.png align="left")

Declarations that are affected by the TDZ

1. let - explained above
    
2. const - explained above
    
3. super()
    
4. class
    
5. default function parameter
    

---

**class**

```javascript
let car = new Car(); // TDZ

class Car {
    constructor(color) {
        this.color = color;
    }
}
```

You can create a new instance after the declaration of the class. Otherwise, the JavaScript engine cannot refer to the class.

---

**super()**

```javascript
class MiniVan extends Car {
    constructor(color, power) {
        this.power; // TDZ
        super();
    }
}
```

The super() must be called before `this` keyword. Before calling super() this binds to TDZ

---

**Default Function Parameter**

```javascript
let a = 5
function myFunc(a = a) {
    return a * a;
}
console.log(myFunc()); // ReferenceError
```

When you want to use the default function parameter, avoid using the same variable name as the default parameter.

Better code:

```javascript
let num = 5;
function myFunction(a = num) {
    return a * a;
}
console.log(myFunc()); // 25
```

---

Declarations that are **NOT** affected by the TDZ

1. var - explained above
    
2. function - explained above
    

These two are explained above. They are not affected because the declaration and initialization phases occur at the same time, so `undefined` is assigned in the memory spaces. This means that the JavaScript engine can refer to the variable or function.