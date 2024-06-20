---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.2
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# Iterators and iterable classes

In python, an iterator is an object that you can loop over.
For example, you can loop over a list, a string, or a dictionary in python.

```{code-cell} ipython3
print("looping over a list")

for i in [1, 2, 3]:
    print(i)

print("looping over a string")

for i in "123":
    print(i)

print("looping over a dictionary")

d = {1:"a", 2:"b", 3:"c"}
for i in d:
    print(i)
```

For example, `range(n)` is an iterator for the first `n` non-negative integers.

```{code-cell} ipython3
for i in range(3):
    print(i)
```

## Make your own iterator

We discuss three ways.

(method:yield)=
### 1. Using `yield` instead of `return` in a function

```{code-cell} ipython3
def my_range(n):
    i = 0
    while i < n:
        yield i
        i += 1
```

Unlike a function with a return command, this function will continue to run after the `yield` statement.

```{code-cell} ipython3
for i in my_range(3):
    print(i)
```

### 2. Create a class with an `__iter__` method

```{code-cell} ipython3
class MyRange():
    def __init__(self, n):
        self.n = n

    def __iter__(self):
        return my_range(self.n)
```

The `__iter__` method returns an iterable object. In this case it is the iterable function `my_range` that we defined earlier.

```{code-cell} ipython3
for i in MyRange(3):
    print(i)
```

### 3. Create a class with a `__next__` method

```{code-cell} ipython3
class MyRange2():
    def __init__(self, n):
        self.n = n
        self.i = 0

    def __iter__(self):
        return self

    def __next__(self):
        i = self.i
        if self.i < self.n:
            self.i += 1
            return i
        else:
            raise StopIteration
```

```{code-cell} ipython3
for i in MyRange2(3):
    print(i)
```
