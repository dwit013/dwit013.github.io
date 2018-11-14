---
layout: page
---

## Module 4

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Control Statements

## 4.3 For loop statement

The for loop in Python is used to iterate over a sequence (list, tuple, string) or other iterable objects. Iterating over a sequence is called traversal.

Syntax of for loop

    for val in sequence:
	    Body of for

Here, val is the variable that takes the value of the item inside the sequence on each iteration.

Loop continues until we reach the last item in the sequence. The body of for loop is separated from the rest of the code using indentation.

Examples

    >>> cities = ['Kathmandu', 'Lalitpur', 'Bhaktapur']
    >>> for city in cities:
            print(city)
    Kathmandu
    Lalitpur
    Bhaktapur

    >>> numbers_divisible_by_three = [3, 6, 9, 12, 15]
    >>> for num in numbers_divisible_by_three:
    ...     quotient = num / 3
    ...     print(f"{num} divided by 3 is {int(quotient)}.")
    ...
    3 divided by 3 is 1.
    6 divided by 3 is 2.
    9 divided by 3 is 3.
    12 divided by 3 is 4.
    15 divided by 3 is 5.

# for loop with dictionary

To loop all keys from a dictionary.

    for k in dict:
	    print(k)

To loop every key and value from a dictionary

    for k, v in dict.items():
	    print(k,v)

Example

    >>> country_capital = {
    ...     'Nepal'       : 'Kathmandu',
    ...     'India'       : 'New Delhi',
    ...     'China'       : 'Beijing'
    ... }
    >>> for country, capital in country_capital.items():
    ...     print(f"The capital of {country} is {capital}")
    ...
    The capital of Nepal is Kathmandu
    The capital of India is New Delhi
    The capital of China is Beijing

# range()

range() allows you to generate a series of numbers within a given range. 

<b>History of range()</b>

<em>
range() in Python 2 and range() in Python 3 are entirely different. range() in Python 3 is just a renamed version of a function that is called xrange in Python 2.
</em>
<em>
Originally, both range() and xrange() produced numbers that could be iterated over with for-loops, but the former generated a list of those numbers all at once while the latter produced numbers lazily, meaning numbers were returned one at a time as they were needed.
</em>
<em>
Having huge lists hang around takes up memory, so xrange() replaced range(), name and all.
</em>

Example

    for i in range(3, 16, 3):
        quotient = i / 3
        print(f"{i} divided by 3 is {int(quotient)}.")

There are three ways you can call range():

* range(stop) takes one argument.
* range(start, stop) takes two arguments.
* range(start, stop, step) takes three arguments.

range(stop)

When you call range() with one argument, you will get a series of numbers that starts at 0 and includes every whole number up to, but not including, the number you have provided as the stop.

Example

    >>> for i in range(3):
    ...     print(i)
    ...
    0
    1
    2

range(start, stop)

When you call range() with two arguments, you get to decide not only where the series of numbers stops but also where it starts, so you don’t have to start at 0 all the time. 

    >>> for i in range(1, 8):
    ...     print(i)
    ...
    1
    2
    3
    4
    5
    6
    7


range (start, stop, step)

When you call range() with three arguments, you can choose not only where the series of numbers will start and stop but also how big the difference will be between one number and the next. If you don’t provide a step, then range() will automatically behave as if the step is 1.

# Decrementing with range()

If your step is positive, then you move through a series of increasing numbers and are incrementing. If your step is negative, then you move through a series of decreasing numbers and are decrementing. 

    >>> for i in range(10, -6, -2):
    ...     print(i)
    ...
    10
    8
    6
    4
    2
    0
    -2
    -4


<hr>
<a href="../while-statement" style="float:left;"> &laquo; Prev </a>
<a href="/" style="float:right;"> Next &raquo; </a>