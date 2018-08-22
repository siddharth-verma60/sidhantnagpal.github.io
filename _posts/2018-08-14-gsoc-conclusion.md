---
layout: post
title: "Concluding GSoC 2018: SymPy"
summary: "SymPy - Transforms, Convolution & Linear Recurrence Evaluation"
comments: true
category:
tags:
- gsoc
- sympy
---

<img src="/files/gsoc-sympy.png" style="width:75%; height:75%; float:left; margin-left:55px;" />
<br clear="all" />

This post summarises the work that I have done during GSoC for SymPy. The links to the Pull Requests are in chronological order under each header. For following the progress made during GSoC, see my [weekly posts](https://sidhantnagpal.github.io/blog).

This summer has been a great learning experience and has helped me get a good exposure of test-driven development. I plan to actively review the work that has went into this project and continue contributing to SymPy. I am grateful to my mentors, [Kalevi](https://github.com/jksuom) and [Aaron](https://github.com/asmeurer) for reviewing my work, giving me valuable suggestions, and being readily available for discussions.

## Pull Requests

This is the [list](https://github.com/sympy/sympy/pulls?q=is%3Apr+author%3Asidhantnagpal+is%3Aclosed) of merged Pull Requests.

#### Major Additions
- [sympy/sympy#14725](https://github.com/sympy/sympy/pull/14725): Add discrete module, and transforms sub-module including Fast Fourier Transform, Number Theoretic Transform, and include docstring, doctests, unit-tests.
- [sympy/sympy#14745](https://github.com/sympy/sympy/pull/14745): Add convolution sub-module including `convolution_fft`, `convolution_ntt` and a general method `convolution` for identifying the type of convolution and handling the cyclic convolution case, and include docstring, doctests, unit-tests.
- [sympy/sympy#14765](https://github.com/sympy/sympy/pull/14765): Implement Walsh Hadamard Transform and include doctests, unit-tests, docstring for the same.
- [sympy/sympy#14783](https://github.com/sympy/sympy/pull/14783): Implement `convolution_fwht` and add support for keyword `dyadic` in the general `convolution` method, and include docstring, doctests, unit-tests.
- [sympy/sympy#14816](https://github.com/sympy/sympy/pull/14816): Add a method `linrec` which allows evaluation of linear recurrences without obtaining closed form expressions, and include tests for the same.
- [sympy/sympy#14853](https://github.com/sympy/sympy/pull/14853): Implement Möbius Transform using Yate's Dynamic Programming method while having `subset` keyword for flexibility of the implementation, and include docstring, doctests, unit-tests.
- [sympy/sympy#14878](https://github.com/sympy/sympy/pull/14878): Implement subset convolution and include docstring, doctests, unit-tests.
- [sympy/sympy#14928](https://github.com/sympy/sympy/pull/14928): Add covering product in convolutions sub-module and include docstring, doctests, unit-tests.
- [sympy/sympy#14954](https://github.com/sympy/sympy/pull/14954): Add intersecting product in convolutions sub-module and include docstring, doctests, unit-tests.

#### Documentation and Code Refinements
- [sympy/sympy#14969](https://github.com/sympy/sympy/pull/14969): Improve Sphinx [docs](http://docs.sympy.org/) for SymPy, use plural module names - `convolutions` and `recurrences`, refine the documentation for `discrete` module.
- [sympy/sympy#14994](https://github.com/sympy/sympy/pull/14994): Add reStructuredText file for `discrete` module for inclusion in Sphinx docs, which can be referred [here](http://docs.sympy.org/dev/modules/discrete.html).
- [sympy/sympy#15025](https://github.com/sympy/sympy/pull/15025): Refine `discrete` module to fix tests using floats instead of Rationals, adding warning about sequence size for `fft` and other improvements.

#### Additional Improvements
- [sympy/sympy#14712](https://github.com/sympy/sympy/pull/14712): Add `.rewrite(exp)` capability for instances of `Pow` and fix bugs in `solvers` module.
- [sympy/sympy#14907](https://github.com/sympy/sympy/pull/14907): Fix exception handling for factorial modulo and refine the signature for general `convolution` method.
- [sympy/sympy-bot#18](https://github.com/sympy/sympy-bot/pull/18): Fix the issue of incorrect links being referred in wiki by explicitly specifying the links instead of using relative paths.

## Future Work
- Adding a user-facing public method that internally calls `discrete.recurrences.linrec` and possibly extending it for different types of recurrences as well.
- Making methods `fft` and `convolution_fft` efficient for both symbolic and numeric variants, as some discussion and benchmarking has been done for it and there is some work done by [Colin](https://github.com/cbm755) for implementing a `ComplexFloat` class in [sympy/sympy#12192](https://github.com/sympy/sympy/pull/12192) which would be very helpful for the same.
