Strings
=======
Introduction
------------
We will now start touring some of the most widely used data types in Python. In this chapter, we will discuss the string (`str`) data type. The following lessons will showcase lists (`list`) and dictionaries (`dict`).

Briefly, the built-in data types can be categorized as follows (the examples in parentheses are not exhaustive):

- Logical (`bool`)
- Numeric (`int`, `float`, `complex`)
- Sequences
  - Containers (`list`, `tuple`)
  - Flat sequences (`str`, `bytes`, `bytearray`)
- Mappings (`dict`, `set`, `frozenset`)

Python really loves sequences, and one of the most frequently used data types are lists, tuples, and strings. More on that soon, but let's first recap what we already know. We are already familiar with two numeric types, namely `int` and `float`:

```python
>>> a = 17
>>> b = 2.5
>>> type(a)
int
>>> type(b)
float
```

Python also supports complex numbers out of the box (`j` is used for the imaginary unit):

```python
>>> c = 15 + 7j
>>> type(c)
complex
```

Mutable and immutable data types
--------------------------------
Python distinguishes between two kinds of data types: mutable and immutable ones. Mutable objects can be changed after they have been created, whereas immutable objects can *not* be changed after they have been instantiated.

From the data type categorization we have just discussed, only `list`, `bytearray`, `dict`, and `set` are mutable &ndash; all other types are immutable.

For example, let's see what immutable means for an `int` object. First we assign the name `a` to the immutable `int` object `2`:

```python
>>> a = 2
```

The `id` function returns the unique ID of a Python object. This is just a number, but if two objects have different IDs we know that they are two different objects. Conversely, if two objects have identical IDs we know that they are really only one object.

```python
>>> id(a)
4549479360
```

Let's re-assign our name `a` to the `int` object `3`:

```python
>>> a = 3
```

To verify that `a` is attached to a different object now, we inspect its ID:

```python
>>> id(a)
4549479392
```

The ID is different than before, which means that `a` now refers to a different object. In other words, re-assigning `a` did *not* change the original `2` object (it cannot be changed because an `int` object is immutable), but the name simply points to a different object.

In this chapter, we will see that strings are also immutable &ndash; once a string is created it cannot be changed/modified anymore. Consider the following example where we are trying to change one character in an existing string (more on that later):

```python
>>> s = "Pithon"
>>> s[1]  # character at index 1
'i'
>>> s[1] = "y"  # let's try to change that character
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-7-91d25f8c1859> in <module>
----> 1 s[1] = "y"

TypeError: 'str' object does not support item assignment
```

Clearly, modifying a string after it has been created is not supported because strings are immutable.

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.