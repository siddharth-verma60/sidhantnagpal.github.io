---
layout: post
title: "GSoC 2018: SymPy - Week 6 & 7"
summary: "SymPy - Transforms, Convolution & Linear Recurrence Evaluation"
comments: true
category:
tags:
- gsoc
- sympy
---

<img src="/files/gsoc-sympy.png" style="width:75%; height:75%; float:left; margin-left:55px;" />
<br clear="all" />

The second phase of Coding Period has started.

I started this phase working on recurrence submodule under `discrete`. After having an initial discussion with [Kalevi](https://github.com/jksuom) regarding the functionality to be implemented, I did the proof-of-concept for the same on a remote branch.

After the approach was finalized, the implementation was polished before opening the PR. The PR [#14816](https://github.com/sympy/sympy/pull/14816) also included documentation, doctests, and unit tests for the module.

The method `linrec(coeffs, init, n)` takes coefficients, initial values and point of evaluation for the linear recurrence. Usage for a recurrence like `f(n) = f(n - 7) + f(n - 13) + f(n - 17)` (having order `17`) would be:

```python
In []: coeffs, init = [0]*17, [1]*17
In []: coeffs[7 - 1] = coeffs[13 - 1] = coeffs[17 - 1] = 1
In []: [linrec(coeffs, init, n) for n in range(40, 50)]
Out[]: [17, 21, 21, 23, 29, 31, 31, 35, 41, 41]

In []: def f(n):
  ...:     if n < 17:
  ...:         return 1
  ...:     return f(n - 7) + f(n - 13) + f(n - 17)
  ...:

In []: [f(n) for n in range(40, 50)]
Out[]: [17, 21, 21, 23, 29, 31, 31, 35, 41, 41]
```

As suggested by [Aaron](https://github.com/asmeurer), it will be good to have a user-facing method that calls `linrec` internally for performing the computation.

Looking forward to another exciting week.
