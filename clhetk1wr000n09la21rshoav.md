---
title: "[JavaScript] Accessing the DOM Using JavaScript - Explained with Examples."
seoTitle: "Accessing the DOM Using JavaScript - Explained with Examples."
seoDescription: "Explore how to access to the document object model using JavaScript. Beginner Friendly."
datePublished: Mon May 08 2023 12:28:36 GMT+0000 (Coordinated Universal Time)
cuid: clhetk1wr000n09la21rshoav
slug: javascript-accessing-the-dom-using-javascript-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683536317240/1bd33740-aea6-4c0e-8c4e-744c874b4096.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683548895384/a1956ea9-4f91-437f-83fd-e44c64d064c1.jpeg
tags: programming-blogs, javascript, web-development, dom, dom-manipulation

---

---

### Introduction

This article covers useful methods that you need to access a document object model (DOM) using JavaScript.

Methods that will be covered:

1. getElementById().
    
2. getElementsByClassName().
    
3. getElementsByTagname().
    
4. getElementsByName().
    
5. querySelector().
    
6. querySelectorAll().
    

> If you want to find out more about the DOM, check out this article: [How to Optimize Your Website?](https://jaylog.hashnode.dev/how-to-optimize-your-website-dom-tree-cssom-tree-rendering-tree)

---

### getElementBy...()

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
    <div>
      <label for="userId">User ID</label>
      <input type="text" name="" id="userId" class="form-control" />
    </div>
    <div>
      <label for="userPW">Password</label>
      <input type="text" name="" id="userPW" class="form-control" />
    </div>
    <div>
      <input type="checkbox" name="chk_pl" id="chk_html" value="HTML" />
      <label for="chk_html">HTML</label>
      <input type="checkbox" name="chk_pl" id="chk_css" value="CSS" />
      <label for="chk_css">CSS</label>
      <input type="checkbox" name="chk_pl" id="chk_js" value="JS" />
      <label for="chk_js">JavaScript</label>
      <button onclick="doSave();">Save</button>
    </div>
    <script>
        // key in the same id to access the HTML element you want.
        console.log(document.getElementById("user_Id"));
        // <input type="text" name="" id="userId" class="form-control" />
        
        // key in the tag name that you want to access.
        console.log(document.getElementsByTagName("label"));
        // prints HTML collection(5) because there are 5 label tags.

        // key in the class name that you want to access.
        console.log(document.getElementsbyClassName("form-control"));
        // prints HTML collection(2) because there are 2 tags with the class name = form-control.

        function doSave() {
            let chks = document.getElementsByName("chk_pl") // returns an array
            let checkedValue = [];
            for (const chk of chks) {
                if (chk.chekced) { // if the checkbox is checked
                     chkedValue.push(chk.value);
                } 
            }
            console.log(checkedValue); 
            // the output depends on what is checked.
        }
    </script>
  </body>
</html>
```

1. getElementById() receives one parameter, which is the id value. Then, you can access a DOM.
    
2. getElementsByTagName() receives one parameter, which is the tag name. Then, you can access the HTML elements with that specific tag name.
    
3. getElementsByClassName() receives the class name. Then, you can access the HTML elements with that specific class name.
    
4. getElementsByName() receives the name. Then, you can access the HTML elements with that specific class name.
    

---

### QuerySelector() & QuerySelectorAll()

querySelector() is the same as the getElementById().

querySelectorAll() is the same as the other three.

Do you notice that getElementById() "element" is singular?

But the "element" of getElementsByName or TagName or ClassName is plural, "elements". Those refer to querySelectorAll()

You can use these two methods to access the DOM using the CSS selectors.

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* id selector */
      #userId {
      }

      /* class selector */
      .form-control {
      }

      /* tag selector */
      label {
      }

    </style>
  </head>
  <body>
    <div>
      <label for="userId">User ID</label>
      <input type="text" name="" id="userId" class="form-control" />
    </div>
    <div>
      <label for="userPW">Password</label>
      <input type="text" name="" id="userPW" class="form-control" />
    </div>
    <div>
      <input type="checkbox" name="chk_pl" id="chk_html" value="HTML" />
      <label for="chk_html">HTML</label>
      <input type="checkbox" name="chk_pl" id="chk_css" value="CSS" />
      <label for="chk_css">CSS</label>
      <input type="checkbox" name="chk_pl" id="chk_js" value="JS" />
      <label for="chk_js">JavaScript</label>
      <button onclick="doSave();">Save</button>
      <button onclick="doSave2();">Save2</button>
    </div>
    <script>
        // same as getElementById()
        console.log(querySelector("#userId"));
    
        // same as getElementsByTagName()
        console.log(querySelectorAll("label"));

        // same as getElementsByCalssName()
        console.log(querySelectorAll(".form-control"))

        function doSave2() {

            const checkedElements = document.querySelectorAll("[name=chk_pl]:checked");
            let checkedValue = [];
            for (const chk of checkedElements) {
                if (chk.checked) {
                    checkedValue.push(chk.value);
                }
            }
            console.log(checkedValue);
        }
    </script>
  </body>
</html>
```