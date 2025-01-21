---
title: "[CS Fundamentals] Demystifying Variable Scope: Best Practices and Common Pitfalls with Python"
seoTitle: "[CS Fundamentals] Demystifying Variable Scope with Python"
seoDescription: "In computer science, it is so important to fully understand a variable scope as you may face many errors without knowing how they work or your program print"
datePublished: Wed Dec 25 2024 14:31:00 GMT+0000 (Coordinated Universal Time)
cuid: cm53zt0gp000b0ala9xiv038h
slug: cs-fundamentals-demystifying-variable-scope-best-practices-and-common-pitfalls-with-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1735134225583/dc24f62a-d30c-47aa-b6de-aacb896ba7c0.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1735137034416/3add7c3f-a6f7-4a6a-90a5-01bda17cdf8b.jpeg
tags: variables, closure, python, computer-science, fundamentals, scope, local-scope, global-scope, unboundlocalerror

---

---

## **Introduction**

In computer science, it is so important to fully understand a variable scope as you may face many errors without knowing how they work or your program prints an unexpected output. This article will deeply explain about local, global variables, closure, and keywords used for variable scope handling in python.

---

## Local vs. Global

If a variable is assigned in the most outer, it is the gloabl variable, otherwise, it is local.

Example:

```python
a = 10 # global

def foo():
    b = 20 # local 
```

### Global

* Global variables are used for fixed values, such as pi. Pi is always going to be 3.14…..
    
* Accessing global variables in local is not recommended
    
    * For example, using `global` keyword.
        

### Local

* Local variables are declared in loop, function, etc.
    
* They are to solve a certain logic
    
* They no longer exists in the memory after function returns (or finishes)
    
    * But not in closure.
        

---

## Same Variable Name

```python
b = 20 # global variable

def bar():
    b = 30 # local variable
    print(b)

bar() # 30
print(b) # 20
```

In the example, we have two variables with one global and one local scope, and their names are the same. Now, think about why the output of `bar()` is `30`. It’s because python seeks for the local variable first. If there is no local variable, then python seeks for the global variable. Therefore, `30` is correct.

Now, think about why the output of `print(b)` is `20`. `print(b)` is written in the global scope, so python seeks for the global variable. If there is one, it prints the according value. If not, it outputs an error.

Declaring a local variable with the same name of a global variable is called ***variable shadowing.***

---

## UnboundLocalError

Think about the output of `foobar()`

```python
c = 40

def foobar():
    c = c + 10 
    print('Ex3 >', c)

foobar()
```

You may think that `foobar()` will print `50`;however, the output is `UnboundLocalError`.

```plaintext
Traceback (most recent call last):
  File "", line 44, in <module>
    foobar()
  File "", line 38, in foobar
    c = c + 10 # UnboundLocalError
UnboundLocalError: local variable 'c' referenced before assignment
```

> You **CANNOT** modify a global variable in local scope.

We are trying to access a variable that is not even declared. Remember that python will seek for local variable first. In the code above, we are printing `c`, so python finds `c` in the local scope, but it’s not declared, rather it is doing a caculation.

### Global Keyword

If you want to modify it, you can use `global` keyword:

```python
c = 40

def foobar():
    global c
    c = c + 10 
    print('Ex3 >', c)

foobar()
```

However, using `global` is not recommended as it is not good for code maintenace. It does not mean that `global` keyword is **wrong.** It can be used when needed.

---

### nonlocal Keyword

Before going into the `nonlocal` keyword, you must understand closure. You can have a look at my article: [\[Python\] How Closures and Decorators in Python Work Together to Simplify Code](https://jaylog.hashnode.dev/closures-and-decoators)

```python
def outer():
    e = 70
    def inner():
        e += 10
        print('Ex5 >', e)
    return inner

in_test = outer()
in_test()
```

```plaintext
Traceback (most recent call last):
  File "", line 69, in <module>
    in_test()
  File "", line 64, in inner
    e += 10
UnboundLocalError: local variable 'e' referenced before assignment
```

The error message tells us that `e+= 10` got some problems. `local variable ‘e’ referenced before assignment`, but it seems like we are using a variable that is already assigned a value. What’s wrong?

Just like I explained before, we are trying to access a variable that is not even declared. Remember that python will seek for local variable first.

We can use `nonlocal` keyword, not `global` this time because it is using ***closure***.

```python
def outer():
    e = 70
    def inner():
        nonlocal e
        e += 10
        print('Ex5 >', e)
    return inner

in_test = outer()
in_test() # 80
```

---

## locals() & globals()

### `locals()`

* ***Python locals()*** function returns the dictionary of the current local symbol table. We use it to access the local symbol table in ***Python.***
    

```python
def func(var):
    x = 10
    def printer():
        print('Ex6 >', "Printer Func Inner")
    print('Func Inner', locals())

func('Hi')
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735136127440/a12565d6-1015-4780-88ce-6978a1c87bd5.png align="center")

We can check local declarations easily 😊!

---

### `globals()`

* In Python, the globals() function is a built-in function that returns a dictionary representing the current global symbol table.
    

Example:

```python
print(globals())
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735135940856/7308deed-dfcb-459e-932c-50479843b152.png align="center")

It returns all the things that are declared in the global scope. Not just variables only, but functions are also there.

As you may see, they are in the dictionary. Which means, a variable is created like this:

```python
test_variable = 100
globals()['test_variable'] = 100
```

The two lines mean the same thing. We can do something more fun:

```python
for i in range(1, 10):
    for k in range(1, 10):
        globals()[f'plus_{i}_{k}'] = i + k

print(globals())
print(plus_1_2) # we can call them!
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1735136102869/5f0d282c-9ec6-4a19-9102-16f0aa4149b8.png align="center")