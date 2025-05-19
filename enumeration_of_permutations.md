---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.2
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

# Enumeration of Permutations using Fischer-Yates shuffles

```{code-cell} ipython3
from itertools import product
from random import randint

def permutation_from_table(inversion_table,n=FileNotFoundError):
    inversion_table = list(inversion_table)
    n = len(inversion_table)
    w = list(range(1,n+1))
    for k in range(n-1,-1,-1):
        w[inversion_table[k]], w[k] = w[k], w[inversion_table[k]]
    return w

def permutations_fy(n):
    """Generate permutations on `n` letters using Fischer-Yates shuffles."""
    inversion_tables = product(*(range(i) for i in range(1,n+1)))
    for inversion_table in inversion_tables:
        yield permutation_from_table(inversion_table)
```

```{code-cell} ipython3
list(permutations_fy(3))
```

```{code-cell} ipython3
def random_permutation_fy(n):
    """Generate a random permutation using Fischer-Yates shuffles."""
    table = [randint(0,i) for i in range(n)]
    return permutation_from_table(table)
```

```{code-cell} ipython3
[random_permutation_fy(3) for i in range(100)]
```

```{code-cell} ipython3
from math import factorial
def rank(w):
    """Return the rank of the permutation ``w`` in the lexicographic list of permutations of the same length."""
    n = len(w)
    letters = list(range(1,n+1))
    rank = 0
    for i in range(n):
        a = w[i]
        r = letters.index(a)
        letters.pop(r)
        rank += factorial(n-i-1)*(r-1)
    return rank
```

```{code-cell} ipython3
rank([1,2,3])
```

```{code-cell} ipython3

```
