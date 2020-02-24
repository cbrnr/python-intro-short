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

### f-strings
Constructing output strings like this quickly becomes cumbersome. Luckily, Python has a feature called f-strings that greatly facilitate this task. An f-string (formatted string) is a special way to define a string that may contain expressions (such as the names `a` and `b` from the previous example). Whenever Python encounters an expression enclosed in curly braces in an f-string, Python replaces that with its value. To define an f-string, we simple prepend `f` to the string literal:

```python
>>> f"This is an f-string"
'This is an f-string'
```

In this example, we don't really need an f-string, because a regular string could also do the job. However, we can now add an expression in the string, which Python will evaluate and replace in the result (note that we use the name `a` defined previously):

```python
>>> f"The first number is {a}."
'The first number is 5.'
```

We could write the example output from before in a more straightforward way:

```python
>>> print(f"{a} + {b} = {a + b}")
5 + 10 = 15
```

Sometimes, it is necessary to control the format of the evaluated expressions. For example, suppose we want to print the digits of $\pi$ with a precision of five decimal places. Let's see what we get if we print the following f-string:

```python
>>> import math
>>> print(f"The value of pi is approximately {math.pi}.")
The value of pi is approximately 3.141592653589793.
```

It seems like Python prints floating point numbers with 15 decimal places by default. We can change the format of the expressions inside the curly braces with a special [format specification mini-language](https://docs.python.org/3/library/string.html#format-specification-mini-language). In a nutshell, we can optionally append a `:` and the desired format after the expression. For example, we specify the precision of a floating point number to be five decimal places by appending `:.5f`:

```python
>>> print(f"The value of pi is approximately {math.pi:.5f}.")
The value of pi is approximately 3.14159.
```

Note that this doesn't change the value of `math.pi`, but only affects how this number is formatted in the output.

The format specification mini-language is very powerful. It is worth going through some examples to find out what it can do, so make sure to consult the documentation whenever you need a specific output format.

Reading text files
------------------


---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.