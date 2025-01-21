---
title: "[JavaScript] Understanding XMLHttpRequest"
seoTitle: "[JavaScript] Understanding XMLHttpRequest."
seoDescription: "GET, POST, PUT, DELETE methods to request the data and get the response back from the server."
datePublished: Sat May 06 2023 16:31:44 GMT+0000 (Coordinated Universal Time)
cuid: clhc7d0bl000109mk7b7hfdjd
slug: javascript-understanding-xmlhttprequest
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683385984685/e36d3b46-b6e4-4cd8-afc1-d0ba5fac1beb.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683390729380/cc887aa2-df5d-4da1-be66-90ba6f35097d.jpeg
tags: javascript, json, web-development, beginners, xmlhttprequest

---

---

### Introduction

This article will talk about:

1. GET to retrieve the data
    
2. POST to send the data.
    
3. PUT to replace the data.
    
4. DELETE to delete the data.
    

\*note. I am using the JSON-server in this article.

---

### GET Request

You can use the GET method to retrieve the data from the server.

```javascript
function getData(url) {
    return new Promise((resolve,reject)) => {
        const xhr = new XMLHttpRequest();
    
        xhr.open("GET", url);
        xhr.setRequestHeader("content-type", "application/json");
        xhr.send();

     xhr.onload = () => {
        // if xhr.status === 200, it means retrieving the data was                   successful.
        if (xhr.status === 200) {
            // The string type needs to be converted into JSON type.
            const res = JSON.parse(xhr.response); 
            resolve(res);
        } else {
            // prints the status code and status text if failed to retrieve the data.
            console.log(xhr.status, xhr.statusText)
            reject(xhr.status);
        };
    }
}

// prints out the corresponding data.
getData("http://localhost:3000/posts").then((res) => {
    console.log(res);
});
```

---

### POST

You can use the POST method to send the data to the server.

```javascript
function postData() {
    const xhr = new XMLHttpRequest();
    
    xhr.open("POST", "http://localhost:3000/posts");
    xhr.setRequestHeader("content-type", "application/json;charset=UTF-8");
    // specifies the send() because you are trying to send the data.
    xhr.send(JSON.stringify(data)); // converts JSON data type to String.

     xhr.onload = () => {
        // if xhr.status === 201, it means sending the data was                   successful.
        if (xhr.status === 201) {
            // The string type needs to be converted into JSON type.
            const res = JSON.parse(xhr.response); 
            console.log(res);
        } else {
            // prints the status code and status text if failed to retrieve the data.
            console.log(xhr.status, xhr.statusText);
        };
    }
}
```

---

### PUT

You can use the PUT method to replace the data.

```javascript
function postData() {
    const xhr = new XMLHttpRequest();
    
    // I put 2 at the back of the URL to specify that I want to replace the data with ID number = 2.
    xhr.open("PUT", "http://localhost:3000/posts/2");
    xhr.setRequestHeader("content-type", "application/json;charset=UTF-8");
    // The data you want to replace with.
    const data = { title: "HTML", author: "John Doe" };
    // specifies the send() because you are trying to send the data.
    xhr.send(JSON.stringify(data)); // converts JSON data type to String.

     xhr.onload = () => {
        // if xhr.status === 200, it means replacing the data was                   successful.
        if (xhr.status === 200) {
            // The string type needs to be converted into JSON type.
            const res = JSON.parse(xhr.response); 
            console.log(res);
        } else {
            // prints the status code and status text if failed to retrieve the data.
            console.log(xhr.status, xhr.statusText);
        };
    }
}
```

---

### DELETE

```javascript
function postData() {
    const xhr = new XMLHttpRequest();
    
    // I put 2 at the back of the URL to specify that I want to delete the data with ID number = 2.
    xhr.open("DELETE", "http://localhost:3000/posts/2");
    xhr.setRequestHeader("content-type", "application/json;charset=UTF-8");
    // The data you want to replace with.
    const data = { title: "HTML", author: "John Doe" };
    // specifies the send() because you are trying to send the data.
    xhr.send(JSON.stringify(data)); // converts JSON data type to String.

     xhr.onload = () => {
        // if xhr.status === 200, it means deleting the data was                   successful.
        if (xhr.status === 200) {
            // The string type needs to be converted into JSON type.
            const res = JSON.parse(xhr.response); 
            console.log(res);
        } else {
            // prints the status code and status text if failed to retrieve the data.
            console.log(xhr.status, xhr.statusText);
        };
    }
}
```