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

# Probability

The probability of an event refers to the likelihood of an even ocurring.
It is a number between $0$ and $1$, where probability $0$ means that the event will never happen, and probability $1$ means that the event will always happen.

As a concrete example, consider an urn with $3$ red balls and $2$ blue balls. If we draw a ball at random, the probability of drawing a red ball is $\frac{3}{5}$, and the probability of drawing a blue ball is $\frac{2}{5}$.

On a computer we can simulate the urn experiment as follows: we will think of the five balls in the urn as the integers $0,1,2,3,4$.
We will regard the numbers $0,1,2$ as red balls, and the numbers $3,4$ as blue balls.
We will use the `random` module to generate a random number between $0$ and $4$, and then we will check if the number is less than $3$ (red ball) or greater than or equal to $3$ (blue ball).

```{code-cell} ipython3
from random import randint 
def urn_experiment(red=3, blue=2):
    n = red + blue # the total number of balls in the urn_experiment
    a = randint(0,n-1) # a random integer between 0 and n-1, including both ends 
    if a < red:
        return "R"
    else:
        return "B"

urn_experiment()
```

A single run of the urn experiment will return either `red` or `blue`.
From this, it is not really possible to determine the proportion of red balls to blue balls in the urn.
But if we run the urn experiment many times, we may get a clue about the proportion of red balls to blue balls in the urn.

```{code-cell} ipython3
L = [urn_experiment() for i in range(10000)]
print(L.count("R")/10000)
```

In the preceding code, we ran the experiment ten thousand times.
Out of 10000 runs, close to 6000 runs returned `red`, meaning that the fraction of red balls in the urn is close to $\frac{3}{5}$. 

+++

## Formal Definition of Probability

A probability space is a pair $(X,P)$, where $X$ is a set (called the *sample space*, to be thought of as the space of all possible outcomes of an experiment), and a probability function $P$ that assigns a number $0\leq p(x)\leq 1$ to each outcome $x\in X$ such that
$$
\sum_{x\in X} p(x) = 1.
$$
The probability of a subset $A\subset X$ is defined as
$$
P(A) = \sum_{x\in A} p(x).
$$
$P(A)$ is the probability that one of the elements in $A$ is the outcome of the experiment.


### Example: Urn Experiment

In the urn experiment above $X = \{0,1,2,3,4\}$, and the probability function is given by $P(x) = \frac{1}{5}$ for all $x\in X$.
The balls $0,1,2$ are red, and the balls $3,4$ are blue.
The event of drawing a red ball corresponds to the subset $A = \{0,1,2\}$, and the probability of drawing a red ball is $P(A) = \frac 15 + \frac 15 + \frac 15 = \frac 35$.

### Example: An abstract probability space

Let $X=\{\text}{Red},\text{Blue}\}$.
Define $P(\text{Red}) = \frac 35$ and $P(\text{Blue}) = \frac 25$.
Then $

```{code-cell} ipython3

```
