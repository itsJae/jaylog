---
title: "[DBMS] Analyzing Netflix's Database - With ERD"
seoTitle: "[DBMS] Analyzing Netflix's Database"
seoDescription: "Netflix provides a streaming service that offers a wide variety of TV shows and movies. I will share my analysis of the database of Netflix."
datePublished: Tue May 16 2023 00:00:42 GMT+0000 (Coordinated Universal Time)
cuid: clhpid1u406sel7nvdpzy18ux
slug: dbms-analyzing-netflixs-database-with-erd
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684136437348/11ee32aa-7885-4b9a-9491-0079fc423295.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684137025070/9fe55cc9-65d3-40d7-9e70-96205ba9d9f1.webp
tags: programming-blogs, web-development, netflix, dbms, rdbms

---

---

## Introduction

Netflix is one of the Big Tech companies that provides a streaming service that offers a wide variety of TV shows, movies, anime, documentaries, and more on thousands of internet-connected.

Netflix is available across many countries, and they offer different movies/shows to each country. It is important to take note of that they offer limited TV shows for some countries. For example, some Korean Dramas are only available in South Korea.

In this article, I will share my analysis of how their database would be structured. I will analyze their pages, such as:

![How I Bypassed Netflix Profile Lock? | by Krishnadev P Melevila | InfoSec  Write-ups](https://miro.medium.com/v2/resize:fit:1108/1*VnQT2u8hIPRuMfcqJZ6Uog.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684158177921/97f01b1a-14c8-47a7-99eb-fc4aef720fa2.jpeg align="center")

I am a freshman at university, not a professional software engineer, so there could be a misinterpretation. It is my pleasure if you can leave some comments on how you would alter what I have done or which part I can make improvements.

---

## Initial Thought Process

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684137936003/4277ff58-77b7-4306-b958-1bd615c454e0.png align="left")

This is the brainstorming I have done. The first table to be created is the Film. Under the film, there are season table, episode table, trailers & teasers table, similar movies, etc. So, the foreign keys could be EPISODE\_ID, LANG\_ID, COUNTRY\_ID, SEASON\_ID, GENRE\_ID, etc.

One thing I noticed at the brainstorming stage is that Big Tech companies like Netflix would value users' activities, such as how much time they spent on using their app. So, you will be able to notice that I included attributes for user activities.

Other than that, afilm must have a brief storyline, and each episode must have a brief storyline as well. Each film and its episode would have thumbnails as well.

Moreover, the actress can be managed by two tables. Actor and Cast Members. Each actor would have movies that they have participated, so the Actor table would have a CAST\_MEMBER\_ID as a foreign key.

---

## Database Structure

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684158486771/e36c4860-0af3-491b-ab60-7e886634f8fe.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684158512310/e582e2d3-0981-42f7-9de4-3b408e52f0c4.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684158529651/e8bbf97b-1326-4de3-82bd-a47eae8ed938.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684158550775/4e972548-9bdf-41df-94f9-b23e89c16de3.png align="left")

---

## Entity Relationship Diagram (ERD)

I converted the tables into the ERD to show the relationship between each entity.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684164210132/94ca2c9d-da14-4aad-9a9d-eb1f742b8193.jpeg align="center")

Since Netflix would have many tables for their system, there are many entities, so the photo is a bit unclear to see. I am sorry about that.

---

## What I learned

I learned how companies store users' data in their database and use it to enhance the user experience. For example, RESULT\_EXISTS attribute in SearchResult table (right bottom corner) determines if the matching movie/TV show could be found. If you have used Netflix, you would encounter a situation where you cannot find a show. By analyzing the data in the RESULT\_EXISTS attribute, Netflix can decide if they need to release a new show. They would want to do that if a million of users have searched it, and were not able to find the show.

Moreover, there are two attributes of the SearchResult table, which are EPISODE\_CLICK\_DATE and EPLISODE\_EXIT\_DATE. These two attributes store the data of when the user clicked on a certain episode/film and when they exited by searching. This allows Netflix to know how much time the user has remained on a certain page.

Now I can see how companies would make business decisions by looking at the data of the user activities. Nowadays, it is called big data.

---

## Challenges

Netflix is used by people from different countries, hence, it has different a subscription price, available movie, language and policies. So, I had to create extra tables, such as country, subscriptionPrice, filmAvailableCountry, and filmLanguage.

It was challenging because I had never done anything like this before. However, it gave me a better idea of how services like Netflix would have such database structure. I can use this knowledge to create a better DB design for my next practice.

---

## Additionals

While I was thinking about how their structure would be like, I got curious about how Netflix stores all the videos and handles a huge amount of traffic. Especially, videos require a large storage amount, and Netflix has millions of videos that have a quite long running time. So, I did some research.

Here is what I found:

1. Distributed File System (DFS): Netflix likely employs a distributed file system, such as the Hadoop Distributed File System (HDFS) or a custom-built solution. These file systems allow large files (such as videos) to be divided into smaller chunks and distributed across multiple servers and nodes.
    
2. Content Distribution Network (CDN): You might have heard of this term. CDNs consist of geographically distributed servers strategically placed in data centers across different regions. How this works is.. when a user requests a video, the CDN identifies the closest servers around the user. This reduces latency and improves video streaming performance.
    
3. Caching: Caching refers to saving the frequently visited or watched videos, so that the user does not need to download it every time. Caching is also often used for websites. The browser will cache the website that you frequently visit. Caching can result in reducing the load on the database and improves streaming performance by serving content from local storage.