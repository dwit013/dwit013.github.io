---
layout: page
---

## Module 2

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## 2.1 Introduction to Python

Python is a clear and powerful object-oriented programming language. Python is one of the preferred programming languages for working in Test Automation, Web Scraping, Data Analytics, and Machine Learning domains. TIOBE index also ranked it as the third most popular programming languages of 2018.

Python is an interpreted programming language. An interpreted language is a type of programming language for which most of its implementations execute instructions directly and freely, without previously compiling a program into machine-language instructions. The interpreter executes the program directly, translating each statement into a sequence of one or more subroutines, and then into another language (often machine code).

Python has a dynamic type system. Dynamic type checking is the process of verifying the type safety of a program at runtime.

<a href="https://www.techbeamers.com/python-tutorial-step-by-step/"> Read more about Python's Features and Applications </a>

# Download Python

For Windows: <a href="https://www.python.org/downloads/windows/" target="_blank"> Click Here </a> <br>
For Mac: <a href="https://www.python.org/downloads/mac-osx/" target="_blank"> Click Here </a> <br>
For Linux: <a href="https://www.techbeamers.com/python-tutorial-step-by-step/#install-python-on-linux" target="_blank"> Click Here </a> <br>

# Installing Python

For our course, we will be using a Windows machine and you can follow the following steps to install Python in your Windows machine.

For installation on other machines <a href="https://www.techbeamers.com/python-tutorial-step-by-step/#run-python" target="_blank"> click here </a>.

# Installing on Windows

Go to the download python for windos page <a href="https://www.python.org/downloads/windows/" target="_blank"> here</a>, and select the Python 3.x package. Next, launch the download package, follow the steps, and finish the installation.

During installation, select the option "Install for all users" and use the default destination directory.

Next, open the "Start" menu and type "cmd" into the search box. Right-click on the "cmd.exe" link and choose to run as an administrator. 

Change the directory to "C:\Python3x" and run the following command to set Python on the system's path.

<pre>
setx PATH "%cd%;%path%;"
pause
</pre>

# Run Python on Windows

Open Python's default IDE <b>IDLE</b>. 

Once the IDLE window appears, type the following command.

<pre>
>>> print("Hello World")
Hello World!
</pre>

# Python Basics

# Commenting

In Python, a single line comment starts with a <code>#</code>

<pre>
>>> # This is a comment
</pre>

For multiple line comments, we use the delimiter <code>"""</code>

<pre>
“””” 
    This is a multine comment in Python.
    It spans more than a single line.
“”” 
</pre>

# Declaring a variable

In Python, the following rules apply when naming a variable.

<ol>
    <li> It can only be one word. </li>
    <li> It can use only letters, numbers, and the underscore (_) character. </li>
    <li> It cannot begin with a number. </li>
</ol>

Some examples:
<pre>
>>> a = 2
>>> a
2
>>> b = 3
>>> a + b
5
>>> word = "Python"
>>> word
"Python"
</pre>

<hr>
<a href="../../../module/1/github" style="float:left;"> &laquo; Prev </a>
<a href="../basic-datatypes" style="float:right;"> Next &raquo; </a>



