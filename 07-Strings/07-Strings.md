7 – Strings
===========
We will now start touring some of the most widely used data types in Python. In this chapter, we will discuss the string (`str`) data type. The following lessons will showcase lists (`list`) and dictionaries (`dict`).

Briefly, the built-in data types can be categorized as follows (the examples in parentheses are not exhaustive):

- Logical (`bool`)
- Numeric (`int`, `float`, `complex`)
- Sequences
  - Containers (`list`, `tuple`)
  - Flat sequences (`str`, `bytes`, `bytearray`)
- Mappings (`dict`, `set`, `frozenset`)

Python really loves sequences, and one of the most frequently used data types are lists, tuples, and strings. Let's first recap what we already know. We are already familiar with two numeric types, namely `int` and `float`:

```python
>>> a = 17
>>> b = 2.5
>>> type(a)
int
>>> type(b)
float
```

Python also supports complex numbers out of the box (`j` is used for the imaginary unit $j^2 = -1$):

```python
>>> c = 15 + 7j
>>> type(c)
complex
```

Mutable and immutable data types
--------------------------------
Python distinguishes between two kinds of data types: *mutable* and *immutable* ones. Mutable objects can be changed after they have been created, whereas immutable objects can *not* be changed after they have been instantiated.

From the data type categorization we have just discussed, only `list`, `bytearray`, `dict`, and `set` are mutable &ndash; all other types are immutable.

For example, let's see what immutable means for an `int` object. First, we assign the name `a` to the immutable `int` object `2`:

```python
>>> a = 2
```

The `id` function returns the unique ID of a Python object. If two objects have different IDs, we know that they are two different objects. Conversely, if two objects have identical IDs, we know that they are really only one and the same object.

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

The ID is different than before, which means that `a` now refers to a different object. In other words, re-assigning `a` did *not* change the original `2` object (it cannot be changed because an `int` object is immutable), but the name simply points to a different object now.

In this chapter, we will see that strings are also immutable &ndash; once a string is created it cannot be changed/modified anymore. Consider the following example where we are trying to change one character in an existing string (more on the mechanics and meaning of the square bracket notation later):

```python
>>> s = "Pithon"
>>> s[1]  # character at index 1
'i'
>>> s[1] = "y"  # let's try to change that character
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```

Clearly, modifying a string after it has been created is not supported because strings are immutable.

Creating strings
----------------
Alright, so a string is an immutable sequence of characters. All elements of a string are of the same type (characters), so we refer to a string as a *flat* sequence (in contrast, *container* sequences can contain elements of different arbitrary types). Python uses single or double quotes to enclose the content of a string, for instance:

```python
>>> s1 = "String"
>>> s1
'String'
>>> s2 = 'Another string'
>>> s2
'Another string'
```

It doesn't matter if you use single or double quotes as long as the opening and closing quotes are the same. However, there might be cases when you would prefer one type over the other:

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
We can access an individual element of a string (a single character) &ndash; this is called indexing. Python uses an integer index inside square brackets to extract the character at a particular position corresponding to the index. Note that Python starts counting at *zero*, so the first character has index 0, the second has index 1, and so on.

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

An index can also be negative. Negative indices denote the position in a string counting from the *end*:

```python
>>> s[-1]  # last element
'n'
>>> s[-2]  # second last element
'o'
>>> s[-6]  # sixth last element
'P'
```

String slicing
--------------
Python also lets us extract more than one element from a string &ndash; this is called *slicing*. Inside the square brackets, we can specify a start index and a stop index separated by a colon. Optionally, we can also specify a step size (separated by another colon). As we have already seen with the `range` function, Python starts counting at zero and does not include the stop index.

```python
>>> s[0:3]
'Pyt'
>>> s[1:3]
'yt'
>>> s[0:5:2]
'Pto'
>>> s[-4:5]
'tho'
>>> s[-4:-6:-1]
'ty'
```

There are some shortcuts. If you omit the start index, the slice starts with the first element. If you omit the stop index, the slice ends with the last element (inclusive). If you omit the step size, the default of 1 is used.

```python
>>> s[:3]
'Pyt'
>>> s[3:]
'hon'
>>> s[::-1]  # negative step size counts backwards
'nohtyP'
```

Working with strings
--------------------
### Length
The built-in `len` function returns the length of a sequence, or in other words, the number of elements it contains. Therefore, `len` returns the number of characters in a string:

```python
>>> s = "Python"
>>> len(s)
6
>>> len("This is a pretty long string.")
29
```

We can also create an empty string like this:

```python
>>> s = ""
>>> len(s)
0
```

The enclosing quotes are *never* part of the actual string!

### Concatenation
Strings are immutable, so we cannot change them after they have been created:

```python
>>> s = "house"
>>> s[0]
'h'
>>> s[0] = "m"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
```

However, if we want to replace one or more characters in a string, we can always create a *new* string as follows:

```python
>>> s = "m" + s[1:]
>>> s
'mouse'
```

The previous snippet uses all characters except the first of the string `"house"` (so `s[1:]` is just `"ouse"`). It then prepends the string `"m"`, which together creates a new string object. Finally, we assign the name `s` to the new string.

Apparently, we can concatenate strings with the `+` operator. This creates a new string by appending all strings in the operation. Another example:

```python
>>> x = "a" + "a" + "a"
>>> x
'aaa'
```

It follows that the `*` operator performs repeated concatenation as a shortcut:

```python
>>> x = "a" * 3
>>> x
'aaa'
```

### String methods
A method is a function which is attached to an object. The syntax for calling a method differs slightly from a normal function, but conceptually methods are just functions. A method call always starts with the object you want to call the method on, followed by a dot, and finally the method call (which involves the method name and a pair of parentheses).

For example, strings have an `upper` method, which returns a new string in all caps:

