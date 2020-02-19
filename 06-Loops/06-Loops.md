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

---
![https://creativecommons.org/licenses/by-nc-sa/4.0/](cc_license.png) This document is licensed under the [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) by Clemens Brunner.