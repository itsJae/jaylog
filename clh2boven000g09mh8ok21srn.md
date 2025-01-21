---
title: "[CSS] Media Query for the Responsive Webs - Explained with Examples"
seoTitle: "What Is Media Query in CSS and Its Importance."
seoDescription: "Learn about media query and how webpages adapt to the user's device!"
datePublished: Sat Apr 29 2023 18:35:14 GMT+0000 (Coordinated Universal Time)
cuid: clh2boven000g09mh8ok21srn
slug: css-media-query-for-the-responsive-webs-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682950624029/2cd171c0-2152-40e9-8337-f6fbe2038626.png
tags: media-queries, programming-blogs, css, frontend-development, responsive-web-design

---

---

### 🔎Introduction

There are many different models of technology, such as the Samsung mobile phone vs. the iPhone. They both have their own distinct design and screen sizes.

To develop a good website that is accessible to as many people as possible, your website needs to be able to adapt to the user's device.

Then, the first thing that comes to our mind is how websites adapt to users' devices.

In CSS, we can use something called media query to set a condition such as when the user's screen size is less than 750px, change the layout.

---

### Importance of Media Query

Media query allows you to create different layouts depending on the size of the viewpoint.

---

### Syntax:

```css
@media screen and (width: ___px) {
    element {
        /* any codes written here will be excuted when the user's screen has                   a width of ___px. */
    }
}
```

If you want to use a media query, start by writing @ symbol and followed by media.

Then, usually followed by screen and (width).

However, people use different models of mobile phones, such as the iPhone 14 and iPhone 14 Max.

Instead of using width: \_\_\_px, you can use max-width or min-width.

### Syntax:

```css
/* max-width */
@media screen and (max-width: ___px) {
    element {
        /* any codes written here will be excuted when the user's screen size is less than ___px. */        
    }
}

/* min-width */
@media screen and (min-width: ___px) {
    element {
        /* any codes written here will be excuted when the user's screen size is greater than ___px. */        
    }
}
```

Screen refers to the user's screen.

```css
@media screen and (max-width: ___px)
```

This statement means that I will use the media query when the user's screen is less than \_\_\_px.

---

### Example:

```css
.row {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
}

@media screen and (max-width: 768px) {
    .row,
    .navbar {
        flex-direction: column;
    }
}
```

Additional note:

* flex-direction: colum will set my nav organized in a column.
    
* .row class makes sure that the contents are stored inside the container. I used flex-wrap: wrap to do so.
    
* If I do not do flex-wrap: wrap, this will happen:
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682792618762/3df141f0-3320-44e0-a5ac-d8885fad82fc.png align="center")

---

### Actual Implementation

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682792897355/8d64e1d2-e6e4-49e2-a3f3-e3706583d09e.png align="center")

This screen is about 800px, which is not less than what I set as max-width (768px). So, this screen is for PC users.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682793014440/631aafda-5489-41c2-a1f5-ff231510c3dd.png align="center")

We can see the difference here as the navigation is organized in a column as I wrote flex-direction: column.

---

### This happened because....

```css
@media screen and (max-width: 768px) {
    .row,
    .navbar {
        flex-direction: column;
    }
}
```

The screen is now less than 768px, so the website applies flex-direction: column.