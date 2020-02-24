Input and Output
================
We will now delve into simple input and output (I/O) operations, which includes activities such as getting input from the keyboard, reading text files, string formatting, and writing data to text files.

We will start with string formatting.

String formatting
-----------------
We are already familiar with the built-in `print` function. If we pass it an argument, the function will write this argument on the screen (more technically, it will write to standard output):

```python
>>> print("Hello")
Hello
```

The argument does not have to be a string, because `print` also works with numeric types:

```python
>>> print(55)
55
```

In fact, `print` accepts an arbitrary number of arguments:

```python
>>> print("Hello", "world", "this", "is", 2020)
Hello world this is 2020
```

When there is more than one argument, `print` automatically creates a space to separate the arguments in the output. We can use the `sep` parameter to change this default argument from `" "` to any string we want. For example, we could set `sep` to an empty string:

```python
>>> print("Hello", "world", "this", "is", 2020, sep="")
Helloworldthisis2020
```

Strings are perfectly suited for outputting information either to the screen or to a file (because strings can contain arbitrary characters including numbers). Therefore, we can use the `str` function to convert arbitrary data types to strings:

```python
>>> str(55)
'55'
```

When writing a script, we often want to output information such as the result of a calculation. Suppose we compute the sum of two numbers `a` and `b`, and we would like to print the result in a nicely formatted way. Here's one option using multiple arguments for the `print` function:

```python
>>> a = 5
>>> b = 10
>>> print(a, "+", b, "=", a + b)
5 + 10 = 15
```

Alternatively, we could build our desired output string and pass that as the sole argument to `print` (remember that `+` concatenates strings):

```python
>>> print(str(a) + " + " + str(b) + " = " + str(a + b))
5 + 10 = 15
```

Notice that we must take care of whitespace ourselves, because the `print` function with one argument just outputs this argument.


---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.