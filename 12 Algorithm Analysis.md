#computing 
[[Computing]]

# 12 Algorithm Analysis

# 12.1 Running Time

**Running time** is derived by taking the number of basic operations (mathematical, comparisons, assignments) executed by the algorithm.

The running time of algorithms is a function $T$ of the size of its input $n$, which is denoted as $T(n)$, where $n\ge0, n \in \mathbb{Z}$ and $T(n) \gt 0$ for all values of $n$.

## 12.1.2 Counting Running Time

To count the running time of a block of code written sequentially, we add up the number of operations

If we have nested loops, we multiply the number of operations

# 12.2 Big $O$ notation

There are 2 important principles to remember when working with big $O$ notation.
1. Constant factors doesn't matter. 
	- if $T\left(n\right)$ is $O\left(df\left(n\right)\right)$ for some constant $d>0$, then $T\left(n\right)$ is $O\left(f\left(n\right)\right)$, i.e. we ignore the multiplicative constants.
2. The low-order terms don't matter.
	- if $T\left(n\right)$ is $O\left(n^3+n\right)$, then $T\left(n\right)$ is $O\left(n^3\right)$. In particular, we can ignore the additive constants as well.

For example:
$O(4) \to O(1)$
$O(2n+2) \to O(n)$

**Common running times for algorithms:**

| Big $O$      | Name                              |
| ------------ | --------------------------------- |
| $O(1)$       | Constant                          |
| $O(\log n)$  | Logarithmic                       |
| $O(n)$       | Linear                            |
| $O(n\log n)$ | Log-linear                        |
| $O(n^2)$     | Quadratic                         |
| $O(n^k)$     | Polynomial, $k \in \mathbb{Z}^+$  |
| $O(k^n)$     | Exponential, $k \in \mathbb{Z}^+$ |

The entries in the table are arranged by efficiency.

In most cases, the following holds for algorithms:
- $O(1)$ - algorithm does not depend on input size
- $O(\log n)$ - problem gets reduced in half each time through the process
- $O(n)$ - simple iterative or recursive programs
- $O(n^k)$ - nested loops or recursive calls
- $O(k^n$) - multiple recursive calls at each level

**Time complexity of algorithms in chapter 11:**

| Algorithm      | Time complexity                    |
| -------------- | ---------------------------------- |
| Linear Search  | $O(n)$                             |
| Binary Search  | $O(\log n)$                        |
| Insertion Sort | $O(n^2)$                           |
| Bubble Sort    | $O(n^2)$                           |
| Quicksort      | avg: $O(n \log n)$ worst: $O(n^2)$ |
| Merge Sort     | $O(n\log n)$                                  |

**Useless definition:**
Let $T(n)$ be the running time of algorithm $A$ and $f\left(n\right)$ be some function defined on the nonnegative integers $n$. We will use the following statements interchangeably:
- $T\left(n\right)$ has order of growth of $f\left(n\right)$,
- $T\left(n\right)$ is $O\left(f\left(n\right)\right)$,
if and only if there exists an integer $n_0$ and a constant $c>0$ such that for all integers $n\geq n_0$, we have $T\left(n\right)\leq cf\left(n\right)$. In other words, we can bound the value of $T(n)$ by some constant multiple of the value of $f(n)$ when $n$ is big enough.

_Last edited 18/09/2023 by Joshua Lim NJC_