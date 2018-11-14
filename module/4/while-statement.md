---
layout: page
---

## Module 4

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Control Statements

## 4.2 While Statment

Iteration means executing the same block of code over and over, potentially many times. A programming structure that implements iteration is called a loop.

In programming, there are two types of iteration, indefinite and definite:

* With indefinite iteration, the number of times the loop is executed isn’t specified explicitly in advance. Rather, the designated block is executed repeatedly as long as some condition is met.

* With definite iteration, the number of times the designated block will be executed is specified explicitly at the time the loop starts.

# The while Loop

Simple form of while loop looks like:

    while <expr>:
        <statement(s)>

(`<statement(s)>`) represents the block to be repeatedly executed, often referred to as the body of the loop. This is denoted with indentation, just as in an if statement.

Example

    >>> n = 5
    >>> while n > 0:
    ...     n -= 1
    ...     print(n)
    ...
    4
    3
    2
    1
    0

When a while loop is encountered, (`<expr>`) is first evaluated in Boolean context. If it is true, the loop body is executed. Then (`<expr>`) is checked again, and if still true, the body is executed again. This continues until (`<expr>`) becomes false, at which point program execution proceeds to the first statement beyond the loop body.

# Looping through a list

Here’s a while loop involving a list, rather than a numeric comparison:

    >>> a = ['foo', 'bar', 'baz']
    >>> while a:
    ...     print(a.pop(-1))
    ...
    baz
    bar
    foo

# Interruption of Loop Iteration

Python provides two keywords that terminate a loop iteration prematurely:

* break immediately terminates a loop entirely. Program execution proceeds to the first statement following the loop body.
* continue immediately terminates the current loop iteration. Execution jumps to the top of the loop, and the controlling expression is re-evaluated to determine whether the loop will execute again or terminate.

The distinction between break and continue is demonstrated in the following diagram:

<img src="https://files.realpython.com/media/t.680f4db5c6a2.png" alt="Break vs Continue" width="auto" height="500px">
<em> Break vs Continue </em>

Break Example

>>> n = 5
>>> while n > 0:
...     n -= 1
...     if n == 2:
...         break
...     print(n)
...
4
3

Continue Example

>>> n = 5
>>> while n > 0:
...     n -= 1
...     if n == 2:
...         continue
...     print(n)
...
4
3
1
0

# The else Clause

Python allows an optional else clause at the end of a while loop. This is a unique feature of Python, not found in most other programming languages. The syntax is shown below:

    while <expr>:
        <statement(s)>
    else:
        <additional_statement(s)>

The (`<additional_statement(s)>`) specified in the else clause will be executed when the while loop terminates.

But, isn't this the same as following:

    while <expr>:
        <statement(s)>
    <additional_statement(s)>

In the latter case, without the else clause, (`<additional_statement(s)>`) will be executed after the while loop terminates, no matter what.

When (`<additional_statement(s)>`) are placed in an else clause, they will be executed only if the loop terminates “by exhaustion”—that is, if the loop iterates until the controlling condition becomes false. If the loop is exited by a break statement, the else clause won’t be executed.

# Nested Loops

A while loop can be contained within another while loop.

    while <expr1>:
        statement
        statement

        while <expr2>:
            statement
            statement  

Example

    >>> a = ['foo', 'bar']
    >>> while len(a):
    ...     print(a.pop(0))
    ...     b = ['baz', 'qux']
    ...     while len(b):
    ...         print('>', b.pop(0))
    ...
    foo
    > baz
    > qux
    bar
    > baz
    > qux

# One-line while Loops

As with an if statement, a while loop can be specified on one line. If there are multiple statements in the block that makes up the loop body, they can be separated by semicolons (;):

    >>> n = 5
    >>> while n > 0: n -= 1; print(n)
    4
    3
    2
    1
    0


<hr>
<a href="../conditional-statement" style="float:left;"> &laquo; Prev </a>
<a href="../for-loop-statement" style="float:right;"> Next &raquo; </a>