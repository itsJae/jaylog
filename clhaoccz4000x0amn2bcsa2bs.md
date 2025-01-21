---
title: "[JavaScript] Simple Rock Paper Scissors Game - Beginner Friendly"
seoTitle: "Simple Rock Paper Scissors Game - Beginner Friendly"
seoDescription: "Build a mini rock paper scissors game in 5 minutes!"
datePublished: Fri May 05 2023 14:51:34 GMT+0000 (Coordinated Universal Time)
cuid: clhaoccz4000x0amn2bcsa2bs
slug: javascript-simple-rock-paper-scissors-game-beginner-friendly
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683298532208/43c7200a-33fd-411b-8e6f-7b8a4ea8d031.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683298547892/159faa94-ab3f-42d5-a834-6b684860bb85.png
tags: programming-blogs, javascript, web-development, beginners, rock-paper-scissors

---

---

### Introduction

To build a rock paper scissors game, you need to use Math.random() method to randomly generate rock, scissors and paper.

In this mini-build, we will use HTML to allow users to choose their option and print out the result if they won against the computer.

---

### getRandomInt() Function

```javascript
function getRandomInt(min, max) {
    return Math.floor(Math.random() * (max - min + 1) - min);
}
```

This function generates a random number between min and max values.

For example, getRandomInt(1, 10) will give a random number between 1 and 10.

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <button onclick="rspGame('rock');">rock</button>
    <button onclick="rspGame('paper');">paper</button>
    <button onclick="rspGame('scissors');">scissors</button>
  </head>
  <body>
    <script>
        function rspGame(userInput) {
            computerRsp = ["rock", "paper", "scissors"];
            computerOutput = computerRsp[getRandomInt(0, 2)]

            userWinValue = {
                rock: "scissors",
                paper: "rock",
                scissors: "paper"
            };
            
            console.log("User Side:", userInput);
            console.log("Computer Side:", computerOuput);
            return userWinValue[userInput] === computerOutput
            ? "User Wins!" 
            : userInput = comptuerOutput
            ? "Draw!"
            : "Computer Wins!";
        }

        function getRandomInt(min, max) {
            return Math.floor(Math.random() * (max - min + 1) - min);
        }
    </script>
  </body>
</html>
```

The portion below lets the user makes their choice.

If a click on the button is detected, the computer generates its output (one of rock, paper, scissors), then prints out the results.

```xml
    <button onclick="rspGame('rock');">rock</button>
    <button onclick="rspGame('paper');">paper</button>
    <button onclick="rspGame('scissors');">scissors</button>
```