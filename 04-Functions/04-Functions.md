Functions
=========
Functions encapsulate code, or in other words, functions group lines of code that belong together. They promote reusability and prevent code duplication. For example, if you need to perform repeated calculations consisting of several lines of code, this code might be outsourced into its own function. We will see examples of Python functions soon, but first we will discuss how to call and define functions.

Calling functions
-----------------
We have briefly mentioned that we call an existing function with its name followed by a pair of parentheses. Inside the parentheses a function can accept arguments, which are specific values we need to pass when we call the function.

For example, we already know two functions: `print` and `type`. Here's how we call these functions:

```python
>>> print("Hello")
Hello
>>> type("Hello")
str
```

Note that both functions are called with one argument (the string `"Hello"` in this case). However, we can also call some functions without any argument:

```python
>>> print()

```

No matter how many arguments a function takes, we need to supply the pair of parentheses in order to call the function.

Calling a function means that Python executes the lines of code belonging to the function. In the examples we've just shown, we don't know what lines of code get executed when we run the existing `print` or `type` functions. For all we care, this is not important as long as the functions do what they are supposed to do. This is what encapsulation actually means, a function encapsulates its code, and we can call a function without ever knowing what code it contains.

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.