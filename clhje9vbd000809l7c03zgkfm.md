---
title: "[HTML] Web Accessibility & Semantic HTML for the Screen Reader- Why You NEED to Consider."
seoTitle: "Web Accessibility & Semantic HTML for the Screen Reader"
seoDescription: "It is essential to understand the web accessibility, especially if you are a web developer."
datePublished: Thu May 11 2023 17:19:38 GMT+0000 (Coordinated Universal Time)
cuid: clhje9vbd000809l7c03zgkfm
slug: html-web-accessibility-semantic-html-for-the-screen-reader-why-you-need-to-consider
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683825439318/432891da-ffac-4b3a-9ac5-a8024b883903.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683825529574/e98533ea-bb8f-4de8-b9db-c0e8ed23c688.jpeg
tags: programming-blogs, web-development, accessibility, html5, web-accessibility

---

---

### Introduction

When you read news articles online, you might have noticed that those websites have screen readers. Not only the news article publishers, but you can easily see many websites have screen readers for the blind.

As a developer, it is important to write clean codes, make things work and solve problems. However, the end users must have enjoyable experiences with the products.

If you want your website to be accessible to as many as possible, you need to know about Web Accessibility, which will be covered in this article.

Web Accessibility refers to making your HTML code as semantic as possible. It is always a good practice to write semantic HTML rather than non-semantic tags, such as `<div>` or `<span>.`

Moreover, this article introduces some key things you need to take note of when you write your HTML code.

---

### Semantic HTML

Semantic HTML refers to tags that have meanings themselves. For example, &lt;strong&gt;, &lt;em&gt; and &lt;abbr&gt;.

A property can also help the screen reader to convey the website's content to the blind. For example, alt property in &lt;img&gt; tag.

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
    <p style="font-weight: bold">Bolded words</p>
    <p><b>Bolded</b>words</p>
    <p><strong>Bolded</strong>words</p>

    <p style="font-style: italic">Italcized words</p>
    <i>Italicized words</i>
    <p><em>Italcized words</em></p>

    <img src="./path" alt="Description about the image">
 </body>
</html>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683820931851/51484147-0333-4f0a-83ab-d839bb42f559.png align="center")

They look the same, but as a developer, you always need to think about why there are several ways of doing the same task. Giving style or using &lt;b&gt; tag only makes the texts bolded. However, &lt;strong&gt; makes the screen reader read the bolded text with stronger accents.

Same for &lt;em&gt; tag. Giving style or using &lt;i&gt; tag only italicized texts. This means that the screen reader will not be able to address the meaning to the users correctly. Using &lt;em&gt; tag will let the screen reader understand that you want to emphasize a certain part.

Alt property can be used to describe the image. It allows the screen reader to read and describe the image to the user who might not be able to see the screen. Additionally, please use double quotation ("") when you put a property in HTML tag. If this is not done properly, some information can be ignored.

### Things You Can Consider for Web Accessibility

---

### Specifying Character Set

Specifying character set refers to this:

```xml
<meta charset="UTF-8" />
```

UTF-8 is an encoding system for Unicode. Basically, using UTF-8 is safe because it can translate any character into Unicode.

If you do not specify it, the browser will automatically set it randomly. If the character set is wrongly set, some characters on your website are not shown to the user. This means that the screen reader cannot read it.

---

### Matching the for Value with Id Value.

It is a good practice to match the value of the for property with the value of the id property. What I mean is:

```xml
<lable for="userID">User ID</label>
<input type="text" id="userID" />
```

If you match the values of those two properties, the screen reader can tell the user that the input box requires a user id as input.

Imagine if you don't. Users who cannot see the screen will not be able to know if the field requires their email, phone number or address.

---

### Using RGB Code for Color Styles

This might be relevant to CSS, but you can still give styles by writing a style property in your HTML tag.

Using RGB code is needed because it is helpful for people with color blindness.

You can read the web guidelines about color blindness if you want to find out more.

---

### Self-closing Elements

When you write self-closing elements, you can add a slash(/) before the closing bracket.

What I mean is:

```xml
<input type="text" />
<br />
```

There is not syntax error although you take out the slash(/), but it is a good practice to always include them for a better web accessibility.

---

### Indentation

You always want to make your code more readable. But the reason for doing it is not only for co-workers but for the screen reader as well.

---

If you liked this article, or if this was helpful, please hit the like button :)