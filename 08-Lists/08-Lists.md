Lists and tupels
================
Creating lists
--------------
A list is a container sequence which, unlike strings, can contain elements of arbitrary types (even lists). We use square brackets to construct a new list (with commas separating the list elements):

```python
>>> x = [23, "Hello!", "test", 1.44, True]
>>> y = [1, "1", [1, 2, 3], ["test", False, [True, True, 2, 4]]]
```

Indexing and slicing
--------------------
Indexing and slicing works exactly like with strings. We use the indexing operator (square brackets) to extract single or multiple elements from a list:

```python
>>> x[0]
23
>>> x[-2]
1.44
>>> x[1:4]
['Hello!', 'test', 1.44]
>>> x[::-1]
[True, 1.44, 'test', 'Hello!', 23]
```

Working with lists
------------------
### Length
The `len` function returns the number of elements in a list:

```python
>>> len(x)
5
>>> len(y)
4
```

An empty list has length 0:

```python
>>> z = []
>>> len(z)
0
```

### Mutating lists
In constrast to strings, lists are mutable. That is, elements in a list can be modified after the list has been created. For example:

```python
>>> x
[23, 'Hello!', 'test', 1.44, True]
>>> x[1] = 12345
>>> x
[23, 12345, 'test', 1.44, True]
```

### Concatenation
Adding lists with the `+` operator concatenates their elements and creates a new list:

```python
>>> [1, 2, "three"] + ["four", 5, 6.0]
[1, 2, 'three', 'four', 5, 6.0]
```

Likewise, the `*` concatenates list elements multiple times:

```python
>>> [1.0, 2, "three"] * 3
[1.0, 2, 'three', 1.0, 2, 'three', 1.0, 2, 'three']
```

### List methods
Lists have their own host of methods. Bear in mind that in general, list methods change the given list *in place*, whereas string methods always create a new string. One of the most frequently used methods is `append`, which (as the name implies) appends a new element at the end of the list:

```python
>>> x
[23, 12345, 'test', 1.44, True]
>>> x.append(13)
>>> x
[23, 12345, 'test', 1.44, True, 13]
```

If we want to append more than one element, we can use the related `extend` method:

```python
>>> x.extend(["A", "B", "C"])
>>> x
[23, 12345, 'test', 1.44, True, 13, 'A', 'B', 'C']
```

Note that `x.append(["A", "B", "C"])` also works but produces a different result &ndash; this appends one element, namely the list `["A", "B", "C"]`:

```python
>>> x.append(["A", "B", "C"])
>>> x
[23, 12345, 'test', 1.44, True, 13, 'A', 'B', 'C', ['A', 'B', 'C']]
```

The `del` command or the `pop` method both remove elements from a list. For example, this removes the two elements `x[1:3]`:

```python
>>> del x[1:3]
>>> x
[23, 1.44, True, 13, 'A', 'B', 'C', ['A', 'B', 'C']]
```

Similarly, this is how to remove the last element using `pop`:

```python
>>> x.pop(-1)
['A', 'B', 'C']
>>> x
[23, 1.44, True, 13, 'A', 'B', 'C']
```

Note that `pop` returns the removed element *and* changes the list in place (`del` does not return anything).

The `remove` method removes elements by value (instead of by index). For example, `x.remove(13)` removes the first element in the list which is equal to `13`:

```python
>>> x.remove(13)
>>> x
[23, 1.44, True, 'A', 'B', 'C']
```

Finally, the `sort` method sorts a list in place if this is possible. This means that all elements should be of the same type, otherwise sorting will result in an error.

```python
>>> x.sort()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: '<' not supported between instances of 'str' and 'bool'
```

```python
>>> h = [6, 9, 23, 1, -78, 44]
>>> h.sort()
>>> h
[-78, 1, 6, 9, 23, 44]
```

### Iterating over lists
Just like we saw in strings, the `in` operator checks whether a specific value is contained in a list:

```python
>>> x = [1, 2, 3, 4, 5]
>>> 2 in x
True
>>> 7 in x
False
```

Iteration with a for-loop also works as expected:

```python
>>> for element in x:
...     print(element)
...
1
2
3
4
5
```

Tuples
------
On a superficial level, tuples are immutable lists. We will not go into more detail why tuples are useful (there are many important applications), but suffice it to say that we should use tuples instead of lists whenever we do not want to change its elements. For example, instead of storing the latitude and longitude of a given location in a list, a tuple might be more reasonable (because the coordinates of a given location will not change).

