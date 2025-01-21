---
title: "[Python] How Closures and Decorators in Python Work Together to Simplify Code"
seoTitle: "[Python] How Closures and Decorators in Python Work Together to Simpli"
seoDescription: "A closure is created when a function (the inner function) is defined within another function (the outer function) and the inner function references variable"
datePublished: Thu Dec 19 2024 14:53:55 GMT+0000 (Coordinated Universal Time)
cuid: cm4vfzdsn000808l79jv87l2k
slug: closures-and-decoators
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1734617163779/1c4e85ae-37c8-42fe-9022-46dc16987a2b.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1734620023429/bd499a55-099a-4f8b-8f1f-62e2abf6378e.png
tags: closure, python, scope, decorators, python-advanced

---

---

## What Is Closure?

A closure is created when a function (the inner function) is defined within another function (the outer function) and the inner function references variables from the outer function.

```python
def func1():
    a = []
    def func2(v):
        a.append(v)
        return sum(a) / len(a)
    return func2

f = func1
f(10)
```

It looks simple, but seems weired as well. You may wonder how `func2` refers to `a` even though `func1` is completely finished after returning `func2`? `func2` should be excuted after `func1` returns `func2`, right?

Let’s see what happens when we call f(10).

1. `a` is declared in the outer function’s scope
    
2. `func2` is declared
    
3. `func1` returns `func2`. Now func1 is closed.
    
4. Since `func1` returns `func2`, `f = func1` is the same as `f = func2()`
    
5. `f(10)` means `func2(10)`, but we are trying to refer to `a`, which is the variable of outer function (and outer function is closed already). However, the program runs without any errors. It’s because `func1` **uses a closure**
    

Characteristics of a closure:

1. A function is a inner function of an otuer function.
    
2. The inner function refers to the variable in the outer function’s scope.
    
3. The outer function returns the inner function.
    

---

## Free Variable

You must understand what is a free variable as it is related to decorators and closures. It is a variable that is used within a function but is not defined inside the function or passed as a parameter. Instead, it refers to a variable that exists in the surrounding scope, such as a global or nonlocal scope. Simply, it is the variable declared in the outer function’s scope.

Example:

```python
def func1():
    # Free variables
    a = []
    b = {}
    def func2():
        return
    return
```

---

## Deep Dive into Closure

```python
def closure_ex():
    # Free variable
    series = []

    def averager(v):
        series.append(v)
        print(f'inner >>> {series} / {len(series)}')
        return sum(series) / len(series)
    return averager

avg_closure = closure_ex()

avg_closure1(10)
avg_closure1(40)

print(avg_closure.__code__.co_freevars) # ('series',)
print(avg_closure.__closure__[0].cell_contents) # [10, 40]
```

We can check free variables with `.__code__.co_freevars`

We can also check the contents with `.__closure__[0].cell_contents`

### **Advantages of using closure:**

1. **Encapsulation of State**
    

* Closures allow you to encapsulate state within a function, so you can hide variables and data from the outside world. This makes it easier to manage and protect data while still providing controlled access through the closure.
    

---

2. **Data Hiding**
    

* With closures, you can create private variables that are not directly accessible from outside the function. This mimics the concept of private variables in object-oriented programming.
    

---

3. **Improved Code Reusability**
    

* Closures enable writing more reusable and modular code. You can define a function once and generate customized versions of it with different parameters, making the code more flexible and reducing redundancy.
    

---

4. **Memory Efficiency**
    

* Since closures can capture the environment and maintain state without creating additional objects or storing state globally, they can be memory efficient in certain use cases.
    

---

## Decorator

A **decorator** is a design pattern that allows you to modify or enhance the behavior of functions or methods without changing their actual code. This allows us not to waste time and memory. Simply, decoratr “decorates” our functions, adding extra things.

Example (Timing function execution):

```python
def performance_clock(func):
    def performance_clocked(*args):
        start_time = time.perf_counter()
        result = func(*args)
        end_time = time.perf_counter() - start_time
        name = func.__name__
        arg_str = ', '.join(repr(arg) for arg in args)
        print('[%0.5fs] %s(%s) -> %r' % (end_time, name, arg_str, result))        

        return result

    return performance_clocked

@performance_clock
def time_func(seconds):
    time.sleep(seconds)

@performance_clock
def sum_func(*numbers):
    return sum(numbers)

time_func(1.5) # [1.50155s] time_func(1.5) -> None
sum_func(1, 2, 3, 4, 5) # [0.00000s] sum_func(1, 2, 3, 4, 5) -> 15
```

`@performance_clock` ← this part is a decorator. We can apply a decorator syntax with using `@` symbol.

How it works:

1. `time_func(1.5)` uses a `performance_clock` decorator.
    
2. `performance_clock` receives `time_func` as an argument. Therefore, `performance_clock(time_func)`.
    
3. `performance_clock` returns `performance_clocked`.
    
4. `performance_clocked` receives 1.5 as an argument.
    
5. Then, things inside print will be printed.
    
6. Then, it wil return the the `result`.
    

Without the decorator, if you call `time_func(1.5)`, nothing really happens. Just function will be finished after a few seconds that is assigned to the argument.