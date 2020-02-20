Loops
=====
It is often necessary to repeat statements a certain number of times. For example, let's assume that we wanted to print "Hello!" five times. Rather naively, we could write this simply as:

```python
print("Hello")
print("Hello")
print("Hello")
print("Hello")
print("Hello")
```

Although this does the job, it is really cumbersome to repeat the same line of code multiple times. Furthermore, imagine we made a mistake and we really wanted to print "Bye" instead of "Hello" &ndash; we'd have to change our code in five different locations.

for-loops
---------
Luckily, Python features loops, which enable us to perform repeated actions. Like functions and conditions, loops also let us control the program flow. Our previous example could be written with a loop as follows:

```python
for i in range(5):
    print("Hello")
```

This is obviously much shorter than writing out each repetition manually (even more so if the loop involves more iterations). Furthermore, if we want to make changes, we only need to do it once inside the body of the loop.

Let's analyze the structure of a for-loop in Python. The first part should look familiar: just like functions and conditions, for-loops start with a header. This time, the header is introduced by the `for` keyword. Next, the loop header defines a name (`i` in our case), which gets all values of a sequence-like object, which is specified last (`range(5)` in the example). In each iteration of the loop, the name `i` gets a value of the sequence we are iterating over. We will see how `range(5)` works in a moment. A colon concludes the loop header.

The indented part after the header forms the body of the loop. This code block is what is actually repeated (in our example, `print("Hello")` is repeatedly called five times).

We can further inspect what's going on by printing the name `i` inside the loop:

```python
for i in range(5):
    print(i)
```

This yields the following output:
```
0
1
2
3
4
```

Alright, so `range(5)` produces a sequence of 5 numbers, starting at 0 and ending with 4. The loop iterates over all elements of this sequence until it is exhausted, after which the loop stops. In each iteration of the loop, `i` contains the i-th element of the sequence, and this particular value is used when running the body of the loop.

As a sidenote, `range` can also be called with two arguments, which are then interpreted as start and stop values of the created range. However, the stop value does not belong to the sequence anymore (this is because the difference between stop and start gives the number of elements):

```python
>>> list(range(2, 8))  # 8 - 2 = 6 values (from 2 to 7)
[2, 3, 4, 5, 6, 7]
```

Note that we have to use `list` in order to see all the elements that `range` creates at once (more on lists soon).

A loop can iterate not only over `range`, but over any sequence-like object (or rather, over any collection, which is a data type that can contain more than one elements). We will learn more about three widely-used container types (strings, lists, and dictionaries) in the next chapters. Here's a short preview of what a loop can do. First, we can iterate over a string:

```python
for s in "Hello World!":
    print(s)
```

Here, `s` sequentially gets all characters of the string `"Hello World!"` as the loop iterates. That is, in the first iteration `s` contains the character `"H"`, in the second `"e"`, and so on. The `print` function is called in each iteration with the single characters as arguments, so the output looks like this (the `print` function automatically inserts a newline at the end, though this can be changed with its `end` parameter):

```
H
e
l
l
o

W
o
r
l
d
!
```

A list is another popular sequence-like data type that can contain elements of arbitrary types (more on this later). We can iterate over a list like this:

```python
a = ["Hello", "world!", "I", "love", "Python!"]

for element in a:
    print(element)
```

The output is:
```
Hello
world!
I
love
Python!
```

### Breaking and continuing loops
Python lets as preemptively break out of a loop or jump to the next iteration from anywhere in the loop body using the `break` and `continue` keywords, respectively.

Sometimes, we want to stop a loop early, like in the following example that demonstrates how to search for a character within a string:

```python
i = 0

for c in "Seek and destroy":
    if c == "k":
        break
    i += 1

print(i)
```

This example searches for the first occurrence of the character `"k"` within the string `"Seek and destroy"`. If it finds it, the name `i` contains the position (index) of this character within the string (`3` in this example, because Python starts to count at zero). Notice that once we have found the character (`c == "k"`), we immediately break out of the loop (which means Python immediately jumps to the end of the loop, which is the `print(i)` function call). As we will see soon, `break` is especially useful in while-loops.

The next (somewhat silly) example demonstrates the use of the `continue` statement, which causes Python to immediately jump back to the loop header and begin the next iteration.

```python
for num in range(2, 10):
    if num % 2 == 0:
        print("Found an even number", num)
        continue
    print("Found an odd number", num)
```

This is the output:
```
Found an even number 2
Found an odd number 3
Found an even number 4
Found an odd number 5
Found an even number 6
Found an odd number 7
Found an even number 8
Found an odd number 9
```

while-loops
-----------
In addition to for-loops, Python also supports while-loops. In general, both loop types can be used interchangeably, but while-loops are especially useful when we want a loop that never stops (an infinite loop), or in cases where we don't know in advance how many iteration we are going to perform.

Here's our first for-loop example transformed to a while-loop:

```python
i = 0

while i < 5:
    print(i)
    i += 1
```

This produces the same output as its for-loop counterpart:
```
0
1
2
3
4
```

In this case, we would prefer the for-loop because it requires us to write only two lines of code as opposed to four lines for the while-loop.

However, while-loops are useful if we don't know the number of iterations, which is often the case when user input is involved. Consider the following example, which prompts the user to input a key and runs until the input equals the `"q"` character:

```python
while True:
    line = input("> (enter 'q' to quit) ")
    if line == "q":
        break
```

The while-loop makes this use case quite natural. Apparently, `while True` is always `True`, so the loop will go on forever. However, notice that there is a `break` statement inside the loop body, which will exit the loop immediately. This will only happen if the user input (stored in `line`) equals `"q"`.

Here's another fun little example which involves a (potentially) infinite while-loop. It also contains a condition with `if`, `elif`, and `else` blocks. The job of the user is to guess the value of `number` (which is 23 in this case, but we assume that the user doesn't know this value). If the guess is correct, we `break` out of the loop and the program is done. If the user's guess is incorrect, we give a hint and go to the next iteration.

```python
number = 23

while True:
    guess = int(input("Enter an integer: "))  # int converts the input into a number
    if guess == number:
        print("Congratulations, you guessed it.")
        break
    elif guess < number:
        print("No, it is a little higher than that.")
    else:
        print("No, it is a little lower than that.")
```

Exercises
---------
1. Iterate over the list `lst = ["I", "love", "Python"]` and in each iteration, `print` the current list element on the screen.

2. Iterate over the list `lst = ["I", "love", "Python"]` and in each iteration, use a second loop to iterate over the current string and `print` each character on the screen followed by a `-`. Use the `end="-"` argument in `print` to get the desired output, which should look like this: `I-l-o-v-e-P-y-t-h-o-n-`.

3. Iterate over the list `[1, 13, 25, -11, 17, 24, 9, -1, 2, 3]` until you encounter the first even number. Once you find this number, break out of the loop and print the number on the screen. Since we have not learned about lists yet, use a for-loop to solve this problem (we could also use a while-loop, but we need to know more about lists before we can do so).

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.