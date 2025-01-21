---
title: "[Python] Leveraging __name__ for Efficient Python Module Organization"
seoTitle: "[Python] Leveraging __name__ for Efficient Python Module Organization"
seoDescription: "We can distinguish between running directly and importing as a module. When a Python file is executed directly, the interpreter sets the special variable __"
datePublished: Mon Dec 23 2024 13:53:45 GMT+0000 (Coordinated Universal Time)
cuid: cm513lekt000409l843qhanzh
slug: python-leveraging-name-for-efficient-python-module-organization
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1734960664641/b4ae8b73-9dfa-41d9-963c-e5886a256046.gif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1734962018820/e4eabfd1-f69c-4787-884a-c63d83422b4b.gif
tags: python, modules, dunder, name, built-in-variable, special-variable

---

---

## Introduction

If you have used python before, you may have seen a code snippet like this:

```python
if __name__ == '__main__':
    # do something
```

This code is so simple and short, but do you fully understand what it means, and why it is so important to avoid errors when you create modules? This article will introduce what `__name__` is, and how essential it is when we create modules.

---

## What is \_\_name\_\_?

You may have seen some python codes that start with double underscore, which we also call dunder (short for “double underscore”). It is a special or built-in variable. `__name__` is assigned with a new value when python interpreter runs. Therefore, it is a variable, but you don’t declare and you don’t really assign a value to it. It automatically works as python interpreter runs.

The value of `__name__` is dependent on whether your current file is imported or not. Let’s have a look at this example:

```python
# ex_module.py
def func():
    print("Hi")

print('__name__:', __name__) 
```

```python
# main.py
import ex_module.py # IMPORTANT! ex_module is imported, so __name__ changes.
ex_module.func() 
```

Output:

```python
>>> Hi 
>>> __name__: ex_module
```

`__name__` is ex\_module because `ex_module.py` is imported in `main.py`.

Now, what if ex\_module.py is not imported?

```python
# ex_module.py
print('__name__:', __name__)
```

Output:

```python
>>> __name__: __main__
```

`__name__` is `__main__` because `ex_module.py` is not imported anywhere else. Consequently, this means `ex_module.py` is the main file. Let’s say you are building a program, and you will need a lot of modules to import. You would have built your custom modules, right? The main file imports all the modules you created, but is the main file imported? → NO!

So, python interpreter understands that it is the main file if the file is not imported.

---

## Why Do We Need \_\_name\_\_?

We can distinguish between running directly and importing as a module. When a Python file is executed directly, the interpreter sets the special variable `__name__` to `"__main__"`. If the file is imported as a module, `__name__` will be set to the name of the module.

This behavior is particularly useful for writing scripts that can be used both as standalone programs and as reusable modules.