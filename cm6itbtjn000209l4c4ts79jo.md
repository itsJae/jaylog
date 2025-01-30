---
title: "[Python] Global Interpreter Lock (GIL)"
seoTitle: "[Python] Global Interpreter Lock (GIL)"
seoDescription: "GIL

GIL ensure that only one thread executes Python bytecode at a time, which means it prevents multiple threads from executing Python code concurrently."
datePublished: Thu Jan 30 2025 04:05:55 GMT+0000 (Coordinated Universal Time)
cuid: cm6itbtjn000209l4c4ts79jo
slug: python-gil
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738207900893/9cafcd32-1647-47f0-87dc-207fbb5b865e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1738209922493/ed922d06-8c79-4a6b-906a-a519cd2381e9.png
tags: python, cpython, gil, global-interpreter-lock

---

---

## GIL

> GIL ensure that only one thread executes Python bytecode at a time, which means it prevents multiple threads from executing Python code concurrently.

GIL works like this:

![Python]GIL 너는 대체 머냐?](https://blog.kakaocdn.net/dn/GuLai/btsGFDWfc7e/GClgmUrJA7wbP5ykk6T4FK/img.png align="left")

There are three threads, but they are not running concurrently. One needs to ***release*** in order for other threads to ***acquire***.

So, simply GIL is a limitation. However, you don’t have to worry because python is fast enough even though only one thread executes at a time.

---

## Purpose of Using it

Using GIL in CPython is to solve problems that arise when managing memories. Python manages memories by a reference counting method. Every object in Python has an associated reference count. This count tracks how many references (variables, function arguments, etc.) point to the object. When the count becomes 0, Python automatically deallocates the object and free the memory.

> If multiple threads modify referecne count at the same time, it may result in a race condition.

That’s why GIL is used. CPython locks the interpreter globally, so that one thread executes at a time.

---

## If You Don’t Want GIL

You can do a multiprocessing or use Jython and PyPy.