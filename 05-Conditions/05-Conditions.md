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

Conditions
----------
We are now ready to discuss conditions. A condition checks whether a specific comparison (boolean expression) is `True` or `False`. Python runs an associated block of code only if the result is `True`.

Here's the structure of a condition in Python as pseudo-code:

```
if <expression is True>:
    <do something>
    ...
    ...
elif <expression is True>:  # optional
    <do something else>
    ...
elif <expression is True>:  # optional
    <do something else>
    ...
    ...
else:  # optional
    <do something>
```

Clearly, the indented lines of code belonging to a specific condition are only executed if the condition is `True`. We can test for several condition sequentially by using `elif` statements after the initial `if` statement. If no condition is `True`, the code in the `else` block is run. Importantly, Python only executes the first block of code where the condition returns `True`; once this happens, all other `elif` and `else` blocks are completely ignored.

### Example 1
Let's work through some examples. Here's a simple condition consisting of only one `if` statement:

```python
a = 2

if a > 0:
    print("a is a positive number")
    print("this is good to know")
```

If we run these lines, the indented block of code will be executed, because `a` is in fact greater than zero, the condition `a > 0` is `True`, so we get the following output:
```
a is a positive number
this is good to know
```

If we take the same `if` block, but set `a = 0` before, we do not get any output because the indented block of code is not run (the condition `a > 0` is `False`):

```python
a = 0

if a > 0:
    print("a is a positive number")
    print("this is good to know")
```

### Example 2
We can now add an optional `else` branch, which gets executed if none of the previous conditions returned `True`:

```python
a = 0

if a > 0:
    print("a is a positive number")
    print("this is good to know")
else:
    print("a is either 0 or a negative number")
```

Now because `a > 0` is `False`, Python will run the code associated with the `else` branch, so we get the following output:
```
a is either 0 or a negative number
```

### Example 3
Also optionally, we can add (an arbitrary number of) `elif` branches, for example:

```python
a = -5

if a > 0:
    print("a is a positive number")
    print("this is good to know")
elif a < 0:
    print("a is a negative number")
else:
    print("a is 0")
```

This results in:
```
a is a negative number
```

### Example 4
Due to the fact that Python only runs the code associated with the first condition yielding `True`, the order of the conditions is important. Consider the following two examples containing identical conditions, but in a different order:

```python
a = 4

if a > 5:
    print("One")
elif a < 10:
    print("Two")
elif a == 4:
    print("Three")
else:
    print("Four")
```

This example results in:
```
Two
```

```python
a = 4

if a > 5:
    print("One")
elif a == 4:
    print("Three")
elif a < 10:
    print("Two")
else:
    print("Four")
```

Now this example results in:
```
Three
```

### Example 5
We haven't really talked about data types other than numeric ones yet, but Python can also compare non-numeric types such as strings:

```python
>>> p = "Python"
>>> r = "R"
>>> p == r
False
>>> p > r
False
>>> p < r
True
```

Therefore, we can use such comparisons in a condition:

```python
if p != r:
    print("Python and R are different, but both are pretty cool!")
```

Exercises
---------
1. Write the following program:
   - First, ask the user to type in two numbers `x` and `y`. You can use the `input` function to get user input. Note that `input` always returns a `str`, but you can use the `int` function to convert a number contained in a `str` to `int`!
   - Once you have both numbers `x` and `y`, check if their sum is greater than 50.
   - If the sum is greater than 50, print "Greater than 50!"
   - If the sum is less than 50, print "Less than 50!"
   - If the sum is exactly 50, print "50!"
---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.