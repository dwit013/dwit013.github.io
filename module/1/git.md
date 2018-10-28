---
layout: page
---

## Module 1

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## 1.1 Git

Git is a version control system. It is a free and open source software used for tracking changes in computer files and coordinating work on those files among multiple people.

Git was created by Linus Trovalds in 2005 for development of the Linux kernel, with other kernel developers contributing to its inital development.

# Version Control System

Version control is a system that records changes to a file or a set of files over time. It is the management of changes to documents, computer programs, large websites and other collection of information.

Suppose you are writing an essay. You make the first draft ready and save it as <code>first_draft.txt</code>. The next day, you make some revisions to it and save it as <code>second_draft.txt</code>. Finally, one day before submission, you make the final changes and save it as <code>final_draft.txt</code>. You make the submission and the teacher returns back the file with corrections as <code>corrected.txt</code>. It is already a mess. Imagine doing this with multiple files when working on a large development project. This is where version control system comes in handy.

Version control systems tracks the changes made to each file, records the date and time the changes were made. Moreover, if multiple people are working on the project, it also keeps track of who made the changes. And the main benefit to using a VCS is you can revert back to an older version when required. 

## Git Setup

# Installing Git

Check this <a href="https://git-scm.com/book/en/v2/Getting-Started-Installing-Git" target="_blank"> link </a> to download and install git.

# Setup

Git stores all the configuration information in gitconfig file.

# Identity

Setup username and email address 

<pre>
$ git config --global user.name "John Doe" 
$ git config --global user.email johndoe@example.com
</pre>

<code>-- global</code> option will set the information for the whole system. However, if you want to use a different account for a specific project you can setup the new account information when working in the project directory.

For example, you have a project named 'personal_blog' and you want to use a different account when working on the project. You can follow the following commands.

<pre>
cd personal_blog
$ git config --local user.name "Jane Doe"
$ git config --local user.email janedoe@example.com
</pre>

Here <code> -- local </code> option is default. Hence, you can omit it. 

# Checking your settings

<pre>
$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...
</pre>

# Initializing a Repository

<code>$ git init </code>

This creates a new subdirectory named .git that contains all of your necessary repository files — a Git repository skeleton.

# Cloning an exisiting Repository

You clone a repository with <code> git clone url </code>. For example, if you want to clone the Git linkable library called <code>libgit2</code>, you can do so like this:

<code>$ git clone https://github.com/libgit2/libgit2</code>

If you want to clone the repository into a directory named something other than libgit2, you can specify the new directory name as an additional argument:

<code>$ git clone https://github.com/libgit2/libgit2 mylibgit</code>


# Further Reading
<a href="https://git-scm.com/book/en/v2" target="_blank"> Git Book </a>
<hr>
<a href="../../../index" style="float:left;"> &laquo; Prev </a>
<a href="../git-basics" style="float:right;"> Next &raquo; </a>