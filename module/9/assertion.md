---
layout: page
---

# Module 9

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

# Debugging

## 9.2 Assertion

An assertion is a sanity check to make sure your code isn’t doing something obviously wrong. These sanity checks are performed by `assert` statements. If the sanity check fails, then an `AssertionError` exception is raised. In code, an `assert` statement consists of the following:

*   The `assert` keyword
    
*   A condition (that is, an expression that evaluates to `True` or `False`)
    
*   A comma
    
*   A string to display when the condition is `False`
    
For example, enter the following into the interactive shell:

```python
>>> assert sum([1, 2, 3]) == 6, "Should be 6"
>>> assert sum([1, 2, 2]) == 6, "Should be 6"
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AssertionError: Should be 6
```

In plain English, an `assert` statement says, “I assert that this condition holds true, and if not, there is a bug somewhere in the program.” Unlike exceptions, your code should _not_ handle `assert` statements with `try` and `except`; if an `assert` fails, your program _should_ crash. 

By failing fast like this, you shorten the time between the original cause of the bug and when you first notice the bug. This will reduce the amount of code you will have to check before finding the code that’s causing the bug.

Assertions are for programmer errors, not user errors. For errors that can be recovered from (such as a file not being found or the user entering invalid data), raise an exception instead of detecting it with an `assert` statement.

<hr>
<a href="../exceptions" style="float:left;"> &laquo; Prev </a>
<a href="../logging" style="float:right;"> Next &raquo; </a>