---
title: "[CS Fundamentals] Binary Search"
seoTitle: "[CS Fundamentals] Binary Search"
seoDescription: "Binary Search is a powerful algorithm to search for a certain value. If you were to find 3 in an array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9], how are you going t"
datePublished: Mon May 19 2025 15:06:40 GMT+0000 (Coordinated Universal Time)
cuid: cmav7xefu000e09jrftpia5fz
slug: cs-fundamentals-binary-search
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1747041878054/c8d8adb9-097d-484b-9562-f43e4bce9a46.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1747043094611/94c0c82b-6e75-4577-9fd2-522412fa9c5d.png
tags: algorithms, python, binary-search-algorithm, bisect

---

---

## Idea

Binary Search is a powerful algorithm to search for a certain value. If you were to find 3 in an `array = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`, how are you going to come up with the index of `3`? The first method that pops up in your head would be looking at each value starting from index 0 to the end, and see if there are any matching values. However, this method is inefficient if you have a large amount of data.

We can use binary search to make it more efficient. In binary search, we set `left`, `right` and `mid`. If a value of mid index is greater than the target value, we divide an array with mid becoming the left.

For example, our target is `3`, and `mid` is `4`. In `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`, `arr[4] = 4`, so it is greater than the target, so we only look at the left side of the array like this: `[0, 1, 2, 3]`. If the target was `7`, the target is greater than `arr[mid]`, so we look at the right side of the array like this: `[5, 6, 7, 8, 9]` ***becasue it is guaranteed that the target is not on the other half.***

---

## Code

Using Recursion:

```python
def binary_search(arr, target, left, right):
    if left > right:
        return None
    mid = (left + right) // 2
    
    if array[mid] == target:
        return mid
    elif array[mid] > target:
        return binary_search(arr, target, left, right - 1)
    else:
        return binary_search(arr, target, left + 1, right)
```

Using While Loop:

```python
def binary_search(arr, target, left, right):
    while left <= right:
        mid = (left + right) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] > target:
            right = mid - 1
        else:
            left = mid + 1
    return None
```

---

## Python Bisect Library

Bisect is a python library that helps you to easily do a binary search with a single line of code. You can implement binary search with the code above, but you can save your time with bisect.

bisect\_left(literable, value): returns the left-most element that can be insrted while keeping the list sorted.

bisect\_right(literable, value): returns the right-most element that can be insrted while keeping the list sorted.

To help you understand, I have a picutre below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1747042235984/70787bfa-fc39-4f0b-b3c2-03b235b33bed.png align="center")

```python
from bisect import bisect_left, bisect_right

a = [1, 2, 4, 4, 8]
x = 4

print(bisect_left(a, x)) # 2
print(bisect_right(a, x)) # 4
```

Using bisect, we can calculate the number of elements on a certain boundary.

```python
from bisect import bisect_left, bisect_right

def count_by_range(a, left, right):
    right_idx = bisect_right(a, right)
    left_idx = bisect_left(a, left)
    return right_idx - left_idx

a = [1, 2, 3, 3, 3, 3, 4, 4, 8, 9]

# returns the number of 4 in list
print(count_by_range(a, 4, 4)) # 2

# returns the number of elements in a range of -1 to 3.
print(count_by_range(a, -1, 3)) # 6
```