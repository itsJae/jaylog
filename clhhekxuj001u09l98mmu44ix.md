---
title: "[JavaScript] Understanding Onclick Event Listener and Various Ways to Code It."
seoTitle: "[JavaScript] Understanding Onclick() Event Listener"
seoDescription: "Onclick(), addEventListener(), DOM, querySelector(), getElementById()"
datePublished: Wed May 10 2023 07:52:42 GMT+0000 (Coordinated Universal Time)
cuid: clhhekxuj001u09l98mmu44ix
slug: javascript-understanding-onclick-event-listener-and-various-ways-to-code-it
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683705052167/b6ac5390-ae96-43b1-a143-f58b5327f163.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683705097164/c85a4795-05eb-43f7-84a4-4ca15bb4beef.jpeg
tags: programming-blogs, javascript, web-development, event-listener, onclick

---

---

### Introduction

This article explores two ways of adding an event listener onclick().

1. Adding onclick="" property in your HTML tag.
    
2. Using addEventListener() method in JavaScript.
    

> [\[JavaScript\] Accessing the DOM Using JavaScript - Explained with Examples.](https://jaylog.hashnode.dev/javascript-accessing-the-dom-using-javascript-explained-with-examples)

---

### Onclick Property in HTML Tag

Onclick property is written in your HTML tag, and receives the function after the assignment operator(=).

That function is executed when the user clicks a button.

Before going through this article, if you don't know how to access the DOM(document object model), check out this article.

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
    <button onclick="doSave();" id="btn">Save</button>
  </body>
    <script>
        function doSave() {
            // code in here will be executed when the user clicks a button
        }
    </script>
</html>
```

---

### Using addEventListener Method in JavaScript

You can use an addEventListener method to do the same task as above.

I prefer using this, and many developers also prefer to do this because your code is more manageable and readable.

Imagine you have a thousand lines of HTML code. It would be quite hard to manage them. So, we can create a function in JavaScript to make it more manageable.

AddEventListener receives two parameters:

1. Event type
    
2. Function that will be executed when the event happens.
    

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
    <button id="btn">Save</button>
  </body>
    <script>
        function addClickEvent() {
            document.querySelector("#btn")
            .addEventListener("click", function() {
                // code in here will be executed when the user clicks a button
            }
        }
    </script>
</html>
```

What the function addClickEvent() is doing:

1. Access the DOM by using the id="btn".
    
2. Specifies that the event listener "click" is added.
    
3. When a user clicks a button, anything inside the function (second parameter of addEventListener) will be executed.