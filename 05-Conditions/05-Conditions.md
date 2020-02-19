Conditions
==========
As our programs grow more complex, we frequently want to execute a block of code only if a specific condition is met. For example, we might want to output a message only if a certain variable is less than some value. This is where conditions come in handy &ndash; they allow us to run code only if a condition is fulfilled. Conditions are another important building block of almost any real-world program. Just like functions, conditions allow as to control the flow of execution (which is otherwise linear from top to bottom).

Comparisons
-----------
A condition is based on a comparison. A comparison is an expression, which means that it has a value. Because a condition can be either true or false, Python has a special data type `bool` exactly for this purpose. A `bool` can either be `True` or `False` (notice the capitalization):

```python
>>> x = True
>>> type(x)
bool
>>> y = False
>>> type(y)
bool
```

### Comparison operators
Python features the following binary comparison operators:

- Equality `==`
- Inequality `!=`
- Less than `<`
- Greater than `>`
- Less than or equal `<=`
- Greater than or equal `>=`

Here are some examples:

```python
>>> x = 2
>>> x == 2
True
>>> x != 2
False
>>> x > 2
False
>>> x < 10
True
```

We can combine two or more comparison expressions using the `and` and `or` operators.

```python
>>> x > 0 and x < 10
True
>>> x == -2 or x == 2
True
>>> x > 5 or x < 10 and x > 8
False
```

Note that Python has a shortcut for the first expression of the previous example block:

```python
>>> x > 0 and x < 10
True
>>> 0 < x < 10
True
```

The `not` operator inverts a boolean expression:
```python
>>> not True
False
>>> not False
True
>>> not 0 < x < 10
False
```

We can always use parentheses to change precedence or improve readability:

```python
>>> not(0 < x < 10)
False
>>> (x < 0) or (x >= 2)
True
```

Finally, Python has an `is` and `in` operators that also produce boolean results. The `is` operator checks if two objects are identical (as opposed to `==`, which only checks if two values are identical). This distinction is important, but we won't need it very often especially when we are just beginning to learn Python.

The `in` operator checks whether some value is contained in some sequence. We will come back to this operator when we introduce Python lists (the `list` type).

### Comparing floating point numbers
Python distinguishes between integer numbers (`int`) and floating point numbers (`float`). These two types represent numbers enterily differently. Most noteably, `int` have exact internal representations, whereas `float` numbers can only be stored with limited precision in general. This can lead to subtle issues especially when we are comparing two floating point numbers for equality:

```python
>>> 0.1 + 0.1 + 0.1 == 0.3
False
```

A common solution is not to test for exact equality, but to allow a certain amount of wiggle space for two numbers to still compare equal:

```python
>>> (0.1 + 0.1 + 0.1) - 0.3 < 1e-15
True
```

The `math` module has a function called `isclose`, which can be used exactly for this purpose:

```python
>>> import math
>>> math.isclose(0.1 + 0.1 + 0.1, 0.3)
True
```

Here's another example where we are bitten by rounding errors of floating point arithmetic. Let's divide 4 by 0.4, which is 10 as we can readily verify ourselves.

```python
>>> 4 / 0.4
10.0
```

When we now compute the integer division result, we would expect the result to be 10, but strangely this is not the case in Python:

```python
>>> 4 // 0.4
9.0
```

The reason is that due to limited precision, rounding errors can be introduced.


Exercises
---------

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.