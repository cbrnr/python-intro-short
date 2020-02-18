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

Defining functions
------------------
We are not restricted to calling existing functions. In fact, we can create our own functions and they behave just like any regular built-in function. Here's how we define a function in Python conceptually (using pseudo-code):

```
def function_name(<arg1>, <arg2>, ...):
    <do something>
    ...
    <optionally return something>
```

A function definition starts with a function header introduced with the keyword `def`. We then specify the function name (keeping in mind the naming rules we've already discussed) followed by a pair of parenthesis. If our function requires additional information to do its job, we specify its parameters inside the parentheses (separated by commas). Each parameter gets its own name, and the function can use specific values of these parameters (called arguments) when it is called. Finally, the function header needs to be concluded with a `:`.

Next, we indent all lines that belong to the function body. That way, Python knows which lines to execute when we call the function. A function body can consist of one or several lines of code. Optionally, a function can return a value, for example the result of a computation. This return value can be evaluated and used by Python just like any expression.

### Example 1
Let's review some examples for simple functions. The following function is named `test1`, takes no arguments, and consists of two lines of code. When called, the function internally assigns the name `s` to the string `"Hello World!"`, which it then prints to the screen. This function does not return a value.

```python
>>> def test1():
...    s = "Hello world!"
...    print(s)
```

The prompt changes from `>>>` to `...` after the function header, because Python knows that the function definition is incomplete. As with the regular prompt, do not type the `...` prompt when you define this function in the interactive interpreter. If you copy these lines to a script, also make sure not to include the prompts.

Notice that running these three lines of code in Python does *not* actually *run* the function &ndash; they *define* the function so that Python now knows that a function `test1` exists. We have to *call* this function in order to run it:

```python
>>> test1()
Hello world!
```

### Example 2
Let's modify this function so that it returns a value. Here's our new function `test2`:

```python
>>> def test2():
...    s = "Hello world!"
...    return s
```

This function contains a `return` statement, which in this case means that the function returns `s` (which is equal to the string `"Hello world!"`) to the caller. After defining this function, we can call it:

```python
>>> test2()
'Hello world!'
```

Since we are using Python in interactive mode, the returned value is automatically printed on the screen. However, we can now use the returned value by assigning a name:

```python
>>> h = test2()
```

Now the result of calling `test2` (its return value) is accessible with the name `h`, which refers to the string `'Hello world!'`:

```python
>>> h
'Hello world!'
>>> type(h)
str
```

### Example 3
Let's define an even more sophisticated function, this time we want to have two parameters. The function should return the sum of these two parameters, which is why we will call our function `add` (instead of `test3`):

```python
>>> def add(x, y):
...    return x + y
```

Once the `add` function is defined, we can call it with two arguments:

```python
>>> add(3, 7)
10
```

When the function is called, the arguments (the concrete values `3` and `7`) are used in place of the parameters `x` and `y` inside the function body. That's why the function returns `3 + 7` (evaluating to `10`) in this example.

Notice that we need to supply exactly two arguments when we call `add`. If we don't, Python will throw an error:

```python
>>> add(5)
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-2-e1d21b2822df> in <module>
----> 1 add(5)

TypeError: add() missing 1 required positional argument: 'y'
```

Because this function returns a value, we already know that whenever Python sees a function call like `add(5, 5)` it will evaluate/replace this expression with its return value `10`. Using this knowledge, we can compose more complicated expressions as follows:

```python
>>> add(add(2, add(5, 7)), 9)
23
```

Working inside out, Python replaces each function call with its concrete returned value until the result cannot be further reduced. Here's a breakdown of the steps involved in the previous example:

```python
>>> add(add(2, add(5, 7)), 9)  # add(5, 7) is evaluated to 12
>>> add(add(2, 12), 9)  # add(2, 12) is evaluated to 14
>>> add(14, 9)  # add(14, 9) is evaluated to 23
23
```

Of course, we can also assign a name to the returned value if we want to use it in some subsequent step:

```python
>>> a = add(add(2, add(5, 7)), 9)
>>> a - 20
3
```


---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.