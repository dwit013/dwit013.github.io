---
layout: page
---

## Module 6

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Modular Programming

## 6.3 Virtual Environment

Suppose you are working on two separate projects: Project_A and Project_B. Say, you are using a package `package_one` version 1.0 for Project_A. But, Project_B requires the same package `package_one` but its latest version, version 2.0. 

All the packages installed using a third party installer such as **pip** are located in the site-packages folder. 

    >>> import site
    >>> site.getsitepackages()
    ['/home/usr/anaconda3/lib/python3.6/site-packages']

So if you download a new version of a package, the latest version is downloaded and stored in the same folder. There is no way to distinguish between the two versions, and the latest version is used when the package is imported.

## Virtual Environment

Virtual environment is a self-contained directory tree that contains a Python installation for a particular version of Python, plus a number of additional packages.

The simple idea behind virtual environment is to create an isolated environment for Python projects. Therefore, each project can have its own dependencies, regardless of what dependencies every other project has.

There is no limit to the number of virtual environments you can create.

**Note:** It is always a good idea to work in a virtual environment.

## Installing

If you are using Python 3.6 or later, virtualenv tool comes built in. Otherwise you have to install it.

    pip install virtualenv

## Using virtual environment

# Create a project directory.

    mkdir my_project
    cd my_project

# Create a virtual environment

    virtualenv


<hr>
<a href="../modules" style="float:left;"> &laquo; Prev </a>
<a href="../virtual-environment" style="float:right;"> Next &raquo; </a>