---
layout: page
---

## Module 5

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Functions

A function is a block of code which runs when the function is called. Functions are reusable and perform a single, related action. Functions provide modularity for our code.

Functions take in data, known as parameters, and can return data as a result.

## 5.2 User-defined Functions

Python has many built-in functions but we can create our own functions, known as built-in functions.

In Python a function is defined using the (`def`) keyword.

    def function_name (parameters):
        "function_docstring"
        code_block
        return [expression]

The above syntax follows the following rules:

* Function is defined using (`def`) keyword followed by function name and parantheses.
* The parantheses contain a single parameter, multiple parameters or none at all.
* The parantheses are followed by colon (:)
* The block of code inside the function is indented.
* The statement (`return [expression]`) exits a function, optionally passing back an expression to the caller. A return statement with no arguments is the same as return None.

Example

    >>> def add(a, b):
            "This function adds two numbers."
            result = a + b
            return result
    ...
    >>> print(add(1, 2))
    3

A function must be called in order to execute its action.

# Passing Argument Values

There are multiple ways of passing argument values when calling a function.

# Required Arguments

Required arguments are passed in correct positonal order.

Example

    >>> def print_name(name):
            print (name)
            return
    ...
    >>> print_name("John")
    John

# Keyword Arguments

When you use keyword arguments in a function call, the caller identifies the arguments by the parameter name. This allows you to skip arguments or place them out of order because the Python interpreter is able to use the keywords provided to match the values with parameters. 

Example

    >>> def person_details(name, age):
            print ("Name: ", name)
            print ("Age: ", age)
            return 
    ...
    >>> person_details(age=20, name="Jane")
    Name: Jane
    Age: 20

# Default Parameter Value

We can define a default parameter value for a function. If the function is called without any parameter value, then the default value will be used.

Example

    >>> def increment(value = 1):
            return value + 1
    ...
    >>> increment()
    2
    >>> increment(5)
    6

# Variable-length Arguments

Variable-length arguments allow us pass more number of arguments than specified.

Example

    >>> def print_all(*args):
            for var in args:
                pritn var
            return
    ...
    >>> print_all(1, "Two", 3, 4, 5.0)
    1
    Two
    3
    4
    5.0


<hr>
<a href="../built-in-functions" style="float:left;"> &laquo; Prev </a>
<a href="../anonymous-function" style="float:right;"> Next &raquo; </a>