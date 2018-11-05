---
layout: page
---

## Module 2

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## 2.2 Basic Datatypes

# Simple Python Code

Enter <code> 1 + 1 </code> in the IDLE

<pre>
>>> 1 + 1
2
</pre>

In Python, <code> 1 + 1 </code> is called an <em>expression</em>. An expression can consist of values (such as 1), operators (such as +, -, *, /). You can also use paranthesis for grouping.

Some examples:

<pre>
>>> 5 + 5
10
>>> 10 * 3 - 5
25
>>> (10 * 3 - 5) / 5
5
>>> 5 / 2
2.5
</pre>

# Data types in Python

Below is the list of important data types commonly used in Python.

<ol>
    <li> Booleans </li>
    <li> Numbers </li>
    <li> Strings </li>
    <li> Bytes </li>
    <li> Lists </li>
    <li> Tuples </li>
    <li> Sets </li>
    <li> Dictionaries </li>
</ol>

# 1. Booleans

A boolean has two values - True or False. These values are constants and can be used to assign or compare boolean values.

<pre>
>>> condition = True
>>> if condition == True:
...     print("The condition is true.")
... else:
...     print("The condition is false.)
...
The condition is true
</pre>

# 2. Numbers

Numbers are one of the most prominent Python data types. The basic data types for numbers in Python are integer and float. Python also introduces complex as a new type of number.

Key points:

<ul>
    <li> The numbers in Python can be <b>int, float or complex</b>.</li>
    <li> Python has a built-in function <code>type()</code> to determine the data type of a variable or a value.
    </li>
    <li> In Python, you can add a <b>"j"</b> or <b>"J"</b> after a number to make it imaginary or complex. </li>
</ul>

<pre>
>>> num = 2
>>> print(type(num))
>>> num = 3.0
>>> print(type(num))
>>> num = 3+5j
>>> print(type(num))
</pre>

# Some operations on numbers

With Python, you can also use the <code>**</code> operator to calculate powers.

<pre>
>>> 3 ** 2 
9
>>> 2 ** 7  
128
</pre>

The equal sign (=) is used to assign a value to a variable.

<pre>
>>> breadth = 5
>>> length = 5 * 2
>>> length * breadth
50
</pre>

There are plenty of other operators you can use in Python expressions. The following table lists all the math operators in Python from highest to lowest precedence.

<table>
    <thead>
        <th> Operator </th>
        <th> Operation </th>
        <th> Use Case </th>
    </thead>
    <tr>
        <td> ** </td>
        <td> Exponent </td>
        <td> 3 ** 2 </td>
    </tr>
    <tr>
        <td> % </td>
        <td> Modulus/remainder </td>
        <td> 22 % 8 </td>
    </tr>
    <tr>
        <td> // </td>
        <td> Integer division/floored quotient </td>
        <td> 22 / 8 </td>
    </tr>
    <tr>
        <td> / </td>
        <td> Division </td>
        <td> 22 / 7 </td>
    </tr>
    <tr>
        <td> * </td>
        <td> Multiplication </td>
        <td> 10 * 3 </td>
    </tr>
    <tr>
        <td> - </td>
        <td> Subtraction </td>
        <td> 7 - 5 </td>
    </tr>
    <tr>
        <td> + </td>
        <td> Addition </td>
        <td> 10 + 2 </td>
    </tr>
</table>

# 3. Strings

Besides operating on numbers, you can also manipulate strings. Strings can be enclosed in single quotes <code>('...')</code> or double quotes <code>("...")</code>

<code>\</code> can be used to escape quotes.

<pre>
>>> 'Good Day!'
'Good Day!'
>>> 'Don\'t do that.'
"Don't do that."
>>> "Don't do that."
"Don't do that."
</pre>

You can use raw strings by adding an <code>r</code> before the first quote if you don’t want characters prefaced by <code>\</code> to be interpreted as special characters.

<pre>
>>> print('C:\some\name') 
C:\some
ame
>>> print(r'C:\some\name') 
C:\some\name
</pre>

For multiple lines you can use triple-quotes: <code>"""..."""</code> or <code>'''...'''</code>.

<pre>
print("""\
database: connect [OPTIONS]
     -user john                         
     -email john@gmail.com               
""")
</pre>

You can concatenate two strings using the <code>+</code> operator.

<pre>
>>> 'Alice' + 'Bob'
'AliceBob'
</pre>

You can repeat the strings using <code>*</code> operator.

<pre>
>>> 'mi' + 2 * 'si' + 'pi'
'misisipi'
</pre>

Two or more string literals next to each other are automatically concatenated.

<pre>
>>> 'Py' 'thon'
'Python'
</pre>

You can break long strings using this feature.

<pre>
>>> text = ('This is a multiple line text.' 
            'It has two sentences.')
>>> text
This is a multiple line text. It has two sentences.
</pre>

# Indexing in strings

Strings can be indexed with the first character having index 0. There is no separate character type; a character is simply a string of size one.

<pre>
>>> word = 'Apple'
>>> word[0]
'A'
>> word[4]
'e'
</pre>

Indices may also have negative numbers.

<pre>
>>> word[-1]
'e'
>>> word[-3]
'p'
</pre>

Note that since -0 is the same as 0, negative indices start from -1.

In addition to indexing, slicing is also supported. While indexing is used to obtain individual characters, slicing allows you to obtain substring.

<pre>
>>> word[0:2]
'Ap'
>>> word[2:4]
'ple'
</pre>

Note that start is always included, and the end always excluded.

Slice indices have useful defaults.
<ul> 
    <li> An omitted first index defaults to zero </li> 
    <li> An omitted second index defaults to the size of the string being sliced. </li>
</ul>

<pre>
>>> word[:2]
'Ap'
>>> word[3:]
'le'
</pre>

# Bytes

The byte is an immutable type in Python. It can store a sequence of bytes (each 8-bits) ranging from 0 to 255. Similar to an array, we can fetch the value of a single byte by using the index. But we can not modify the value.

Here are a few differences between a byte and the string.

<ul>
    <li>Byte objects contain a sequence of bytes whereas the strings store sequence of characters.</li>
    <li>The bytes are machine-readable objects whereas the strings are just in human-readable form.</li>
    <li>Since the byte is machine-readable, so they can be directly stored to the disk. Whereas, the strings   first need to encoded before getting on to the disk.</li>
</ul>

<pre>
>>> # Make an empty bytes object (8-bit bytes)
>>> empty_object = bytes(16)
>>> print(type(empty_object))
< class 'bytes' >
>>> print(empty_object)
b'\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00'
</pre>

<hr>
<a href="../python" style="float:left;"> &laquo; Prev </a>
<a href="../../../module/3/list" style="float:right;"> Next &raquo; </a>