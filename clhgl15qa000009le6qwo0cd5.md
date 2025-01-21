---
title: "[JavaScript] Tutorial for Disabling a Button Until the User Enters Something."
seoTitle: "[JavaScript] Tutorial for Disabling a Button Using JavaScript."
seoDescription: "Make a button that is disabled until the user enters something in 5 minutes. It's Beginner Friendly!"
datePublished: Tue May 09 2023 18:05:30 GMT+0000 (Coordinated Universal Time)
cuid: clhgl15qa000009le6qwo0cd5
slug: javascript-tutorial-for-disabling-a-button-until-the-user-enters-something
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683654876207/b0b698b7-fc9b-41e6-bb8f-b0e9f5ba7250.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683654887890/3e3a7a72-a1f0-4d9f-b9b3-47ed30a1cc5d.png
tags: programming-blogs, javascript, web-development, dom, beginners

---

Make a button that is disabled until the user enters something in 5 minutes. It's Beginner Friendly!

---

### Introduction

This article introduces how to make a button that is disabled until the user inputs a value.

If you add this feature to your website, users cannot click the button unless they have entered a value.

Before going through this article, if you don't know how to access the DOM(document object model), check out this article:

> [\[JavaScript\] Accessing the DOM Using JavaScript - Explained with Examples.](https://jaylog.hashnode.dev/javascript-accessing-the-dom-using-javascript-explained-with-examples)

---

### Tutorial

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
    <input type="text" name="" id="userInput" onkeyup="validateInput();" />
    <button onclick="doSave()" id="btn" disabled>Save</button>
    <script>
      // executed when the user inputs a value.
      function validateInput() {
        if (document.querySelector("#userInput").value.length <= 0) {
          document.querySelector("#btn").disabled = true;
        } else {
          document.querySelector("#btn").disabled = false;
        }
      }

      // executed when the button is clicked
      function doSave() {
        console.log(document.querySelector("#userInput").value);
        document.querySelector("#btn").disabled = true;
        setTimeout(function () {
          document.querySelector("#btn").disabled = false;
        }, 2000);
      }
    </script>
  </body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683654311266/295d2b97-1c5d-45f3-84b8-3cf04a611b82.png align="center")

The Save button is disabled when there is no value entered.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683654343397/971489e1-d48d-45ea-a608-b8c58c56a282.png align="center")

Then, it allows a user to click on it once the value is entered.

After clicking the save button, the button is disabled for two seconds.

---

### HTML Tags

```xml
<input type="text" name="" id="userInput" onkeyup="validateInput();" />
<button onclick="doSave()" id="btn" disabled>Save</button>
```

The &lt;input&gt; tag has onkeyup event listener. This event listener will happen when the user types something.

The &lt;button&gt; tag has onclick event listener. This will happen when the user clicks the save button. Moreover, the &lt;button&gt; tag has "disabled". This means that the button will be disabled to the user in the initial phase, but it will become enabled when the user enters something.

---

### function validateInput()

This function is called when the user enters a value because I added an event listener onkeyup, which means when a user presses a key, the function is executed.

This function has an if-else statement to decide whether we should disable the button or not.

The button is disabled when the user has no input, which is done by these lines of code:

```javascript
if (document.querySelector("#userInput").value.length <= 0) {
    document.querySelector("#btn").disabled = true;
}
```

If there are any inputs from the user, the button is enabled, which is done by these lines of code:

```javascript
else {
    document.querySelector("#btn").disabled = false;
}
```

---

### function doSave()

This function is executed when a user clicks a button.

The function prints out what the user has entered and then disables the button for two seconds.

Let me briefly explain the setTimeout() method.

setTimeout() receives two parameters

1. A function that will be executed.
    
2. Time in milliseconds. In the example, 2000 corresponds to 2 seconds.
    

```javascript
setTimeout(function () {
    document.querySelector("#btn").disabled = false;
}, 2000);
```

Anything written in the function will be executed after two(2) seconds.