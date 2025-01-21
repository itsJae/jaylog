---
title: "[Python] Magic Method"
seoTitle: "[Python] Magic Method"
seoDescription: "Magic methods, also known as dunder methods (short for "double underscore"), are special methods in Python that start and end with double underscores."
datePublished: Sun Dec 15 2024 05:39:13 GMT+0000 (Coordinated Universal Time)
cuid: cm4p6emga000a09la83d9f7il
slug: python-magic-method
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1734239194746/f3ad070d-3933-4444-af8e-10c9178fde4e.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1734241138325/11c7cb91-3cca-46e6-ae22-b6126eef1f43.jpeg
tags: programming-blogs, python, methods, python-beginner, python-magic-method

---

---

## What is a magic method?

Magic methods, also known as dunder methods (short for "double underscore"), are special methods in Python that start and end with double underscores. They automatically invoked by python to perform specific operations.

Example:

* \_\_init\_\_
    
* \_\_add\_\_
    
* \_\_str\_\_
    
* \_\_repr\_\_
    

---

## Why is it important?

We can get the calculation result of `1 + 1` by using `+` operand in python, but have you ever thought of how `1 + 1` (or any other calucations) is interpreted by python? Let’s have a look at this code:

```python
a = 1
print(type(a)) # <class 'int'>
```

We assign `1` to `a`, so `a` is an integer. `type(a)` tells us that the type of a is ‘`int`’, but you need to have a look at ‘class’. `int` is a class. As `int` is a class, `float` and `str` are also classes.

Let’s check the attributes and methods that we can use! The `dir()` function in Python is used to list the attributes and methods of an object. It returns all properties and methods of the specified object, without the values.

```python
a = 1
print(type(a)) # <class 'int'>
print(dir(a))
```

Result of `print(dir(a))`:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1734239997197/b99ffa29-d477-4f4a-a3ef-1f80b92b9516.png align="center")

The second element of the list is `‘__add__’`. Now, let me show you using a magic method.

```python
a = 10
print(a + 10) # 20
print(a.__add__(10)) # 20
```

The result of using `+` operand and using the `__add__` are the same. I am not gonna lie, `+` operand is way easier to understand and more readable. Then, why does python have so many magic methods? It’s because it allows us to customize the method. `+` operand only allows us to add two numbers, which is **not** fun and flexible.

---

## Powerfulness of Magic Method

I am going to introduce you some examples to show you how powerful magic methods are.

Example:

```python
class Fruit():
    def __init__(self, name, price):
        self._name = name
        self._price = price

    def __str__(self):
        return f'Fruit Class Info: {self._name}, {self._price}'

    def __add__(self, x):
        print('Called >> __add__')
        return (self._price + x._price) * 0.8

s1 = Fruit('Orange', 7500)
s2 = Fruit('Banana', 3000)

# Not using magic method
print(s1._price + s2._price)

# Using magic method
print(s1 + s2)
```

Notice that I did `(self._price + x._price) * 0.8`. I am not just adding two values, but also multiplying it by 0.8. Let’s say you are the owner of a fruit store, and you want to set the sales percentage differently every month. Then, you can just addit `__add__` magic method in your `Fruit()` class. How powerful!