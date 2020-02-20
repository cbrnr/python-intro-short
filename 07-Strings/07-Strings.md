Strings
=======
We will now start touring some of the most widely used data types in Python. In this chapter, we will discuss the string (`str`) data type. The following lessons will showcase lists (`list`) and dictionaries (`dict`).

Briefly, the built-in data types can be categorized as follows (the examples in parentheses are not exhaustive):

- Logical (`bool`)
- Numeric (`int`, `float`, `complex`)
- Sequences
  - Containers (`list`, `tuple`)
  - Flat sequences (`str`, `bytes`, `bytearray`)
- Mappings (`dict`, `set`, `frozenset`)

Remember that the `type` function can help you determine the type of a given object.

We are already familiar with two numeric types, namely `int` and `float`:

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

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.