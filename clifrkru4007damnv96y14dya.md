---
title: "[TypeScript]  Tutorial for Compiling TypeScript & Compiler Options"
seoTitle: "[TypeScript]  Tutorial for Compiling TypeScript & Compiler Options"
seoDescription: "This article will be a tutorial/guide for those who want to know how to compile your TypeScript file into a JavaScript file."
datePublished: Sat Jun 03 2023 09:00:39 GMT+0000 (Coordinated Universal Time)
cuid: clifrkru4007damnv96y14dya
slug: typescript-tutorial-for-compiling-typescript-compiler-options
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1685678540425/a5d45d5f-c0d4-4adb-ba1f-6cbf3584fd86.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1685678600365/d0ea488b-f1e0-4f94-b962-43bfae45a731.png
tags: programming-blogs, web-development, typescript, compiler, compiler-option

---

---

## Introduction

This article will be a tutorial/guide for those who want to know how to compile your TypeScript file into a JavaScript file.

Moreover, I will be introducing what is a compiler option, and what options you can give to a compiler.

---

## Downloading Node.js

In order to compile the TS file, please make sure that you have downloaded node.js with a version later than 10. If you want to check if node.js is already installed, open a terminal or cmd to type a command.

```javascript
node -v
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685679552465/484cd932-195e-4703-9eda-62a8401b024b.png align="left")

If you have node.js you will get the version name.

If not, please download the LTS version here: [Node.js](https://nodejs.org/ko)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685679651556/86fc9397-fc8c-49ca-80eb-097818bf63ab.png align="left")

---

## Compiling

> In TypeScript, you need to "compile" your TypeScript file into a JavaScript file to run your program.

That's what compiling means. It's just like converting your .doc file into .pdf file.

Let's say we have this TypeScript file (`index.ts`):

```javascript
function sum(a: number, b: number): number {
    return a + b;
}

console.log(sum(10, 20));
```

Right-click on the folder that has the TypeScript file you want to compile.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685679855541/177606ae-8bcc-48c9-a634-3510dccbc3b1.png align="center")

Open the terminal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685679984384/3b8c6b83-f0ea-442b-b621-0347aabcdbd6.png align="center")

Install TypeScript Globally

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685680109646/4d0de6c3-206e-44b4-99cf-a47489d91788.png align="center")

Compile TypeScript

Compile TS file by using a command `tsc` (stands for TypeScript Compile) followed by the file name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685680247907/4bb56d45-ed4f-48ea-b00d-9937b9e28743.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1685680204804/e48eed0e-cfb9-4d99-9bf5-b81e51422b70.png align="center")

Now you have index.js, which is a JavaScript file (index.js):

```javascript
function sum(a, b) {
    return a + b;
}
console.log(sum(10, 20));
```

Compared to a TypeScript file (index.ts):

```javascript
function sum(a: number, b: number): number {
    return a + b;
}

console.log(sum(10, 20));
```

---

## Compiler Options

When you compile your TypeSript file, you can give options to it.

For example:

```javascript
{
    "complierOptions": {
        "allowJs": true, 
        "checkJs": true, 
        "noImplicitAny": true     
    }
}
// https://www.typescriptlang.org/tsconfig
```

Those are only a few of the compiler options.

If you want to find out more about it, TypeScript's website has a list of them.

TypeScript website: [TypeScript: TSConfig Reference](https://www.typescriptlang.org/tsconfig)