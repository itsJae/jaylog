---
title: "[Python] How to Create Immutable Dictionaries & Sets in Python?"
seoTitle: "[Python] How to Create Immutable Dictionaries & Sets in Python?"
seoDescription: "You can make your dictionary as immutable by using MappingProxyType function in types module. You are making your dictionary as read-only."
datePublished: Sun Dec 15 2024 13:41:13 GMT+0000 (Coordinated Universal Time)
cuid: cm4pnmgne000409ldd6kn5yft
slug: python-how-to-create-immutable-dictionaries-sets-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1734267990871/88a30076-9e88-45a7-b68d-9a2a4fe32747.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1734270014666/f37afd07-e841-4a48-a182-18974b552ce7.png
tags: python, immutable, sets, dictionary, python-beginner

---

---

## What are Immutable Dictionaries & Sets?

Before reading this article, you should have an understanding of mutable and immutable types in python. You can look at my article that explains them pretty easy: [\[CS fundamentals\] Mutable vs. Immutable](https://jaylog.hashnode.dev/cs-fundamentals-mutable-vs-immutable).

Dictotionaries and sets are mutable as we can change values. For example:

```python
d = {'key1': 'value1'}
print(d) # {'key1': 'value1'}

d['key2'] = 'value2'
d.setdefault('key3', 'value3')
print(d) # {'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}

s = {'Apple', 'Orange', "Apple", "Orange", 'Kiwi'}
print(s) # {'Kiwi', 'Orange', 'Apple'}

s.add('Melon')
print(s) # {'Melon', 'Kiwi', 'Orange', 'Apple'}
```

As you may see, the values of `d` and `s` can be changed, which means they are mutable.

---

## Immutable Dictionaries and Sets

**Creating Immutable Dictionary:**

```python
from types import MappingProxyType

d = {'key1': 'value1'}

# Read-only
d_frozen = MappingProxyType(d)
print(d_frozen) # {'key1': 'value1'}

d_frozen['key2'] = 'value2' # error
```

> You can make your dictionary as immutable by using `MappingProxyType` function in types module.

You are making your dictionary as read-only, so that your co-workers cannot edit the sensitive data stored in your immutable dictionary.

If you try to assign a new key-value pair, it will print an error.

```plaintext
Traceback (most recent call last):
  File "your_file", line 14, in <module>
    d_frozen['key2'] = 'value2'
TypeError: 'mappingproxy' object does not support item assignment
```

---

**Creating Immutable Set:**

```python
s = frozenset(['Apple', 'Orange', "Apple", "Orange", 'Kiwi'])
s.add('Melon') # error
```

It’s very simple. You can use `frozenset()` to make it immutable. Just like a dictionary, immutable set is also read-only, so that the data are not changed by someone.

If you try to modify it, it will print an error:

```plaintext
Traceback (most recent call last):
  File "your_file", line 29, in <module>
    s6.add('Melon')
AttributeError: 'frozenset' object has no attribute 'add'
```