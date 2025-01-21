---
title: "[JavaScript] What Are the Input Event Listener and Event.target Property?"
seoTitle: "What Are the Input Event Listener and Event.target Property?"
seoDescription: "Explore what event.target means and how it works as well as how to use the input event listener."
datePublished: Wed May 10 2023 14:03:52 GMT+0000 (Coordinated Universal Time)
cuid: clhhru9ui000k0al7hx0s2d97
slug: javascript-what-are-the-input-event-listener-and-eventtarget-property
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683727327717/00ccf4e2-5f89-4484-a5f9-2e321fcf8b11.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683727405600/cd315135-e89f-4be7-8275-b99c675093f0.webp
tags: programming-blogs, javascript, web-development, input, event-listener

---

---

### Introduction

This article mainly talks about the input event listener, but also event.target property because I want to have a better and deeper understanding of both.

The input event happens right before users take their hands off the keycap.

The order of the user pressing a key is like this:

1. keypress - happens when a user presses a key
    
2. keydown - happens when a user fully presses a key.
    
3. input - happens when a value entered by the user is input.
    
4. keyup - happens when the key is fully up.
    

If you cannot image this process, think of yourself pressing any keys on your keyboard. The key will first be pressed by you, then it goes down, you enter a value to input data, then key comes up.

> keypress -&gt; keydown -&gt; input -&gt; keyup

---

### Characteristic of Input Event Listener

Input happens when the user enters a value, and that value goes into the value property.

However, that value is not visible to the user. The value is shown to the user when the keyup event happens

We can use this characteristic to make our program/code better.

---

### Implementation

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <label for="numberInput" />Only Numbers Are Allowed
    <input type="text" id="numberInput" oninput="onlyNumbers();" value=""/>
    <script>
        function onlyNumbers() {
            const regExp = /\D/g; // finds all the non-numeric characters.
            event.target.value = event.target.value.replace(regExp, "");
        }
    </script>
  </body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683725606272/81fd6518-2125-4f68-a351-773b1918cb28.png align="center")

If you run this code on your IDE, you will see that it does not allow you to input any non-numeric characters.

The regular expression `/\D/g` means to find all the non-numeric characters.

Then this code will eliminate any non-numeric characters.

```javascript
event.target.value = event.target.value.replace(regExp, "");
```

If you want to find out more about the regular expression, check out this article:

> [\[JavaScript\] Understanding the Regular Expression](https://jaylog.hashnode.dev/javascript-understanding-the-regular-expression-explained-with-examples)

---

### Event.target

I started to write this article because I wanted to learn more about `event.target`.

Basically, `event.target` returns the element where the event has occurred.

In the example above, event.target refers to the `<input/>` tag, because the function `onlyNumbers()` is residing in the `<input/>` tag.

So, e`vent.target.value` will return the value entered by users.

Another way of getting the value of a specific element is `document.getElementById().value`

They can be written interchangeably, but it is also important to research and understand the difference. It is a good practice to always think about why they provide methods that do the same thing.

The differences:

1. `getElementById()` allows you to key in an id to access the DOM. Therefore, it is useful when you know the id of an element you want to access.
    
2. `event.target` is used with key related events, such as keypress, keydown, input and keyup.