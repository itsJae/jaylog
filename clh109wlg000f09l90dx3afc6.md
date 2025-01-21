---
title: "[CSS] CSS Combinator Selector - Explained with Examples"
seoTitle: "CSS Combinator Selectors with Examples and Explanation"
seoDescription: "Learn about combinator selectors, such as descendant, child, adjacent sibling and general sibling selectors. Easy-to-follow with examples and syntax."
datePublished: Fri Apr 28 2023 21:38:12 GMT+0000 (Coordinated Universal Time)
cuid: clh109wlg000f09l90dx3afc6
slug: css-css-combinator-selector-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682956053567/3216fb7a-76b6-41d8-a36b-7fc5e8cb8c0b.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682950247951/60adf369-72dd-4521-b14c-f17341690577.png
tags: css-selectors, programming-blogs, css, web-development, cssselector

---

---

### Introduction

Combinator selectors in CSS describe the relationship between selectors. CSS allows us to select more than one content for the styling, and it is done by using combinator selectors.

Combinator selectors are useful because it allows us to select the attribute that we want to give certain styles.

There are four types of combinator selectors

1. Descendant Selector (space)
    
2. Child Selector (&gt;)
    
3. Adjacent Sibling Selector (+)
    
4. General Sibling Selector (~)
    

---

### Descendant Selector (space)

Descendant Selector will select all the elements that come after the parent element.

### Syntax:

```css
parent child {
    /* write some codes for style */
}
```

This code means that the style will be applied to the &lt;p&gt; tags that have a &lt;div&gt; tag as their parent.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682715512512/369b2fd4-79ef-4372-a1d5-ae4212ccb5dc.png align="center")

### CSS Code Snippet:

```css
div p {
    /* write some codes for style */
}
```

### HTML Code Snippet:

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
      <p>Paragraph1</p>
      <p>Paragraph2</p>
      <span>
        <p>This p tag will also be affected.</p>
      </span>
    </div>

    <p>This will not be affected because it is not in the div.</p>
  </body>
```

---

### Child Selector (&gt;)

The difference between the child selector and the descendant selector:

* The child selector selects the elements that are an intermediate child.
    
* On the other hand, the descendant selector selects all the elements that are placed inside the parent tag.
    

### Syntax:

```css
parent > child {
    /* write some codes for style */
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682716132653/7f35e88b-bdab-4566-bb6b-1eed833de834.png align="center")

### CSS Code Snippet:

```css
div > p {
    /* write some codes for style */
}
```

### HTML Code Snippet:

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
      <p>Paragraph1</p>
      <p>Paragraph2</p>
      <span>
        <p>This will not be affected as it is not intermediate child of div tag.</p>
      </span>
    </div>

    <p>This will be affected.</p>
  </body>
</html>
```

---

### Adjacent Sibling Selector (+)

This selector allows you to select the element that is placed adjacent to a certain element. In other words, this selector selects the element that is placed next to the specified tag.

### Syntax:

```css
element + element {
    /* write some codes for style */
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682716793333/41435406-6456-4e0f-a141-651a747318a4.png align="center")

Let's look at some codes for a better understanding

### CSS Code Snippet:

```css
p + p {
    /* write some codes for style */
}
```

### HTML Code Snippet:

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
    <h1> Adjacent sibling selector (+) property</h1>  
    <p> It is the first paragraph </p>  
    <p> It is the second paragraph which is immediately next to the first paragraph, and it gets selected. </p>  
    <div> This is the div element </div>  
    <p> This is the third paragraph which does not get affected </p>  
    <p> This paragraph is also selected because it immediately next to third paragraph </p>  
    </body> 
</html>
```

---

### General Sibling Selector (~)

It selects the elements that follow the elements of the first selector, and both of them are children of the same parent.

When to use it?

* It is useful when we have to select the siblings of an element even if they are not adjacent directly.
    
* When you want to select the elements that share the same parent.
    

### Syntax:

```css
element ~ element {
    /* write some codes for style */
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1682717127116/3e0e934a-ec9b-4351-a417-b8dbed4a70f7.png align="center")

### CSS Code Snippet:

```css
h1 ~ p {
    /* write some codes for style */
}
```

### HTML Code Snippet:

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      div p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>General sibling selector (~) property</h1>
    <p>It is the first paragraph element which will get effected.</p>
    <div>
      <p>This is not effected because it is under div tag.</p>
    </div>
    <p>It is the paragraph element after the div, and it will be affected.</p>
    <p>It is the paragraph element which will also get affected.</p>
  </body>
</html>
```

---

### Conclusion

We can select different elements by using some special characters, such as (&gt;), (+) and (~). These are called combinator selectors, and they allow us to select the elements that we want.