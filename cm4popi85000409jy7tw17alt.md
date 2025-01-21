---
title: "[CS Fundamentals] Deep Dive into Shallow Copy vs. Deep Copy. Explained in Python"
seoTitle: "[CS Fundamentals] Deep Dive into Shallow Copy vs. Deep Copy. Explained"
datePublished: Sun Dec 15 2024 14:11:34 GMT+0000 (Coordinated Universal Time)
cuid: cm4popi85000409jy7tw17alt
slug: cs-fundamentals-deep-dive-into-shallow-copy-vs-deep-copy-explained-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1734270232805/3462cff3-c312-44e0-9fbc-b2fceed24b98.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1734270240681/19759497-acb4-4071-bd37-1e7b342c8e96.png
tags: python, computer-science, fundamentals, cs, shallowcopy, deepcopy

---

---

## Introduction

Before going in, you should know the difference between mutable and immutable types in python. You can have a look at my article: [\[CS Fundamentals\] Mutable vs. Immutable](https://jaylog.hashnode.dev/cs-fundamentals-mutable-vs-immutable).

You don’t need to care about shallow copy and deep copy for immutable objects, such as int, float, str, etc. Let’s have a look at this example:

```python
a = 10
b = a

print(id(a)) # 139774137238944
print(id(b)) # 139774137238944

print(a is b) # True
```

So, their ids are the same, but now look at this one:

```python
a = 10
b = a

a += 5

print(id(a)) # 139774137239104
print(id(b)) # 139774137238944

print(a is b) # False
```

Once the value of `a` is changed, their ids are not the same, which means they are **independent**.

> Therefore, we do not need to care about immutable types, as they will be independent when the value is changed.

This means that mutable types are not independent sometimes. Now, let’s move forward to **shallow copy vs deep copy.**

---

## Shallow Copy

```python
import copy

c_list = [1, 2, 3, [4, 5, 6], [7, 8, 9]]
d_list = copy.copy(c_list) # shallow copying c_list

print(id(c_list) == id(d_list))
print(c_list)
print(d_list)

d_list[1] = 100
```

Output:

```plaintext
False
[1, 2, 3, [4, 5, 6], [7, 8, 9]]
[1, 100, 3, [4, 5, 6], [7, 8, 9]]
```

As we did a shallow copy, two lists are independent. The second element of `d_list` is now `100`. However, we cannot say they are completely independent each other.

Let’s have a look at this example:

```python
# Extra codes
d_list[3].append(1000)
d_list[4][1] = 10000

print(c_list)
print(d_list)
```

Output:

```plaintext
[1, 2, 3, [4, 5, 6, 1000], [7, 10000, 9]]
[1, 100, 3, [4, 5, 6, 1000], [7, 10000, 9]]
```

Do you notice that the values are added to both lists? This is the characteristic of shallow copying. It cannot go deeply.

---

## Deep Copy

Using deep copy, we are able to make two lists completely independent.

```python
import copy

e_list = [1, 2, 3, [4, 5, 6], [7, 8, 9]]
f_list = copy.deepcopy(e_list) # deep copying e_list

f_list[1] = 100
f_list[3].append(1000)
f_list[4][1] = 10000

print(e_list)
print(f_list)
```

Output:

```plaintext
[1, 2, 3, [4, 5, 6], [7, 8, 9]]
[1, 100, 3, [4, 5, 6, 1000], [7, 10000, 9]]
```

---

## Conclusion

![Understanding the Difference Between Shallow Copy, Deep Copy, and  References in Python](https://media.licdn.com/dms/image/v2/D4D12AQEhCOPPI1VqsQ/article-inline_image-shrink_1000_1488/article-inline_image-shrink_1000_1488/0/1697709447743?e=1739404800&v=beta&t=CzyXwEHDPMI8HNnxtNsdwdkL7IJlxaomdRF6p7xj__I align="left")

Shallow copy and deep copy are very important and fundamental concept in computer science. It is essential to understand the difference of both to prevent the error. Imagine not knowing the difference .You will not even be able to know why an array is affected by another array. It can cause side-effects on your code.

It’s also important to keep in mind that every variable will point to some location when it is declared. It’s great if you are able to draw a picture of memory space!