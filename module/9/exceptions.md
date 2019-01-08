---
layout: page
---

# Module 9

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

# Debugging

Debugging is a process of identifying and removing errors from the program.

Python provides a few tools and techniques to identify what exactly your code is doing and where it's going wrong.

## 9.1 Exceptions

An exception is an event, which occurs during the execution of a program, that disrupts the normal flow of the program's instructions.

The term exception is, in fact, short form for the phrase "exceptional event."

### Exception Handling

Exception handling is the process responding to the occurrence of exceptions. In Python, if we do not handle the exception, or when we get an error, the program crashes. For a real-world application, this is not desired behavior. Instead, a mechanism must be built to detect errors, handle them, and then continue to run.

A simple example is "divide-by-zero" error. Write the following code and save it as `division_error.py`.

```python
def divideBy(num):
  return 21/num

print(divideBy(2))
print(divideBy(7))
print(divideBy(0))
print(divideBy(1))
```

The output of this code will be as follows:

```python
11.5
3.0
Traceback (most recent call last):
  File "C:/division_error.py", line 6, in <module>
    print(divideBy(0))
  File "C:/division_error.py", line 2, in divideBy
    return 21 / num
ZeroDivisionError: division by zero
```

Here, a ZeroDivisionError happens as you tried to divide a number by zero.

#### try ... except statement

In Python, errors such as above can be handled with `try` and `except` statements. The code that could potentially cause an error is put in **try block** and in case of an error we define what should be done in the **except block**.

Syntax:

```
try:
  statement/s
except errorType:
  statement/s
```
Example

```python
def divideBy(num):
  try:
    return 21/num
  except ZeroDivisionError:
    print('Error: Invalid argument.')

print(divideBy(2))
print(divideBy(7))
print(divideBy(0))
print(divideBy(1))
```

Output

```
11.5
3.0
Error: Invalid argument.
None
21.0
```
#### List of Python built-in exceptions

<table>
    <thead>
        <th>Exception</th>
        <th>Cause of Error</th>
    </thead>
    <tbody>
        <tr>
            <td>AssertionError </td>
            <td>Raised when assert statement fails.</td>
        </tr>
        <tr>
            <td>AttributeError </td>
            <td>Raised when attribute assignment or reference fails.</td>
        </tr>
        <tr>
            <td>EOFError </td>
            <td>Raised when the input() functions hits end-of-file condition.</td>
        </tr>
        <tr>
            <td>FloatingPointError </td>
            <td>Raised when a floating point operation fails.</td>
        </tr>
        <tr>
            <td>GeneratorExit </td>
            <td>Raise when a generator's close() method is called.</td>
        </tr>
        <tr>
            <td>ImportError </td>
            <td>Raised when the imported module is not found.</td>
        </tr>
        <tr>
            <td>IndexError </td>
            <td>Raised when index of a sequence is out of range.</td>
        </tr>
        <tr>
            <td>KeyError </td>
            <td>Raised when a key is not found in a dictionary.</td>
        </tr>
        <tr>
            <td>KeyboardInterrupt </td>
            <td>Raised when the user hits interrupt key (Ctrl+c or delete).</td>
        </tr>
        <tr>
            <td>MemoryError </td>
            <td>Raised when an operation runs out of memory.</td>
        </tr>
        <tr>
            <td>NameError </td>
            <td>Raised when a variable is not found in local or global scope.</td>
        </tr>
        <tr>
            <td>NotImplementedError </td>
            <td>Raised by abstract methods.</td>
        </tr>
        <tr>
            <td>OSError </td>
            <td>Raised when system operation causes system related error.</td>
        </tr>
        <tr>
            <td>OverflowError </td>
            <td>Raised when result of an arithmetic operation is too large to be represented.</td>
        </tr>
        <tr>
            <td>ReferenceError </td>
            <td>Raised when a weak reference proxy is used to access a garbage collected referent.</td>
        </tr>
        <tr>
            <td>RuntimeError </td>
            <td>Raised when an error does not fall under any other category.</td>
        </tr>
        <tr>
            <td>StopIteration </td>
            <td>Raised by next() function to indicate that there is no further item to be returned by iterator.</td>
        </tr>
        <tr>
            <td>SyntaxError </td>
            <td>Raised by parser when syntax error is encountered.</td>
        </tr>
        <tr>
            <td>IndentationError </td>
            <td>Raised when there is incorrect indentation.</td>
        </tr>
        <tr>
            <td>TabError </td>
            <td>Raised when indentation consists of inconsistent tabs and spaces.</td>
        </tr>
        <tr>
            <td>SystemError </td>
            <td>Raised when interpreter detects internal error.</td>
        </tr>
        <tr>
            <td>SystemExit </td>
            <td>Raised by sys.exit() function.</td>
        </tr>
        <tr>
            <td>TypeError </td>
            <td>Raised when a function or operation is applied to an object of incorrect type.</td>
        </tr>
        <tr>
            <td>UnboundLocalError </td>
            <td>Raised when a reference is made to a local variable in a function or method, but no value has been bound to that variable.</td>
        </tr>
        <tr>
            <td>UnicodeError </td>
            <td>Raised when a Unicode-related encoding or decoding error occurs.</td>
        </tr>
        <tr>
            <td>UnicodeEncodeError </td>
            <td>Raised when a Unicode-related error occurs during encoding.</td>
        </tr>
        <tr>
            <td>UnicodeDecodeError </td>
            <td>Raised when a Unicode-related error occurs during decoding.</td>
        </tr>
        <tr>
            <td>UnicodeTranslateError </td>
            <td>Raised when a Unicode-related error occurs during translating.</td>
        </tr>
        <tr>
            <td>ValueError </td>
            <td>Raised when a function gets argument of correct type but improper value.</td>
        </tr>
        <tr>
            <td>ZeroDivisionError </td>
            <td>Raised when second operand of division or modulo operation is zero.</td>
        </tr>
    </tbody>
