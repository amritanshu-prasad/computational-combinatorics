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

# Binary Sequence

### Definition

A *binary sequence* of length $n$ is a sequence of the form $(a_0,\dotsc,a_{n-1})$, where $a_i\in \{0,1\}$ for $i=0,\dotsc,n$.

### Example: Binary Sequences of Length Three

There are four binary sequences of length $3$, namely:
$$
000, 001, 010, 011, 100, 101, 110, 111
$$
For compactness of notation, the parentheses and commas have been removed.
Moreover the sequences have been listed in dictionary order, also known as *lexicographic order*:
Imagine a language whose alphabet only has two letters, namely $0$ and $1$.
Each word in this language would be a binary sequences.
If all binary sequences were words in this language, a dictionary would list them precisely in the order above.
(generator:binary-sequences)=

Let us generate all binary sequences of length `n` in lexicographic order [using a python function with `yield`](method:yield)

```{code-cell} ipython3
def binary_sequences(n):
    if n == 0:
        yield []
    else:
        for seq in binary_sequences(n-1):
            yield seq + [0]
            yield seq + [1]
```

```{code-cell} ipython3
for seq in binary_sequences(3):
    print(seq)
```

```{code-cell} ipython3

```
