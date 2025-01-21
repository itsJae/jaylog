---
title: "[CSS] Overflow - Explained with Examples."
seoTitle: "CSS Overflow - Explained with Examples."
seoDescription: "CSS overflow is used when the size of the child element is larger than the parent element. Then, the overflow occurs because the content of the child elemen"
datePublished: Fri May 12 2023 14:05:53 GMT+0000 (Coordinated Universal Time)
cuid: clhkmskj2000109mkclgsd8g7
slug: css-overflow-explained-with-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683896885957/65595bab-855e-4505-8a99-6758f04b1374.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683896895286/fa833d37-feea-4787-8af0-f99d5c6b3340.png
tags: programming-blogs, css, web-development, overflow, css-basics

---

---

### What is CSS Overflow?

CSS overflow is used when the size of the child element is larger than the parent element. Then, the overflow occurs because the content of the child element is bigger.

For example:

```xml
<div style="height: 200px; width: 250px; border: 3px solid green;">
    <p>
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
    </p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
</div>
```

This code causes this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683897740274/735df719-23a1-4506-b0bb-bc064dd50aa6.png align="center")

To prevent this or make the contents to be in the green box, you need a property called "overflow".

Overflow can have six(4) values:

1. visible - Default. Overflow is not clipped.
    
2. auto - Overflow is clipped. Scroll bars are made where the contents are overflown.
    
3. scroll - Overflow is clipped. Scroll bars appear on both x and y-axis.
    
4. hidden - Overflow is clipped. The overflew contents are not visible.
    

---

### Overflow: visible

`Overflow: visible` is the default, which means the scroll bars will not appear.

HTML Code:

```xml
<div style="height: 200px; width: 250px; border: 3px solid green; overflow: visible;">
    <p>
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
    </p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
    <p>A</p>
</div>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683897740274/735df719-23a1-4506-b0bb-bc064dd50aa6.png align="center")

---

### Overflow: auto

In overflow: auto, the scroll bars appear for the axis where the content is overflown.

HTML Code:

```xml
<div style="height: 200px; width: 250px; border: 3px solid green; overflow: auto;">
      <p>AAAA</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
</div>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683899194810/bf9dd4be-4e27-4dcd-8260-6909f35d0dc6.png align="center")

Do you notice that the scroll bar is only at the y-axis because we have added so many `<p>` tags in the y-axis?

---

### Overflow: scroll

`Overflow: scroll` adds scroll bars on both x and y-axis regardless of how big or small the content size is. In the past, it was needed because of the browsers like internet explorer.

So, if you want to show the scroll bar every time, you can use `overflow: scroll`.

HTML Code:

```xml
<div style="height: 200px; width: 250px; border: 3px solid green; overflow: scroll;">
      <p>AAAA</p>
      <p>A</p>
      <p>A</p>
</div>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683899457049/e8ed1dc7-f5cc-4693-a88f-2924e6a129f4.png align="center")

You would notice that the scroll bars are there even though the texts are not still in the box.

---

### Overflow: hidden

`Overflow: hidden` only shows the content that is placed inside the parent element. The scroll bars are not generated.

HTML Code:

```xml
<div style="height: 200px; width: 250px; border: 3px solid green; overflow: hidden;">
      <p>
      AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
      </p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
      <p>A</p>
</div>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683899640433/1598abfb-5e53-45dd-aa41-14242e631688.png align="center")

As you can see, the scroll bars do not exist; however, the texts are not overflown. Only the texts in the green box are visible to the users.

\* Additional Note. If you want the text to be shown in a straight line (or a single line), you can add this style:

CSS Code:

```css
p {
    white-space: nowrap;
}
```

---

### Overflow-x and Overflow-y

Overflow-x and overflow-y are not so different from overflow property. They just allow you to select which axis you do not want the content to be overflown.

For overflow-x, it will prevent the overflow in the x-axis

For overflow-y, it will prevent the overflow in the y-axis.