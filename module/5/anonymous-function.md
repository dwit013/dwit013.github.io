---
layout: page
---

## Module 5

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## 5.3 Anonymous Functions

Anonymous functions do not have a function name. They are not declared in the traditional way using (`def`) keyword but instead (`lambda`) keyword is used. 

    lambda arguments: expression

This small anonymous function is called a lambda function. It can take any number of arguments, but can have only one expression. Executing a lambda function evaluates its expression and then automatically returns its result. So there’s always an implicit return statement. It is also known as single expression functions.

Example

    >>> sum = lambda arg1, arg2: arg1 + arg2
    >>> sum(1, 2)

# Some use cases of Lambda function

    >>> (lambda x, y: x + y)(5, 3)
    8

    >>> sorted(range(-5, 6), key=lambda x: x ** 2)
    [0, -1, 1, -2, 2, -3, 3, -4, 4, -5, 5]

Lambdas are also used as lexical closures, a function that remembers the values from the enclosing lexical scope even when the program flow is no longer in that scope.

    >>> def make_adder(n):
    ...     return lambda x: x + n

    >>> plus_3 = make_adder(3)
    >>> plus_5 = make_adder(5)

    >>> plus_3(4)
    7
    >>> plus_5(4)
    9

In the above example the x + n lambda can still access the value of n even though it was defined in the make_adder function (the enclosing scope).

# Map, Filter and Reduce

Lambda functions can be used along with built-in functions like filter(), map() and reduce(). These are three functions which facilitate a functional approach to programming.

# Map

Map applies a function to all the items in an input_list. 

    map(function_to_apply, list_of_inputs)

Example

(Without using map)

    >>> items = [1, 2, 3, 4, 5]
    >>> squared = []
    >>> for i in items:
            squared.append(i**2)
    
(Using map)

    >>> items = [1, 2, 3, 4, 5]
    >>> squared = list(map(lambda x: x**2, items))

# Filter

Filter creates a list of elements for which a function returns true.

    number_list = range(-5, 5)
    less_than_zero = list(filter(lambda x: x < 0, number_list))
    print(less_than_zero)

The filter resembles a for loop but it is a builtin function and faster.

# Reduce

Reduce is a really useful function for performing some computation on a list and returning the result. It applies a rolling computation to sequential pairs of values in a list. 

Example

(Without using Reduce)

    >>> product = 1
    >>> list = [1, 2, 3, 4]
    >>> for num in list:
            product = product * num
    
(Using Reduce)

    >>> from functools import reduce
    >>> product = reduce((lambda x, y: x * y), [1, 2, 3, 4])


<hr>
<a href="../user-defined-functions" style="float:left;"> &laquo; Prev </a>
<a href="/" style="float:right;"> Next &raquo; </a>