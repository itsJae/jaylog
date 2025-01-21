---
title: "[React.js] Error: GH013: Repository rule violations found"
seoTitle: "[React.js] Error: GH013: Repository rule violations found"
seoDescription: "This error occurred when I git push -u origin main to push my commits."
datePublished: Wed Nov 13 2024 14:42:18 GMT+0000 (Coordinated Universal Time)
cuid: cm3fzprj2000h09ie02y6eokp
slug: reactjs-error-gh013-repository-rule-violations-found
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1731508447801/fdf30034-8d71-40d6-8012-ea29f1cf66ea.png
tags: error, github, error-handling, reactjs, commands

---

---

## About Error

This error occurred when I `git push -u origin main` to push my commits.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1731508531374/5baf361d-baaf-4050-99f6-73e12c266a74.png align="center")

The reason was because I wrote personal access token in the `index.html` file. I copied and pasted on there because it’s something I can never remember, but I will need it at some point in the future.

The problem is that github scans all these informations related to security issues, so they blocked my push.

---

## Solution

1. In the error message, there is a link that directs you to the webpage that asks you about the sensitive information in your file. Once you tell them a reason, they will allow your push.
    
2. `git push -f origin main` `-f` means force. You can anyway push your files.
    
3. Delete sensitive information. Github is a space where everyone can see your code (if your repo is public). So, it’s not a good idea to write sensitive information like a personal access token.