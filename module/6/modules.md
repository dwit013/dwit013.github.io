---
layout: page
---

## Module 6

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Modular Programming

Modular programming is a programming paradigm of breaking a large program into separate, smaller and manageable modules. Individual modules can then be assembled together to create a larger application.

In Python, use of Functions, Modules and Packages promote program modularization.

## 6.1 Modules

A module is a file containing Python definitions and statements. The file name is the module name with the suffix `.py` appended. Definitions from a module can be imported into other modules or into the main module.

There are three different ways to define a module in Python. 

* A module can be written in Python itself.
* A module can be written in C and loaded dynamically at run-time, like the re (regular expression) module
* A built-in module is intrinsically contained in the interpreter, like the <a href="https://realpython.com/python-itertools/" target="blank"> iterator modules</a>.

A module’s contents are accessed the same way in all three cases: with the import statement. The import has the following syntax:

    import module_name

Create a Python file named my_module.py

    foo = 7

    def hello():
        print("Hello from my_module.py")

Also create a new file main.py and import the above module to the file.

    import my_module
    
    print(my_module.foo)
    my_module.hello()

Run main.py

Expected Output

    7
    Hello from my_module.py


## Module search path

When the intereter executes `import my_module` statement, it searches for `my_module.py`in a list of directories assembled from the following sources.

* The directory from which the input script was run or the current directory if the interpreter is being run interactively
* The list of directories contained in the PYTHONPATH environment variable, if it is set. (The format for PYTHONPATH is OS-dependent but should mimic the PATH environment variable.)
* An installation-dependent list of directories configured at the time Python is installed

## Accessing objects in modules

Notice that from the `main.py` (caller) objects in the module `my_module` are only accessible when prefixed with `module_name` via dot notation.

Each module has its own private symbol table. The statement `import module_name` only places `module_name` in the caller’s symbol table. The objects that are defined in the module remain in the module’s private symbol table. To be accessed in the local symbol table, names of objects defined in the module must be prefixed by `module_name`.

## dir() function

The built-in function dir() returns a list of defined names in a namespace. Without arguments, it produces an alphabetically sorted list of names in the current local symbol table.

Add the following statement in main.py.

    print(dir())

Expected output

    ['__annotations__', '__builtins__', '__cached__', '__doc__', '__file__',
    '__loader__', '__name__', '__package__', '__spec__', 'mm']

When given an argument that is the name of a module, dir() lists the names defined in the module.

Add the following statement in main.py.

    print(dir(my_module))

Expected Output

    ['__builtins__', '__cached__', '__doc__', '__file__', '__loader__', 
    '__name__', '__package__', '__spec__', 'foo', 'hello']

## Executing modules as scripts

# __ name __ variable

Within a module, the module’s name (as a string) is available as the value of the global variable `__name__`. 

Every module in python has a special attribute called `__name__`. The value of `__name__` attribute is set to `__main__`  when module is run as main program. Otherwise the value of `__name__`  is set to contain the name of the module.

Add the following to my_module.py
    
    foo = 7

    def hello():
        print("Hello from my_module.py")
        print("Value of __name__ is: ", __name__)
    
    if __name__ == "__main__":
        print("Executing as main program")
        hello()

Execute the above file as 

    python my_module.py

Expected Output:

    Executing as main program
    Hello from my_module.py
    Value of __name__ is: __main__

Now execute main_module.py 

    python main_module.py

Expected Output

    7
    Hello from my_module.py
    Value of __name__ is: my_module

## Different ways to import modules

# I. Importing many modules at once.

    import module_name [, module_name ...]

# II. Using an alias (alternate name)

    import module_name as alias

Here, `mn` is an alias for module_name.

# III. Importing individual objects

    from module_name import name(s)

This statement allows individual objects from the module to be imported directly into the caller’s symbol table.

# IV. Importing all objects 

    from module_name import *

This will place the names of all objects from `module_name` into the local symbol table, with the exception of any that begin with the underscore (_) character.

# V. Using an alias for module objects

    from module_name import name as alias

Example

    from my_module import foo as f, hello as hi



<hr>
<a href="../../../module/5/anonymous-function" style="float:left;"> &laquo; Prev </a>
<a href="../packages" style="float:right;"> Next &raquo; </a>