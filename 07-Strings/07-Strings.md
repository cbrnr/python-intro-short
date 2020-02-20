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

In this chapter, we will see that strings are also immutable &ndash; once a string is created it cannot be changed/modified anymore. Consider the following example where we are trying to change one character in an existing string (more on the mechanics and meaning of the square brackets later):

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

Creating strings
----------------
We now turn to the string data type. A string is an immutable sequence of characters. All elements of a string are of the same type (characters), so we refer to a string as a flat sequence (in contrast, container sequences can contain elements of different arbitrary types). Python uses single or double quotes to enclose the contents of a string, for instance:

```python
>>> s1 = "String"
>>> s1
'String'
>>> s2 = 'Another string'
>>> s2
'Another string'
```

It doesn't matter if you use single or double quotes as long as the opening and closing quotes are the same. However, there might be cases when you would prefer one type of quote over the other:

```python
>>> s3 = 'What does "ontology" mean?'
>>> s4 = "That's a string too!"
```

Specifically, if the string itself contains a single (double) quote, it is easier to use a double (single) quote to enclose the string. However, what happens if the string contains both single and double quotes? In this case, we need to escape the quote characters with a backslash like this:

```python
>>> s5 = "This \"string\" has 'both' quotes!"
>>> s6 = 'This "string" has \'both\' quotes!'
```

Using such escape sequences, it is also possible to include non-printable characters in a string. For example, a newline is escaped with `"\n"`:

```python
>>> s7 = "Line one.\nLine two."
>>> s7
'Line one.\nLine two.'
>>> print(s7)
Line one.
Line two.
```

The `print` function converts escape characters to their intended representation, so in the previous example `"\n"` is displayed as an actual line break.

Another option to define a string is to use triple quotes. Triple-quoted strings can span multiple lines, which is not possible with single-quoted strings:

```python
>>> s8 = """This is
... a multi-line
... string."""
>>> s8
'This is\na multi-line\nstring.'
>>> print(s8)
This is
a multi-line
string.
```

String indexing
---------------
We can access individual elements of a string (characters) &ndash; this is called indexing. Python uses an integer index inside square brackets to extract the character at a particular position corresponding to the index. Note that Python starts counting at zero, so the first character has index 0, the second has index 1, and so on.

Here's an example:

```python
>>> s = "Python"
>>> s[0]
'P'
>>> s[1]
'y'
>>> s[5]
'n'
```

If we specify an index which exceeds the length of the string we get an error:

```python
>>> s[6]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

An index can be negative. Negative indices denote the position in a string counting from the end:

```python
>>> s[-1]
'n'
>>> s[-2]
'o'
>>> s[-6]
'P'
```

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.