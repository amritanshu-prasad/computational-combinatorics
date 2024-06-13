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

## Random Sampling

Random integer generators are useful for sampling from a discrete structure.
Python provides the `randint` function from its `random` module.

```{code-cell} ipython3
from random import randint
```

Let us create a list of 1000 random numbers from 0 to 9 (both ends included).
Each integer is equally likely to be selected.

```{code-cell} ipython3
L = [randint(0,9) for i in range(1000)]
```

We can examine the frequencies of the numbers generated.
We expect each of the integers 1 to 10 to occur about 100 times.
However, randomness will imply a certain amout of variation.

```{code-cell} ipython3
from matplotlib.pyplot import hist
hist(L)
```

## A general purpose algorithm for sampling from a finite set

The `randint` function can be used to sample randomly from any finite set as follows:

1. Create a list containing all the elements of the finite set.
2. Let `n` be the length of the list.
3. Choose a random integer `i` between 0 and n-1.
4. Return the element of the list with index `i`.

```{code-cell} ipython3
def random_element(L):
    L = list(L) # in case L is some iterable that is not a list
    n = len(L)
    i = randint(0,n-1)
    return L[i]
```

Let us try this out on our [generator for binary sequences](generator:binary-sequences) 

```{code-cell} ipython3
def binary_sequences(n):
    if n == 0:
        yield []
    else:
        for seq in binary_sequences(n-1):
            yield seq + [0]
            yield seq + [1]
```

to generate a random binary sequence of length three:

```{code-cell} ipython3
random_element(binary_sequences(3))
```

```{code-cell} ipython3

```
