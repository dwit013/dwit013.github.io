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

    python3 -m venv virtual_environment_name

Or

    python3 -m virtualenv virtual_environment_name

Here, virtual_environment_name can be any arbitrary string.

Example

    python3 -m venv env

It creates a directory named **env** that contains a directory structre as follows.

    ├── bin
    │   ├── activate
    │   ├── activate.csh
    │   ├── activate.fish
    │   ├── easy_install
    │   ├── easy_install-3.6
    │   ├── pip
    │   ├── pip3
    │   ├── pip3.6
    │   ├── python -> python3.6
    │   ├── python3 -> python3.6
    ├── include
    ├── lib
    │   └── python3.6
    │       └── site-packages
    └── pyvenv.cfg

# Activating virtual envionment

On Windows run:

    env\Scripts\activate.bat

On Unix or MacOS run:

    source env/bin/activate

If the above action was successful, you should see the name of the virtual environment in your command line.

    (env) $

Also try the following command:

    which python

It shows the current Python file that is being used (It should be inside the virtual environment folder that we just created.)

    /home/usr/my_project/env/bin/python

# Install a third-party module

    pip install requests

The new module will be downloaded to the `env/lib/python3.6/site-packages` folder.

# Deactivating virtual environment

    deactivate

# Freezing dependencies and Source Control

You can create a file that lists all the dependencies used in the project. You can then share this file so that others can install the dependencies.

    pip freeze > requirments.txt

Now we have a requirements.txt file with the following list.

    certifi==2018.11.29
    chardet==3.0.4
    idna==2.8
    requests==2.21.0
    urllib3==1.24.1

To install from the requirements field, the following command can be used:

    pip install -r requirements.txt

# Using different versions of Python

You can also use a different version of Python other than your default one using virtual environment.

    python3 -m virtualenv env --python=python2.7
    
<hr>
<a href="../modules" style="float:left;"> &laquo; Prev </a>
<a href="../virtual-environment" style="float:right;"> Next &raquo; </a>