</table>

### Raising Exceptions

We saw above that Python raises an exception whenever it tries to execute invalid code. But, we can also raise your own exceptions in your code. 

Raising an exception is a way of saying, “Stop running the code in this function and move the program execution to the `except` statement.”

Exceptions are raised with a `raise` statement. In code, a `raise` statement consists of the following:

*   The `raise` keyword
    
*   A call to the `Exception()` function
    
*   A string with a helpful error message passed to the `Exception()` function
    
Try the following in the interactive shell:

```python
>>> raise Exception('This is the error message.')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
    raise Exception('This is the error message.')
Exception: This is the error message.
```

If there are no `try` and `except` statements covering the `raise` statement that raised the exception, the program simply crashes and displays the exception’s error message.

Often it’s the code that calls the function, not the function itself, that knows how to handle an exception. So you will commonly see a `raise` statement inside a function and the `try` and `except` statements in the code calling the function. 

For example, enter the following code and save the program as _areaCalculator.py_:

```python
def calculateArea(width, height):
    if width <= 2:
        raise Exception('Width must be greater than 2.')
    if height <= 2:
        raise Exception('Height must be greater than 2.')
    
try:
    calculateArea(2, 1)
except Exception as err:
    print('An exception happened: ' + str(err))
```

This program uses the `except Exception as err` form of the `except` statement. If an `Exception` object is returned from `calculateArea()`, this `except` statement will store it in a variable named `err`. The `Exception` object can then be converted to a string by passing it to `str()` to produce a user-friendly error message.

Using the `try` and `except` statements, you can handle errors more gracefully instead of letting the entire program crash.

### Getting the Traceback as a String

When Python encounters an error, it produces a treasure trove of error information called the _traceback_. The traceback includes the error message, the line number of the line that caused the error, and the sequence of the function calls that led to the error. This sequence of calls is called the _call stack_.

Open a new file editor window in IDLE, enter the following program, and save it as _errorExample.py_:

```python
def spam():
    bacon()
def bacon():
    raise Exception('This is the error message.')

spam()
```

When you run _errorExample.py_, the output will look like this:

```python
Traceback (most recent call last):
  File "errorExample.py", line 7, in <module>
    spam()
  File "errorExample.py", line 2, in spam
    bacon()
  File "errorExample.py", line 5, in bacon
    raise Exception('This is the error message.')
Exception: This is the error message.
```

From the traceback, you can see that the error happened on line 5, in the `bacon()` function. This particular call to `bacon()` came from line 2, in the `spam()` function, which in turn was called on line 7. In programs where functions can be called from multiple places, the call stack can help you determine which call led to the error.

The traceback is displayed by Python whenever a raised exception goes unhandled. But you can also obtain it as a string by calling `traceback.format_exc()`. This function is useful if you want the information from an exception’s traceback but also want an `except` statement to gracefully handle the exception. You will need to import Python’s `traceback` module before calling this function.

For example, instead of crashing your program right when an exception occurs, you can write the traceback information to a log file and keep your program running. You can look at the log file later, when you’re ready to debug your program. Enter the following into the interactive shell:

```python
>>> import traceback
>>> try:
        raise Exception('This is the error message.')
    except:
         errorFile = open('errorInfo.txt', 'w')
         errorFile.write(traceback.format_exc())
         errorFile.close()
         print('The traceback info was written to errorInfo.txt.')

116
```

The traceback info was written to _errorInfo.txt_.

The `116` is the return value from the `write()` method, since 116 characters were written to the file. The traceback text was written to _errorInfo.txt_.

```python
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
Exception: This is the error message.
```

<hr>
<a href="../../../module/8/inheritance" style="float:left;"> &laquo; Prev </a>
<a href="../assertion" style="float:right;"> Next &raquo; </a>


