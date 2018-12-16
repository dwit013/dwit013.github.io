---
layout: page
---

## Module 6

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Modular Programming

## 6.2 Packages

Packages are a way of hierarchically structuring Python’s module namespace. For example, the module name `name1.name2` designates a submodule named `name2` in a package named `name1`. 

In the same way that modules help avoid collisions between global variable names, packages help avoid collisions between module names.

# Creating Packages

A Python package is simply a directory consisting of one or more Python modules (scripts).

<img src="http://fastread.aitechtonic.com/submittutorial/uploads/python/PackageModuleStructure.jpg"> 
<br>
<em>Image Source: AITechTonic</em>

# Importing packages and its modules

    import package_name[, package_name, ...]
    import game

    import package_name.module_name[, package_name.module_name, ... ]
    import game.sound.load, game.image.open

    from package_name.module_name import names
    from game.level.start import level_one

# Package Initialization

When a package or a module is imported, `__init__.py` is invoked, if present. `__init__.py` can be used for execution of package initialization code, such as initialization of package-level data. 

    print(f'Invoking __init__.py for {__name__}')
    A = ['quux', 'corge', 'grault']

Now when the package is imported, global list A is initialized.

The statment `import package_name` only imports the package and doesn't import any modules. We can import the modules by writing the following in `__init__.py`. 

    import package_name.module_name

## Third-party Modules

# PIP

PIP is a package manager for Python modules/packages. For Python 3.4 or later, PIP is included in default.

# Check if PIP is installed

    pip --version

# Installing Python

You can download and install pip. More details on [Link]('https://pip.pypa.io/en/stable/installing/')

# Downloading and installing a package

    pip install package_name
    
    pip install flask

# Uninstalling a package

    pip uninstall package_name

# List packages

    pip list


<hr>
<a href="../modules" style="float:left;"> &laquo; Prev </a>
<a href="../virtual-environment" style="float:right;"> Next &raquo; </a>