---
layout: page
---

## Module 1

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## 1.2 Git Basics

# Recording changes to the repository

Each file in the working directory can be in one of two states:
<ol>
    <li> Tracked </li>
    <li> Untracked </li>
</ol>

Tracked files are the files that Git knows about. Further, tracked files can be in one of the following states:
<ol>
    <li> Unmodified </li>
    <li> Modified </li>
    <li> Staged </li>
</ol>

All other files are untracked.

When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

<img src="https://git-scm.com/book/en/v2/images/lifecycle.png" alt="Life cycle of status of your files">
<em>Life cycle of status of your files. Source: Git-scm</em>

# Checking the Status of your files

You use <code> git status </code> command to check the status of your project.

<pre>
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
</pre>

This means that your working directory is clean.

Now, let's add a new file to the project. <code>newfile.txt</code> Now if you run <code>git status</code> command, you will get the following response.

<pre>
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add < file >..." to include in what will be committed)

    newfile.txt

nothing added to commit but untracked files present (use "git add" to track)
</pre>

# Tracking new files

The <code>newfile.txt</code> is untracked. You can tell git to track the new file by running the command <code>git add</code>

<code>$ git add newfile.txt</code>

<pre>
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD < file >..." to unstage)

    new file:   README
</pre>

Now the file <code>newfile.txt</code> is tracked by git. You can untrack the file by running the command 

<code>git reset HEAD < filename > </code>

# Staging Modified Files 

Now let us modify our file <code>newfile.txt</code> and then run the <code>git status</code> command.

<pre>
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes not staged for commit:
  (use "git add < file >..." to update what will be committed)
  (use "git checkout -- < file >..." to discard changes in working directory)

    modified:   newfile.txt
</pre>

To stage the modified file, we run the <code>git add</code> command.

<code>git add newfile.txt</code>

If there are multiple files that you want to stage, you can run the following command:

<code> git add . </code>

The <code>.</code> stages all the untracked and modified files. 

# Ignoring Files

You can add a <code>.gitignore</code> file to allow git to ignore certain files. Often these files are those related to the local machine or IDE. 

An example of <code>.gitignore</code> file.

<pre>
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
</pre>

# Commiting your changes

You can commit the files that are in your staging area. You commit log will be stored in the <code>.git</code> directory. To commit the changes you made, you run the following code.

<code> git commit -m "Your message" </code>

For example, to commit the above changes, we write. 

<pre>
$ git commit -m "Added newfile.txt"
[master 463dc4f] Added newfile.txt
 1 files changed, 1 insertions(+)
 create mode 100644 newfile.txt
</pre>

# Viewing commit history

You can view your entire commit history using the command <code>git log</code>

<pre>
$ git log
commit ca82a6dff817ec66f44342007202690a93763949
Author: Scott Chacon < schacon@gee-mail.com >
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the version number

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon < schacon@gee-mail.com >
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon < schacon@gee-mail.com >
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit
</pre>

# Undoing things

There are a few basic tools to undoing changes. However, you must be careful as you can't always undo things.

You can redo a commit by using <code>git commit --amend</code> command. You can make additional changes you forgot, stage them, and commit again. 

<pre>
$ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
</pre>

# Unstaging a staged file

We can remove files from the staging area using <code> git reset HEAD < file > </code> command.

<pre>
$ git reset HEAD newfile.txt
Unstaged changes after reset:
M	newfile.txt
</pre>

<pre>
$ git status
On branch master

Changes not staged for commit:
  (use "git add < file >..." to update what will be committed)
  (use "git checkout -- < file >..." to discard changes in working directory)

    modified:   newfile.txt
</pre>

# Unmodifying a Modified File

If you don't want to keep the new changes and revert back to the file when you last commited, you can use the following command to do so. 

<pre>
$ git checkout -- newfile.txt
$ git status
On branch master
nothing to commit, working tree clean
</pre>

# Working with remotes

Remote repositories are versions of your project that are hosted on the Internet or network somewhere. To be able to collaborate on any Git project, you need to know how to manage your remote repositories. Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work. 

# Showing your remotes

To see which remote servers you have configured, you can run the <code>git remote</code> command. 

<pre>
$ git clone https://github.com/dwit013/assignments.git
Cloning into 'assignments'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
$ cd assignments
$ git remote
origin
</pre>

# Fetching and pulling from your remotes

To get data from your remote projects, you can run:

<code>$ git fetch < remote ></code>

<code>git fetch </code> command only downloads the data to your local repository — it doesn’t automatically merge it with any of your work or modify what you’re currently working on. You have to merge it manually into your work when you’re ready.

You can use the <code>git pull</code> command to automatically fetch and then merge that remote branch into your current branch.

# Pushing to your remotes

When you have your project at a point that you want to share, you have to push it upstream. The command for this is simple: <code>git push < remote > < branch ></code>

<code>$ git push origin master</code>



# Further Reading
<a href="https://git-scm.com/book/en/v2" target="_blank"> Git Book </a>
<hr>
<a href="../git" style="float:left;"> &laquo; Prev </a>
<a href="../github" style="float:right;"> Next &raquo; </a>