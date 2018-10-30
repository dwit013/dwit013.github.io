---
layout: page
---

## Module 1

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## 1.3 GitHub

GitHub is the single largest host for Git repositories, and is the central point of collaboration for millions of developers and projects. A large percentage of all Git repositories are hosted on GitHub, and many open-source projects use it for Git hosting, issue tracking, code review, and other things.

You can setup an account by visiting <a href="https://github.com">https://github.com</a>

# Contributing to a Project

# Forking Projects

When you “fork” a project, GitHub will make a copy of the project that is entirely yours; it lives in your namespace, and you can push to it.

# Creating a Pull Request

Vist <a href="https://github.com/dwit013"> https://github.com/dwit013/ </a> and go to <code> testrepo </code>. Fork the project. The project should appear in your repository list.

Next clone the repository locally.

<pre> 
$ git clone https://github.com/dwit013/testrepo.git 
Cloning into 'testrepo'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
</pre>

Make some changes to the project. For example, add a new file. Then add the changes to the staging area and commit the changes.

<pre>
$ git add myfile.txt
$ git commit -m "Added myfile.txt"
[master 60f8194] Added myfile.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 myfile.txt
</pre>

<pre>
$ git push origin master
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 281 bytes | 281.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/awalesushil/testrepo.git
   40ad3ba..60f8194  master -> master
</pre>

Now the your local changes should appear on your forked github repository. 

<ol>
<li>Next click on the New Pull Request button.</li>

<em>The opened page will show the changes that you have made to the original repository.</em> 

<li>Click on the Create Pull Request button. </li>
<li>Next add a comment and create a pull request.</li>

</ol>

Your pull request shall appear in the Pull Request tab of the original repository page. The owner of the repository can either accept or reject your pull request.

# Further Reading
<a href="https://git-scm.com/book/en/v2" target="_blank"> Git Book </a> <br>
<a href="https://medium.freecodecamp.org/how-to-use-git-efficiently-54320a236369">How to use git efficiently</a>
<hr>
<a href="../git-basics" style="float:left;"> &laquo; Prev </a>
<a href="../../../module/2/python" style="float:right;"> Next &raquo; </a>



