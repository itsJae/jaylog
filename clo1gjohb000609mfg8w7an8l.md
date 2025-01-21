---
title: "[JavaScript] Understanding Event Capturing, Bubbling, Delegation"
seoTitle: "[JavaScript] Event Capturing, Bubbling, Delegation"
seoDescription: "Capturing phase - The event goes down from top to bottom

Target phase - reaches the target event

Bubbling - The event goes up from bottom to top"
datePublished: Sun Oct 22 2023 12:41:20 GMT+0000 (Coordinated Universal Time)
cuid: clo1gjohb000609mfg8w7an8l
slug: javascript-understanding-event-capturing-bubbling-delegation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697947146442/6e213b07-f155-4405-b6ac-83c7d11bf359.avif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697978409662/872b16f1-307e-4a74-a23b-6d7ec99bec93.avif
tags: javascript, events, eventbubbling, event-delegation, event-capturing-and-event-bubbling-in-javascript

---

---

## Introduction

In this article, I will be talking about how the browser detects that there is an event.

The standard DOM Events describes 3 phases of event propagation:

1. Capturing phase - The event goes down from top to bottom
    
2. Target phase - reaches the target event
    
3. Bubbling - The event goes up from bottom to top
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697974367200/c17d7088-4f9c-4ce2-9b0a-5b7cdf6c0372.png align="center")

---

## Event Bubbling

In the event bubbling, the event that occurred on the child element will also occur on its parent, then all the way up on the other parents.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697973777369/b6538de4-04af-421e-813f-cc2599b94c1c.png align="center")

For Example:

```xml
<form onclick="alert('FORM')">FORM Tag
    <div onclick="alert('DIV')">DIV Tag
        <p onclick="alert('P')">P Tag</p>
    </div>
</form>
```

Three elements are nested, so when you click on the &lt;p&gt; element, the event occurs, and the event handler will move up. So, now the event handler is on the &lt;div&gt;, then on the &lt;form&gt;.

We describe this situation as "event bubbling" because it has the characteristic of a bubble, which moves up until it reaches the top.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697974367200/c17d7088-4f9c-4ce2-9b0a-5b7cdf6c0372.png align="center")

Let's have a look at this diagram.

The window object, which is at the very top, has the biggest size, then the document, then &lt;html&gt;, then &lt;body&gt; and so on. The child element is always the innermost and has the smallest size. So, the event bubbling is something that really makes sense because clicking on the &lt;button&gt; is the same as clicking on the &lt;div&gt;

---

## Event Capturing

The event capturing is opposite to event bubbling. The event goes from top to bottom.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697978372953/5150df22-edf9-4ff5-aa01-176fd5e1272c.png align="center")

In order to check how capturing happens when an event occurs, you need to put an option in the third parameter of `addEventListener()` method.

The format is like this -&gt; `addEventListener(event, function(), capture: true)` you can see the `capture: true` is added. This will allow you to see the flow of capturing.

For example:

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Document</title>
    <style>
      body * {
        margin: 10px;
        border: 1px solid red;
      }
    </style>
  </head>
  <body>
    <form>
      FORM
      <div>
        DIV
        <p>P</p>
      </div>
    </form>
    <script>
      for (let element of document.querySelectorAll("*")) {
        element.addEventListener("click", (e) => alert(`Capturing: ${elem.tagName}`), true);
        element.addEventListener("click", (e) => alert(`Bubbling: ${elem.tagName}`));
      }
    </script>
  </body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697973410797/a7edd8a1-07fa-44bf-b14c-d6043a368613.png align="center")

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697978399322/7d3735f2-9c75-4388-a689-fbf6e37080c2.png align="center")

---

## e.stopPropagation()

The problem with bubbling is that the event on the parent or ancestor occurs when the event on the child occurs.

For example,

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697973410797/a7edd8a1-07fa-44bf-b14c-d6043a368613.png align="center")

You only want the event on &lt;div&gt; element to happen, but then the event on &lt;form&gt; will happen as well. To prevent such a scenario, we can use the e.stopPropagation() method.

```xml
<!DOCTYPE html>
<html lang="en">

<head>
  <title>Event Bubbling</title>
  <style>
    body * {
      margin: 10px;
      border: 1px solid red;
    }
  </style>
</head>

<body>
  <form>FORM
    <div">DIV
      <p>P</p>
    </div>
  </form>
</body>
<script>
    const form = document.querySelector('form');
    const div = document.querySelector('div');
    const p = document.querySelector('p');

    form.addEventListener('click', function(e) {
        console.log("<form> onclick event")
    })

    div.addEventListener('click', function(e) {
        console.log("<div> onclick event")
    })

    p.addEventListener('click', function(e) {
        e.stopPropagation();
        console.log("only <p> event occurring.")
    })
</script>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697975603928/572b9671-9729-4198-833d-7defbb524b52.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697975800998/89a48457-4649-417f-abf2-c1af878c0abf.png align="center")

---

## Event Delegation

> In the event delegation, the ancestor element controls the child element

In the previous example:

```xml
<form onclick="alert('FORM')">FORM Tag
    <div onclick="alert('DIV')">DIV Tag
        <p onclick="alert('P')">P Tag</p>
    </div>
</form>
```

We had to put `onclick=""` on every element to add an event listener.

Let's have a look at this example:

```xml
<!DOCTYPE html>
<html>
<head>
    <title>Event Delegation</title>
    <meta charset="UTF-8" />
</head>

<body>
    <div>
        <button class="buttonClass">Click me</button>
        <button class="buttonClass">Click me</button>
    </div>

    <script>
        const buttons = document.getElementsByClassName("buttonClass");
        for (const button of buttons) {
            button.addEventListener("click", () => alert('clicked'));
        }
    </script>
</body>
</html>
```

The &lt;button&gt; elements are controlling the event. Now, what if I want to add more buttons? Will the event occur?

```xml
<!DOCTYPE html>
<html>
<head>
    <title>Event Delegation</title>
    <meta charset="UTF-8" />
</head>

<body>
    <div id="buttons">
        <button class="buttonClass">Click me</button>
        <button class="buttonClass">Click me</button>
    </div>

    <script>
        const buttons = document.getElementsByClassName("buttonClass");
        for (const button of buttons) {
            button.addEventListener("click", () => alert('clicked'));
        }

        let newButton = document.createElement('button');
        let buttonList = document.querySelector('#buttons');
        newButton.innerText = "Click me";
        newButton.setAttribute('class', 'buttonClass');
        buttonList.appendChild(newButton);
    </script>
</body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697977867848/039bb817-e7df-4db2-878b-9333ccc6a561.png align="center")

The third button (new one) is now added, but nothing happens when clicked. It is not working because the onclick events on the first and second buttons were added before creating the third button.

SOLUTION: Event delegation.

We can make the &lt;div&gt; control its child elements, which are &lt;button&gt; elements.

```xml
<!DOCTYPE html>
<html>
<head>
  <title>Event Delegation</title>
  <meta charset="UTF-8" />
</head>
<body>
  <div id="buttons">
    <button class="buttonClass">Click me</button>
    <button class="buttonClass">Click me</button>
  </div>

  <script>
    // changed part.
    const div = document.getElementById("buttons");
    div.addEventListener("click", () => alert('clicked'));

    // this part is not modified.
    let buttonList = document.querySelector('#buttons');
    let button = document.createElement('button');

    button.setAttribute('class', 'buttonClass');
    button.innerText = 'Click me';
    buttonList.appendChild(button);
        
  </script>
</body>
</html>
```