---
layout: page
---

## Module 4

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Control Statements

## 4.1 Conditional Statements

A control structure directs the order of execution of the statements in a program (referred to as the program’s control flow). It allows a program to skip over some statements, execute a series of statements repetitively, or choose between alternate sets of statements to execute.

In a Python program, the if statement allows for conditional execution of a statement or group of statements based on the value of an expression.

# The if Statement

Simplest form of if statement looks like:

    if <expr>:
        <statement>

Here,

* <expr> is evaluated as Boolean expression
* <statement> can be any valid Python statement

Example:

    >>> x = 0
    >>> y = 5

    >>> if x < y:                            
    ...     print('yes')
    ...
    yes
    >>> if y < x:                            
    ...     print('yes')
    ...


If we want to execute two or more statements after checking the condition, we have to be careful with the identation. The group of statements is called a block or compund statement.

    if <expr>:
        <statement>
        <statement>
        ...
        <statement>
    <following_statement>

Here, all the statements at the matching indentation level are considered part of the same block. The entire block is executed if (`<expr>`) is true, or skipped over if (`<expr>`) is false. Either way, execution proceeds with (`<following_statement>`) afterward.

There is no token that denotes the end of the block. Rather, the end of the block is indicated by a line that is indented less than the lines of the block itself.

Example,

    >>> if 'Nepal' in ['India','Nepal','China']:
    ...     print ('The condition is true.')
    ...     print ('Nepal is in between India and China')
    ...     print ('Done')
    The condition is true.
    Nepal is in between India and China.
    Done

Blocks can be nested to arbitray depth. For example,

    >>> if 'Nepal' in ['India', 'Nepal', 'China']:        
    ...     print('Outer condition is true')      
    ...     if 10 > 20:                          
    ...         print('Inner condition 1')       
    ...     print('Between inner conditions')     
    ...     if 10 < 20:                           
    ...         print('Inner condition 2')        
    Outer condition is true
    Between inner conditions
    Inner condition 2

# The else and elif Clauses

We use if ... else clause to evaluate a condition and take one path if it is true but specify an alternative path if it is not.

    if <expr>:
        <statement(s)>
    else:
        <statement(s)>

Example,

    >>> x = 20
    >>> if x < 50:
    ...     print('x is small')
    ... else:
    ...     print('x is large')
    ...
    x is small

We can do branching based on several alternatives. For this, use one or more elif (short for else if) clauses.

    if <expr>:
        <statement(s)>
    elif <expr>:
        <statement(s)>
    elif <expr>:
        <statement(s)>
        ...
    else:
        <statement(s)>

Example

    >>> name = 'Joe'
    >>> if name == 'Fred':
    ...     print('Hello Fred')
    ... elif name == 'Xander':
    ...     print('Hello Xander')
    ... elif name == 'Joe':
    ...     print('Hello Joe')
    ... elif name == 'Arnold':
    ...     print('Hello Arnold')
    ... else:
    ...     print("I don't know who you are!")
    ...
    Hello Joe

# One-Line if Statements

You can also write an entire if statement on one line.

    if <expr>: <statement>

There can even be more than one (`<statement>`) on the same line, separated by semicolons:

    if <expr>: <statement_1>; <statement_2>; ...; <statement_n>

    >>> if 'f' in 'foo': print('1'); print('2'); print('3')
    ...
    1
    2
    3
    >>> if 'z' in 'foo': print('1'); print('2'); print('3')
    ...

Multiple statements may be specified on the same line as an elif or else clause as well:

    >>> x = 2
    >>> if x == 1: print('foo'); print('bar'); print('baz')
    ... elif x == 2: print('qux'); print('quux')
    ... else: print('corge'); print('grault')
    ...
    qux
    quux

    >>> x = 3
    >>> if x == 1: print('foo'); print('bar'); print('baz')
    ... elif x == 2: print('qux'); print('quux')
    ... else: print('corge'); print('grault')
    ...
    corge
    grault

# Conditional Expressions

Python supports one additional decision-making entity called a conditional expression.

    <expr1> if <conditional_expr> else <expr2>

This is different from the if statement forms listed above because it is not a control structure that directs the flow of program execution. It acts more like an operator that defines an expression. 

In the above example, (`<conditional_expr>`) is evaluated first. If it is true, the expression evaluates to (`<expr1>`). If it is false, the expression evaluates to (`<expr2>`).

    >>> lunch_time = True
    >>> print("Let's go to the", 'canteen' if lunch_time else 'library')
    Let's go to the canteen
    >>> lunch_time = False
    >>> print("Let's go to the", 'canteen' if lunch_time else 'library')
    Let's go to the library

Use case:

    >>> if a > b:
    ...     m = a
    ... else:
    ...     m = b
    ...

    >>> m = a if a > b else b

# The pass Statement

Consider the following code:

    >>> if True:
    ... 
    File "<stdin>", line 2
        
        ^
    IndentationError: expected an indented block

We can get over this using the pass statement.

    >>> if True:
    ...     pass
    ...


<hr>
<a href="../../../module/3/dictionary" style="float:left;"> &laquo; Prev </a>
<a href="../while-statement" style="float:right;"> Next &raquo; </a>