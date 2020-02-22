Dictionaries
============
The last built-in data type we are going to cover is the dictionary (`dict`). Just like its name implies, a dictionary is a mapping data type, which maps keys to values. It works a little like a real-word English-German dictionary. Let's assume we wanted to look up the German translation of "cat". We'd flip through the pages until we found the entry for "cat". This entry would contain the German translation "Katze". In this example, "cat" is the key and "Katze" is its value. Therefore, a dictionary is a mapping from keys to values. A dictionary can contain many key-value pairs.

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



---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.