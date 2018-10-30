---
layout: page
---

## Module 2

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## 2.2 Basic Datatypes

# Numbers

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

The basic data types for numbers in Python are integer and float. 

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

There are plenty of other operators you can use in Python expressions, too. The following table lists all the math operators in Python from highest to lowest precedence.

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

# Strings

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

You can use raw strings by adding an <code>r</code> before the first quote if you don’t want characters prefaced by <code>\</code> to be interpreted as special characters

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

<hr>
<a href="../python" style="float:left;"> &laquo; Prev </a>
<a href="../" style="float:right;"> Next &raquo; </a>