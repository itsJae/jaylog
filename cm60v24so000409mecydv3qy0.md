---
title: "[Python] A Guide to Method Overloading Using Multipledispatch"
seoTitle: "[Python] A Guide to Method Overloading Using Multipledispatch"
seoDescription: "This article introduces multipledispatch package that you can use to enhance readability of your code. It also helps you to easily maintain your code. If yo"
datePublished: Fri Jan 17 2025 14:34:31 GMT+0000 (Coordinated Universal Time)
cuid: cm60v24so000409mecydv3qy0
slug: python-a-guide-to-method-overloading-using-multipledispatch
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1737123318282/606e1752-2aef-4544-929f-bec3c46ba44e.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1737124125454/b87be5c3-1b63-4d08-bcf5-077413df738b.jpeg
tags: oop, python, classes, object-oriented-programming, method-overloading, multipledispatch, multiple-dispatch

---

---

## Introduction

This article introduces multipledispatch package that you can use to enhance readability of your code. It also helps you to easily maintain your code. If you have never used it before and you often use method overloading, this post is really gonna help you.

Multipledispatch allows functions to dynamically dispatched pased on the ***types*** of their arguments. The “types”. This is another reason of why we should use multipledispatch when we do a method overloading. You may have experienced or felt that you always have to validate users’ input or arguments passed to a function. Otherwise, it will cause an error.

For example:

```python
class SampleA():
    def add(self, datatype, *args):
        if datatype == 'int':
            return sum(args)
        
        if datatype == 'str':
            return ''.join([x for x in args])

a = SampleA()

print(a.add('int', 5, 6))
print(a.add('str', 'Hi', 'Python'))
```

We should write a code like that!

---

## MultipleDispatch Installation Guide

In your terminal, type:

```python
pip install multipledispatch
```

Then, check if the multipledispatch is successfully installed:

```python
pip list
```

If you can find multipledispatch in the pip list, you are good to go!

---

## Using MultipleDispatch

```python
from multipledispatch import dispatch

class SampleB():
    @dispatch(int, int)
    def product(x, y):
        return x * y

    @dispatch(int, int, int)
    def product(x, y, z):
        return x * y * z

    @dispatch(float, float, float)
    def product(x, y, z):
        return x * y * z

b = SampleB()

print(b.product(5, 10))
print(b.product(5, 10, 10))
print(b.product(2.5, 5.5, 10.9))
```

@dispatch(type) is the part that I am using multipledispatch. You can declare the types of your function’s arguments, and then, fill in the corresponding arguments. That’s it!

This is so powerful because the multipledispatch package understands if the given argument is a float type, or int type, whatever that is, it will use the right function even though functions share the same name.