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

Of course, we can also assign a name to the returned value if we want to use it in a subsequent step:

```python
>>> a = add(add(2, add(5, 7)), 9)
>>> a - 20
3
```

Defining default arguments
--------------------------
Python functions have an extremely useful feature. When defining a function, parameters can get default values, so-called default arguments. This means that parameters with default values are optional when the function is called &ndash; values for these optional parameters do not need to be passed.

Here's our `add` function definition from before, but this time the second parameter gets a default value:

```python
>>> def add(x, y=1):
...    return x + y
```

Now we can call `add` with just one argument (`x`), because if we do not supply a value for `y` Python will use its default value of `1`:

```python
>>> add(5)
6
```

Note that we can still call the function with two arguments if we want to override the default value for `y`:

```python
>>> add(5, 3)
8
```

Calling with keyword arguments
------------------------------
Normally, Python assigns arguments passed in a function call by position. That is, if we call `add(5, 3)`, the first parameter `x` gets the value `5`, and the second parameter `y` gets the value `3`. Specifying arguments in a function call by position is referred to as *positional arguments*.

However, this can quickly get unwieldy if a function has many parameters. Consider the following function definition:

```python
>>> def many_args(a, b, c=0, d=1, e=0, f=5, g=5, h=0, i=-1):
...    pass
```

Parameters `a` and `b` are mandatory, whereas the remaining seven parameters have default values (and are therefore optional). Let's assume we want to call the function with arguments `a=10` and `b=5`, and we want only one of the remaining seven parameters to differ from their default value &ndash; say, we only want `h=-5`. Using positional arguments, we need to include arguments for parameters that we do not want to change:

```python
many_args(10, 5, 0, 1, 0, 5, 5, -5)
```

This is where *keyword arguments* come to the rescue. Whenever we call a function, we can always explicitly include the parameter name in addition to its specific value like this:

```python
many_args(a=10, b=5, h=-5)
```

That way, parameters that should use their default values do not need to be listed in the function call. In addition, keyword arguments make it obvious which arguments we are actually passing.

We can even mix positional and keyword arguments to optimize readability:

```python
many_args(10, 5, h=-5)
```

The first two arguments are matched by position, whereas the third argument is matched by name.


Function scopes
---------------


Exercises
---------
1. Define a function `add_one` which increments and returns the supplied argument (a number) by 1. Then evaluate the following expression:
   ```python
   >>> add_one(add_one(add_one(13)))
   ```
2. Define a function `mult` which multiplies its two input arguments and returns this product. The second parameter should have a default argument of `1` so that the function can also be called with only one argument. Test your function with the following three function calls:
   ```python
   >>> mult(3, 7)
   >>> mult(12)
   >>> mult(2, mult(8, 8))
   ```
3. Define a function `to_fahrenheit` which converts its argument (a temperature in degrees Celsius) into degrees Fahrenheit and returns this result. Furthermore, define another function `to_celsius` which performs the opposite conversion (from degrees Fahrenheit to degrees Celsius). Verify both functions with the following function calls (feel free to test additional temperature values):
   ```python
   >>> to_fahrenheit(0)
   >>> to_celsius(100)
   >>> to_celcius(to_fahrenheit(38))
   ```
4. Define a function `nonsense` that takes three arguments `a`, `b`, and `c`. Arguments `b` and `c` should be optional and default to `10` and `13`, respectively. The function should return the result of `a**2 - b * 2 + c**2`. Call the function in the following ways:

   - Without arguments
   - With three positional arguments
   - With two positional arguments
   - With one keyword argument
   - With two keyword arguments
   - With two positional and one keyword argument
   - With one positional and one keyword argument

   Write down each function call, each return value, and the values for each of the three arguments!

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.