```python
>>> x = "Hello!"
>>> x.upper()
'HELLO!'
```

The method call `x.upper()` basically calls a function `upper` and automatically passes the string object `x` as its first argument. We could also use `str.upper(x)` instead. However, the special method call syntax makes it clear that `upper` is directly attached to a string object (`int` objects do not have an `upper` method for example).

Bear in mind that all string methods return *new* strings, because existing strings are immutable.

We will now quickly tour some of the most frequently used string methods (see the [official Python string documentation](https://docs.python.org/3/library/stdtypes.html#str) for more details). We already saw `upper`, and not surprisingly there is also a `lower` method:

```python
>>> x = "Hello!"
>>> x.lower()
'hello!'
```

Just to re-iterate, we did not change the object `x` is assigned to:

```python
>>> x
'Hello!'
```

However, we can re-assign the name `x` to the newly created string if we want:

```python
>>> x = x.lower()
>>> x
'hello!'
```

The built-in `dir` function lists all methods associated with an object. Therefore, if we want to find out which string methods are available, we call `dir` and pass a string object as the argument:

```python
>>> dir(x)   # x was defined in the previous example and is a string object
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```

This is quite some list. However, we can ignore all names starting and ending with two underscores (for example, `__add__`, `__class__`, and so on). These so-called "dunder" methods are reserved for internal use.

When using IPython, there is a nicer way to get a list of available methods: if you type `x.` and then hit the <kbd>Tab</kbd> key, IPython will show a popup containing all available methods (and it will automatically hide all dunder methods). This makes it especially easy to explore what's available, because after selecting a method we can display its documentation with the `?`, for example `x.upper?`.

In addition to `upper` and `lower`, other case-changing methods are `capitalize`, `casefold`, `swapcase`, and `title`.

The `strip` method is particularly useful to remove leading and trailing whitespace (which is often used for sanitizing strings):

```python
>>> s = "      This is an example.                "
>>> s.strip()
'This is an example.'
```

The `split` method splits a string into a list of shorter strings. By default, `split` splits on [whitespace](https://en.wikipedia.org/wiki/Whitespace_character), which is a nice way to partition a string into words (we will learn about lists in the upcoming chapter):

```python
>>> s = "This is an example."
>>> s.split()
['This', 'is', 'an', 'example.']
```

Note that `split` accepts a `sep` argument, which defines the delimiter used to split the string. We could split by periods:

```python
>>> s = "Today is Sunday. It is sunny. It is not raining."
>>> s.split(".")
['Today is Sunday', ' It is sunny', ' It is not raining', '']
```

Note how the separator is not part of any substring in the resulting list.

The opposite of `split` is `join`. Given a list of strings, we can create a single string by joining all elements in the list.

```python
>>> ";".join(["one", "two", "three"])
'one;two;three'
```

This might look a bit weird, but we are calling the `join` method on the string `";"`, which means that Python creates a new string by joining the list elements with the `";"` character.

The string does not have to be a single character:

```python
>>> " --> ".join(["one", "two", "three"])
'one --> two --> three'
```

Sometimes, it is useful to count or find specific characters in a string. This is where the `count` and `find` methods come in handy. Suppose we have the following string `s`:

```python
>>> s = "pneumonoultramicroscopicsilicovolcanoconiosis"
```

Say we want to know how many `"i"` characters it contains:

```python
>>> s.count("i")
6
```

We can find the index of the first `"i"`:

```python
>>> s.find("i")
14
>>> s[14]
'i'
```

Note that `s[14]` refers to the fifteenth letter. The method accepts an optional `start` argument, which denotes where to start the search:

```python
>>> s.find("i", 15)  # the next "i"
22
```

### Iterating over strings
The `in` keyword checks whether a certain string is contained in another string:

```python
>>> s = "computer"
>>> "mpu" in s
True
>>> "y" in s
False
```

A for-loop can directly iterate over a string as follows:

```python
>>> for c in s:
...     print(c, end=".")
...
c.o.m.p.u.t.e.r.
```

We could also use a while-loop, but this tends to be more cumbersome (and less Pythonic):

```python
i = 0

while i < len(s):
    print(s[i])
    i += 1
```
```
c
o
m
p
u
t
e
r
```

We can now combine what we learned about functions, loops, conditions, and strings to mimic the `find` and `count` methods. Note that in general it is never a good idea to ignore built-in functions and methods and roll a custom implementation, but we do it for didactic purposes.

Remember that the `find` method finds a substring in a string and returns the index of the first match. If it does not find the substring, it returns `-1`.

Here's a function that implements the behavior of the `find` method (provided that the substring is only a single character):

```python
def find(s, sub):
    i = 0
    while i < len(s):
        if s[i] == sub:
            return i  # found it
        i += 1
    return -1  # no match
```

Similarly, here's a custom function which replicates the `count` method:

```python
def count(s, sub):
    i = 0
    for c in s:
        if c == sub:  # found it
            i += 1  # increment our counter
    return i
```

Exercises
---------
1. Write a function called `reverse`, which takes a string and returns a reversed version of that string.

2. Assume we have the following string `s = "educational neuroscience"`. Which method creates a new string where each word starts with an uppercase letter?

3. Assume we have the following string `s = "Edukational Neuroscience"`. How can we replace the `"k"` with a `"c"` and create a new string with the correct spelling from the given string?

4. A palindrome is a word or a sentence which reads the same forwards and backwards, for example "madam" or "Was it a car or a cat I saw?". Write a function `is_palindrome`, which returns `True` if a given string is a palindrome (or `False` if not). It is helpful to convert all characters to lowercase as a first step inside the function. Furthermore, whitespace and punctuation needs to be ignored if the function also needs to work with sentences.


---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by [Clemens Brunner](https://cbrnr.github.io/).