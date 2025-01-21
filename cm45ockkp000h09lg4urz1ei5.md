---
title: "[CS Fundamentals] Mutable vs. Immutable"
seoTitle: "[CS fundamentals] Mutable vs. Immutable"
seoDescription: "This article introduces concepts of mutability and immutability in computer science."
datePublished: Sun Dec 01 2024 14:06:07 GMT+0000 (Coordinated Universal Time)
cuid: cm45ockkp000h09lg4urz1ei5
slug: cs-fundamentals-mutable-vs-immutable
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1733058704280/8c685ff5-68b7-44cf-947b-8d9b81f342b6.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1733061945459/a08b8e70-c6c8-4d7f-af22-f3abe3814ce6.webp
tags: python, immutable, immutability, mutable, types

---

---

## Introduction

This article introduces concepts of mutability and immutability in computer science. It’s very important to understand it because it’s going to help you to solve errors in the future. Especially, beginners often face situations such that program outputs unexpected results. After reading this article, you will have a sight of seeing which variable contains which value.

\* This article is based on python.

---

## Immutable vs. Mutable

An **immutable** value is one whose content cannot be changed without creating an entirely new value, in comparison with mutable variables.

Immutable types:

* int
    
* boolean
    
* float
    
* string
    
* tuple
    
* complex
    
* bytes
    

mutable types:

* list
    
* dictionary
    
* set
    

To understand the difference between immutability and mutability in python, you need to focus on two keywords, which are “change” and “id”. After value changes, if that variable holds the same id, it is mutable. If not, it is immutable.

Immutable Example:

```python
x = 1
y = x

y += 3

print(x, y) # 1, 4
print(id(x), id(y)) # 139812355671168 139812355671264 <- DIFFERNET ID
```

![](https://t1.daumcdn.net/cfile/tistory/276C134655A74C8E09 align="left")

We have x and y, and their types are integer. Integer is immutable, so they point to different id(memory). As I said, each points to different memory after the value of y is changed. Therefore, it is immutable.

```python
x = 1
y = x

y += 9999999999
y = 1

print(id(x), id(y)) # 139771559752832 139771559752832
```

The ids are the same once the values are the same.

---

Mutable Example:

```python
arr1 = [1, 2, 3]
arr2 = arr1

print(id(arr1)) # 140535011664432
print(id(arr2)) # 140535011664432
```

As you might expect, the id is the same. Now let’s have a look at this code:

```python
arr1 = [1, 2, 3]

print(id(arr1)) # 139698565288496
arr1[0] = 9

print(arr1) # [9, 2, 3]
print(id(arr1)) # 139698565288496
```

The id is the same even though the first index of `arr1` is changed to 9. So, we call list **mutable.** We can change the value!

---

## **What are the benefits of immutability?**

* **Safety and Predictability**: Immutable objects can't be modified accidentally, making the code more predictable and reducing bugs.
    
* **Hashing and Dictionary Keys**: Immutable objects can be used as dictionary keys or set elements because their value remains constant.
    
* **Easier Debugging**: Since immutable objects don’t change, it's easier to track their values and debug the code.
    
* **Functional Programming**: Immutability promotes pure functions (functions that don’t alter their inputs), which makes code easier to reason about and test.
    
* **Thread-Safety**: Immutable objects are inherently thread-safe, so you don’t need locks when multiple threads access them.
    
* **Cache-Friendly**: Since they can't change, immutable objects can be cached more efficiently.
    
* **Simplified State Management**: In applications with complex state management, immutability ensures that data remains consistent across changes.