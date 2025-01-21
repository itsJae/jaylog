---
title: "[JavaScript] All About JavaScript String Object Methods, Explained with Real Life Usages - Part 2."
seoTitle: "JavaScript String Object Methods, Explained with Real Life Usages"
seoDescription: "Explore useful String object methods, such as split(), concat(), trim(), padStart(), padEnd(), charAt(), charCodeAt(), startsWith(), endsWith()."
datePublished: Wed May 03 2023 14:25:20 GMT+0000 (Coordinated Universal Time)
cuid: clh7siwnd000b0al47o8zb5c0
slug: javascript-all-about-javascript-string-object-methods-explained-with-real-life-usages-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683019483236/33b008dc-9c9c-4d85-a59d-c9cefc4c66eb.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683123825015/abc9ee8e-a580-49f1-a1c6-f28c898ec964.png
tags: programming-blogs, javascript, web-development, string, methods

---

---

### **JavaScript String Object Methods That Will Be Covered In Part 2:**

1. concat().
    
2. trim().
    
3. padStart().
    
4. padEnd().
    
5. charAt().
    
6. charCodeAt().
    
7. startsWith().
    
8. endsWith().
    
9. split().
    

If you haven't read the part 1, click [here](https://jaylog.hashnode.dev/javascript-all-about-javascript-string-object-methods-explained-with-real-life-usages-part-1) to check out the part 1.

---

### 1\. concat()

Concat() method allows you to concatenate strings together.

You can put multiple parameters if you need to concatenate more than two strings.

```javascript
let str1 = "Java";
let str2 = "Script";
console.log(str1.concat(str2)) // JavaScript

// concatenating more than two strings
console.log("Hyper".concat(" ", "Text"," ", "Markup"," ", "Language"));
// Prints Hyper Text Markup Language
```

---

### 2\. trim()

Trim() method removes white spaces from both sides of the string.

```javascript
let str = "          Hello World         ";
console.log(str.trim()); // Hello World
```

---

### 3\. padStart()

padStart() receives two parameters.

1. The final length of the string
    
2. The character you want to add
    

It is much easier to explain with an example, so let's have a look.

```javascript
let studentNum = "19";
console.log(studentNum.padStart(6, "0")); // 000019
console.log(studentNum.padStart(2, "0")); // 19. Nothing to add on
```

---

### 4\. padEnd()

padEnd() is the opposite of padStart(). It will add the element starting from the end.

padEnd() receives two parameters

1. The final length of the string
    
2. The character you want to add
    

```javascript
let str = "xxyy";
console.log(str.padEnd(6, "z")); // xxyyzz
```

---

### 5\. charAt()

charAt() returns a character at a given index.

```javascript
let str = "hashnode";
console.log(str.charAt(0)); // h
console.log(str.charAt(4)); // n
```

---

### 6\. charCodeAt()

charCodeAt() returns the Unicode of the character at a given index.

For example, the Unicode of character A is 65.

```javascript
let str = "Apple";
console.log(str.charCodeAt(0)); // 65
```

---

### 7\. startsWith()

startsWith() method returns boolean type (true/false).

It returns true if a string starts with a given string set.

It receives one parameter as String type.

In real life, it can be used in this way:

```javascript
let url = "http://website.com";
console.log(url.startsWith("http://")); // true
```

---

### 8\. endsWith()

endsWith() method returns boolean type (true/false) just like startsWith() method.

It returns false if a string ends with a given string set.

It receives one parameter as String type.

In real life, it can be used in this way:

```javascript
let file = "abc.pdf";
console.log(file.endsWith(".pdf")); // true
```

---

### 9\. split()

split() method is very important and handy in JavaScript.

split() splits your string into an array of substrings.

Take a note that split() method will not change your original string.

Also, it only receives on parameter as a string type.

```javascript
let emails = "john@gmail.com, mary@gmail.com, jane@gmail.com";
console.log(emails.split(","));
// returns ["john@gmail.com, mary@gmail.com, jane@gmail.com"]

let sentence = "Hello World";
console.log(sentence.split(" "));
// returns ["Hello", "World"]
```