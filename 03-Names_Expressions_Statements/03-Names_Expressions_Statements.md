Names, expressions, statements
==============================
Objects, values, and types
--------------------------
In Python, everything is an object. Every object has a value and a type. For example, the number `1` we used in our arithmetic calculations is an object. It has the value `1` and is of type `int` (which means integer number). Here are a few examples that can be entered in the interactive interpreter:

```python
>>> 1
1
```

```python
>>> 2.15
2.15
```

```python
>>> "Hello world!"
'Hello world!'
```

```python
>>> '3'
'3'
```

As we already know, Python outputs the value of the last command automatically. That's why we know the value of the `1` object is `1`, and the value of the `"Hello world!"` object is `"Hello world!"`.

To find out the type of a given object, we can use the `type` function as follows:

```python
>>> type(1)
int
```

```python
>>> type(2.15)
float
```

```python
>>> type("Hello world!")
str
```

```python
>>> type('3')
str
```

Apparently, whole numbers are of type `int` (integer number), decimal numbers are `float` (floating point number), and character strings are `str` (string).

Graphically, we can think of an object as a Python entity of a specific type with a specific value:

![Python object](python_object.png)

Names
-----


---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.