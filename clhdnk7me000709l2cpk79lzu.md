---
title: "[JavaScript] Understanding the Regular Expression - Explained with Examples."
seoTitle: "Understanding the Regular Expression - Explained with Examples."
seoDescription: "Understand the Regular Expression with an email input validation."
datePublished: Sun May 07 2023 16:53:00 GMT+0000 (Coordinated Universal Time)
cuid: clhdnk7me000709l2cpk79lzu
slug: javascript-understanding-the-regular-expression-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683474251635/e00a0e94-8136-46ce-b4d8-e31334838d44.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683478350417/652850c5-dda0-49c1-bb55-9f412642db7d.jpeg
tags: programming-blogs, javascript, web-development, beginners, regular-expressions

---

---

### Introduction

A regular expression is a pattern of characters. It is used to match with a certain string and see if it matches a certain condition.

Because it is too complicated, most developers do not memorize it, but you need to be able to understand it and know how to read it.

In this article, we will be using a regular expression to validate the user's email. This should help you to understand a regular expression.

In addition, this article talks about two methods that can be used with a regular expression:

1. test()
    
2. search()
    
3. match()
    

---

### Test(), Search() and Match()

Test() is used to test if the regular expression matches the string.

If it matches, it returns true. If not, it returns false.

Syntax:

```javascript
let str = "123abc456def";
const regExp = /[0-9]{2}a/g; // regular expression 
console.log(regExp.test(str)); // true
```

Search() is a method that is used with a string.

It searches the first element that is given in the parameter and returns the index number.

If it cannot find one, it returns -1.

```javascript
let str = "123abc456def";
const regExp = /[0-9]{2}a/g; // regular expression 
let result = str.search(regExp);
console.log(result); // 1
```

Match() puts matching values into an array and returns the array.

```javascript
let str = "123abc456def";
const regExp = /[a-zA-Z]/g;
result = str.match(regExp);
console.log(result); // ['23a']
```

---

### Regular Expression

We will be writing a regular expression to match or validate the user's email.

Possible email inputs:

1. johndoe@gmail.com
    
2. john.doe@gmail.com
    
3. johndoe11@gmail.com
    
4. john7doe@gmail.com
    
5. jo2hn3d2oe@gmail.com
    
6. johndoe@domain.com.ca
    

The regular expression must match any possible email inputs.

```javascript
const regexpEmail = 
/^([a-z]+\d*)+(\.?[a-z]+\d*)+@([a-z]+\d*)+(\.[a-z]{2,3})+$/;
```

Meanings of Characters:

* ^ character - beginning of input.
    
* $ character - ending of input.
    
* plus (+) - one or more than one.
    
* star(\*) - zero or more than zero.
    
* question mark(?) - only zero or one.
    
* \[a-z\] - the lowercase letter must be placed.
    
* \\d - number must be placed.
    
* \\. - dot(.) must be placed.
    
    * We use backslash because dot(.) is a special character.
        
    * For example, if you want to ensure \\d is placed, you can do: \\\\d because \\d has a meaning in a regular expression.
        

I will explain each part:

(\[a-z\]+\\d\*)+ means more than one lowercase letter and zero or more can be repeated more than one time becuase the whole thing is enclosed by the bracket and the plus(+) sign is at the back.

(\\.?\[a-z\]+\\d\*)+ means dot(.) can be placed zero or one time only, then everything else is the same as above.

@(\[a-z\]+\\d\*) means that @ symbol must be placed, then everything else is the same as above.

(\\.?\[a-z\]{2, 3})+ is for the top level domain (TLD) like .com, .org, .net and .gov. It means that a dot(.) must come, then only a string with a length of either 2 or 3 can be placed. As the whole thing is encolsed by the bracket followed by the plus(+), this can be repeated one or more than one time.