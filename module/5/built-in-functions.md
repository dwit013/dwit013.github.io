---
layout: page
---

## Module 5

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Functions

A function is a block of code which runs when the function is called. Functions are reusable and perform a single, related action. Functions provide modularity for our code.

Functions take in data, known as parameters, and can return data as a result.

## 5.1 Built-in Functions

The Python interpreter has a number of functions and types built into it that are always available.

For a complete list of built-in functions and its use visit this [link](https://docs.python.org/3/library/functions.html).

Some popular built-in functions are as follows:

# enumerate(iterable, start=0)

Return an enumerate object. iterable must be a sequence, an iterator, or some other object which supports iteration. It returns a tuple containing a count (from start which defaults to 0) and the values obtained from iterating over iterable.

    >>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
    >>> list(enumerate(seasons))
    [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
    >>> list(enumerate(seasons, start=1))
    [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]

# input([prompt])

If the prompt argument is present, it is written to standard output without a trailing newline. The function then reads a line from input, converts it to a string (stripping a trailing newline), and returns that.

    >>> s = input('--> ')  
    --> My name is John.
    >>> s  
    "My name is John."

# len(s)

Return the length (the number of items) of an object. The argument may be a sequence (such as a string, bytes, tuple, list, or range) or a collection (such as a dictionary, set, or frozen set).

# sorted(iterable, *, key=None, reverse=False)

Return a new sorted list from the items in iterable.

Has two optional arguments which must be specified as keyword arguments.

key specifies a function of one argument that is used to extract a comparison key from each element in iterable (for example, key=str.lower). The default value is None (compare the elements directly).

reverse is a boolean value. If set to True, then the list elements are sorted as if each comparison were reversed.


<hr>
<a href="../../../module/4/for-loop-statement" style="float:left;"> &laquo; Prev </a>
<a href="../user-defined-functions" style="float:right;"> Next &raquo; </a>