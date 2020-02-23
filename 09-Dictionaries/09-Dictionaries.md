Dictionaries
============
The last built-in data type we are going to cover is the dictionary (`dict`). Just like its name implies, a dictionary is a mapping data type, which maps keys to values. It works a little like a real-word English-German dictionary. Let's assume we wanted to look up the German translation of "cat". We'd flip through the pages until we found the entry for "cat". This entry would contain the German translation "Katze". In this example, "cat" is the key and "Katze" is its value. Therefore, a dictionary is a mapping from keys to values. A dictionary can contain many key-value pairs.

Creating dictionaries
---------------------
Here's how we define a `dict` in Python. We use curly braces to create a dict, and we supply a comma-separated list of key-value pairs inside the braces. The key-value pairs are separated by colons. Let's see an example:

```python
>>> d = {"house": "Haus", "cat": "Katze", "snake": "Schlange"}
```

Alternatively, we can also use the `dict` function and create key-value pairs with keyword arguments:

```python
>>> d = dict(house="Haus", cat="Katze", snake="Schlange")
```

Note that in the second version, dictionary keys need to be valid Python names, whereas the first version is more flexible. For example, we can use an `int` as a key, but only when we use curly bracket notation:

```python
>>> {1: "one", 2: "two"}
{1: 'one', 2: 'two'}
```

In this case, `dict` raises a syntax error:

```python
>>> dict(1="one", 2="two")
  File "<stdin>", line 1
SyntaxError: expression cannot contain assignment, perhaps you meant "=="?
```

Just like in lists and strings, Python uses square brackets to access individual elements in the dict. However, because dictionary entries are not ordered by an integer index starting at zero, we use its keys to retrieve their corresponding values. Let's demonstrate this using the example dictionary from before:

```python
>>> d["cat"]
'Katze'
>>> d["house"]
'Haus'
```

When we use a key that does not exist in the dictionary, Python raises an error:

```python
>>> d["dog"]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'dog'
```

Dictionaries are mutable, which mean that we can modify existing dictionary entries.

```python
>>> d["snake"] = "Python"
>>> d
{'house': 'Haus', 'cat': 'Katze', 'snake': 'Python'}
```

We can add new entries simply by assigning a value to a new key using square bracket notation:

```python
>>> d["bug"] = "Wanze"
>>> d
{'house': 'Haus', 'cat': 'Katze', 'snake': 'Python', 'bug': 'Wanze'}
```

Again, order is irrelevant in dictionaries. There is no first, second or last item in a dictionary &ndash; values can only access by their key.

So far, we have only used strings as dictionary keys. However, we can actually use any *immutable* data type as a key, including integers, floats, and tuples. Importantly, we cannot use lists as keys because lists are mutable. This restriction does not apply to dictionary values, which can be mutable or immutable objects.

```python
>>> x = {13: "A", "c": 2.22, (0, 1): [1, 2, 3]}
>>> x
{13: 'A', 'c': 2.22, (0, 1): [1, 2, 3]}
>>> x[[4, 5, 6]] = "X"  # try to add new entry with mutable key (list)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
```

The previous assignment demonstrates what happens when we try to create a dictionary entry with a list as a key: we get a `TypeError` (note that the error message says that the type is *unhashable* &ndash; for most purposes, unhashable means mutable although technically these are different concepts).

Working with dictionaries
-------------------------
As expected, we can use the `len` function to inspect the number of entries in a dictionary:

```python
>>> d = {"house": "Haus", "cat": "Katze", "snake": "Schlange"}
>>> len(d)
3
```

Notice that an entry is a key/value pair. We can get the keys or values separately by calling the `keys` and `values` methods, respectively:

```python
>>> d.keys()
dict_keys(['house', 'cat', 'snake'])
>>> d.values()
dict_values(['Haus', 'Katze', 'Schlange'])
```

These methods return list-like objects.

Using the `in` operator we can check if the dictionary contains a specific *key*:

```python
>>> "cat" in d
True
>>> "Katze" in d
False
```

If we want to check for a specific value, we can perform our query in `d.values()` instead:

```python
>>> "cat" in d.values()
False
>>> "Katze" in d.values()
True
```

Iterating over dictionaries
---------------------------
Dictionaries are iterable, and if we create a for-loop over a dict, we actually loop over its keys:

```python
>>> for key in d:
...     print(key)
...
house
cat
snake
```

Using the current key in each iteration, we can access the corresponding value via indexing:

```python
>>> for key in d:
...     print(key, ":", d[key])
...
house : Haus
cat : Katze
snake : Schlange
```

Of course we could also iterate over `d.values()` specifically, but often it is necessary to iterate over both keys and values simultaneously. The dict method `items` returns key/value pairs as tuples:

```python
>>> d.items()
dict_items([('house', 'Haus'), ('cat', 'Katze'), ('snake', 'Schlange')])
```

We can use this list-like sequence of tuples in our for-loop, which means that we get a tuple in each iteration. However, instead of assigning one name to the tuple, we can unpack its two components into two distinct names (this is called tuple unpacking):

```python
>>> for key, value in d.items():
...    print(key, ":", value)
...
house : Haus
cat : Katze
snake : Schlange
```

Here's another example of tuple unpacking:

```python
>>> a, b = 12, 13
>>> a
12
>>> b
13
```

The tuple `12, 13` on the right-hand side contains two elements. On the left-hand side we assign two names, one for each tuple component (the tuple components are unpacked into separate names). That way, the canonical way to swap values of two different names in Python is very short and sweet:

```python
>>> a, b = b, a
```

This swaps the values of `a` and `b`, which we can confirm by printing their values:

```python
>>> a, b
>>> a
13
>>> b
12
```

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.