The syntax for creating a tuple is similar to creating a list, except that it doesn't use square brackets. Strictly speaking, listing elements separated by commas defines a tuple, but sometimes parentheses are required and/or improve readability.

```python
>>> t = 23, "Hello!", "test", 1.44, True
>>> t
(23, 'Hello!', 'test', 1.44, True)
```

We cannot modify tuples because they are immutable:

```python
>>> t[1]
'Hello!'
>>> t[1] = 12345
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
```

List comprehensions
-------------------
There is another neat way to construct a list in Python. List comprehensions do not introduce any new functionality (everything can be accomplished without list comprehensions), but this so-called *syntactic sugar* makes some list assignments easier to read.

Consider the following example, where we want to create a list containing all squares from 1 to 10. We already know how to do this with a for-loop:

```python
squares = []
for n in range(1, 11):
    squares.append(n**2)
```

The resulting list looks as expected:

```python
>>> squares
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

An alternative list generation mechanism uses a list comprehension to build the same list. It is generally much more compact and looks as follows:

```python
>>> squares = [n**2 for n in range(1, 11)]
>>> squares
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

In general, a list comprehension is surrounded by square brackets (to denote that a list will be constructed). Inside the brackets, the first expression defines the individual elements that go into the list (`n**2` in our example). After that, something very similar to a for-loop iterates over some sequence (some iterable) to generate the individual elements (in our case, `n` takes on values from `range(1, 11)`).

Here's another example of a list comprehension, which multiplies each element in a (numeric) list by 2:

```python
>>> numbers = [-4, -2, 0, 2, 4]
>>> numbers2 = [n * 2 for n in numbers]
>>> numbers2
[-8, -4, 0, 4, 8]
```

Every time we want to apply some operation to each individual element in a list, a list comprehension might be the way to go. Another example is taking the absolute value of each element in our list:

```python
>>> numbers_abs = [abs(x) for x in numbers]
>>> numbers_abs
[4, 2, 0, 2, 4]
```

Remember that all of these list comprehensions can be written with a regular loop and the `append` method. We can also include a condition in the list comprehension, which will include an element in the new list only if the condition is `True`. This is useful for filtering values like in the following example, where we filter out all values greater than or equal to zero:

```python
>>> [x for x in numbers if x >= 0]
[0, 2, 4]
```

List comprehension can even be nested:

```python
>>> lst = [(x - 1, y - 2) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]
>>> lst
[(0, 1), (0, 2), (1, 1), (1, -1), (1, 2), (2, -1), (2, 2)]
```

This is a pretty complex list comprehension already, and in this case the traditional way might be more readable:

```python
lst = []  # start with an empty list
for x in [1, 2, 3]:
    for y in [3, 1, 4]:
        if x != y:
            lst.append((x - 1, y - 2))
```

The results are exactly the same (observe how the individual `for` and `if` statements correspond to each other in both list assignments).

Let's finish up this topic with a slightly less complex list comprehension just to see another example:

```python
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip().upper() + "!" for weapon in freshfruit]
['BANANA!', 'LOGANBERRY!', 'PASSION FRUIT!']
```


Exercises
---------
1. Write a function `histogram`, which accepts a list of numbers as its input argument. The function should convert the argument to a simple (vertical) histogram as follows. Each element of the list defines a row in the histogram, the length of which is defined by the actual value in the list. By default, the histogram should consist of `*` characters (but it should be possible to change this character with a second input parameter).

   Here are two examples that demonstrates the behavior of the function:

   ```python
   >>> histogram([1, 8, 5, 17, 14, 9, 2])
   *
   ********
   *****
   *****************
   **************
   *********
   **
   >>> histogram([1, 8, 5, 17, 2], char="-")
   -
   --------
   -----
   -----------------
   --
   ```

   Use the `print` function to print the histogram row by row. Repeating a string might be useful, for example `"*" * 8` is `"********"`.

2. Define a function `sum_of_squares` which takes a list of numbers and returns the sum of all squared elements (one number). Note that the built-in function `sum` computes the sum of a list of numbers.

3. Create a list `numbers` consisting of the 25 integers from 1 to 25. Based on this list, generate the following five new list:
   - `squares` containing the squared numbers
   - `evens` containing the even numbers
   - `odds` containing the odd numbers
   - `roots` containing the square roots of the numbers
   - `logs` containing the natural logarithms of the numbers

   For the last two lists, use the functions `sqrt` and `log` from the `math` module (first, `import math` and then use the functions as `math.sqrt` and `math.log`, respectively).

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.