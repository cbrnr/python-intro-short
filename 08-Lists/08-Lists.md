Lists
=====
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
Lists have their own host of methods. Bear in mind that in general, list methods change the given list *in place*, whereas string methods always create a new string.



Exercises
---------

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.