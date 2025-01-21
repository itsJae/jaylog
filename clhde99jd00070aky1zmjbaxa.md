---
title: "[JavaScript] Template Literal and Object Literal for Better Programming."
seoTitle: "Template Literal and Object Literal for Better Programming."
seoDescription: "Your codes are easier to read with object and template literals."
datePublished: Sun May 07 2023 12:32:32 GMT+0000 (Coordinated Universal Time)
cuid: clhde99jd00070aky1zmjbaxa
slug: javascript-template-literal-and-object-literal-for-better-programming
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683462654064/97acb292-18f5-4da8-ac29-48544cc2e656.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683462714091/92bd2f4d-e972-4f1d-a96f-834ade4c1527.jpeg
tags: programming-blogs, javascript, web-development, beginners, objects

---

---

### Introduction

If you know how to use a template and object literal, your codes can be more readable. Especially, if you are working as a team, it is more important.

The syntax is very simple and easy to learn, so let's get started.

---

### Template Literal

If you have programmed in python or java, you might have used formatting before.

In python, you would do:

```python
print("Hello {0}".format("World")) # Hello World
```

In Java:

```java
System.out.printf("Hello %s", "World"); // Hello World
```

It's the same in JavaScript.

In JavaScript:

```javascript
let firstName = "John";
let lastName = "Doe";

console.log("Hi ${firstName} ${lastName}. Welcome!");
// Hi John Doe. Welcome!
```

You need a dollar sign($) followed by curly brackets {}.

Then, the values in the variable will be substituted in that area.

Rather than using plus(+) sign to concatenate strings, using a template literal make your code much easier to read.

---

### Object Literal

If you were to assign a key-value pair in an Object, you might do this:

```javascript
let person = {
    firstName: "John",
    lastName: "Doe",
    email: "john@gmail.com"
}
console.log(person.email) // john@gmail.com
```

If you use an object literal:

```javascript
let str = "email";
let person = {
    firstName: "John",
    lastName: "Doe",
    [str]: "john@gmail.com"
}
console.log(person.email); // john@gmail.com"
```

You can write it in this way if you already have a variable that is the same as the key name that you will be using, you can use square brackets and put the variable name in there.