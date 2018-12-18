---
layout: page
---

## Module 7

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## File Handling

## 7.2 File Handling Basic

Python provides basic functions and methods to manipulate files. Most of the manipulation is based on the **file** object.

## Open Function

The open function is used to open a file. It returns a **file** object.

    file_object = open(file_name, access_mode)

Here
* file_name is a string value that specifies the name of the file to be opened
* access_mode determines the mode in which the file has to be opened - read, write, append

    file = open('some_file.txt', r)

You can also open a file using **with** keyword.

    with open('some_file.txt') as f:
        statement/s

It is good practice to use the with keyword when dealing with file objects. The advantage is that the file is properly closed after its suite finishes, even if an exception is raised at some point.

## Access modes

<table>
    <thead>
        <th> Access Mode </th>
        <th> Description </th>
    </thead>
    <tbody>
        <tr>
            <td> r </td>
            <td> Opens a file for reading only. The file pointer is placed at the beginning of the file.</td>
        </tr>
        <tr>
            <td> rb </td>
            <td> Opens a file for reading only in binary format. </td>
        </tr>
        <tr>
            <td> r+ </td>
            <td> Opens a file for both reading and writing. </td>
        </tr>
        <tr>
            <td> rb+ </td>
            <td> Opens a file for both reading and writing in binary format. </td>
        </tr>
        <tr>
            <td> w </td>
            <td> Opens a file for writing only. Overwrites the file if the file exists. If the file does not exist, creates a new file for writing. </td>
        </tr>
        <tr>
            <td> wb </td>
            <td> Opens a file for writing only in binary format. </td>
        </tr>
        <tr>
            <td> w+ </td>
            <td> Opens a file for both writing and reading. </td>
        </tr>
        <tr>
            <td> wb+ </td>
            <td> Opens a file for both writing and reading in binary format. </td>
        </tr>
        <tr>
            <td> a </td>
            <td> Opens a file for appending. The file pointer is at the end of the file if the file exists. That is, the file is in the append mode. If the file does not exist, it creates a new file for writing.</td>
        </tr>
        <tr>
            <td> ab </td>
            <td> Opens a file for appending in binary format. </td>
        </tr>
        <tr>
            <td> a+ </td>
            <td> Opens a file for both appending and reading. </td>
        </tr>
        <tr>
            <td> ab+ </td>
            <td> Opens a file for both appending and reading in binary format. </td>
        </tr>
    </tbody>
</table>

## Close method

The file object has a close method which flushes any unwritten information and closes the file object.
After the file is closed, no more writing can be done.

Syntax 

    file.close()

Example

    file = open('some_file.txt', r)
    file.close()

## Write method

The write() method writes some string to an open file. It doesn't add a new line character to the end of the string.

Syntax

    file.write(string)

Example

    file = open('file.txt', w)
    file.write('File handling is so easy in Python.')
    file.close()

## Read method

The read() method reads a string from an open file.

Syntax

    file.read(count)

The read() method reads a string from an open file.

Here, **count** specifies the number of bytes to read starting from the beginning of the file.

Example

    file = open('file.txt', r)
    str = file.read(10)
    print (str)
    file.close()

If **count** is not specified, it reads until the end of file.

Example

    with open('file.txt') as f:
        str = f.read()
    print(str)

## Readline method

The readline() method reads a single line from the file and a newline character `\n` is left at the end of the string. It is only omitted on the last line of the file if the file doesn’t end in a newline. 

You can also use the `readlines()` method which reads all the lines in the file and returns a list with the lines as members.

Syntax

    file.readline()

Example

    with open('file.txt') as f:
        f.readline() # reads only the first line
        f.readlines() # reads only the lines and returns a list

For reading lines from a file, you can loop over the file object. This is memory efficient, fast, and leads to simple code:

Example

    for line in f:
        print (line, end =' ')

## File Positions

The tell() method returns an integer value giving the current position within the file. 

Syntax

    file.tell()

The seek() method changes the current file position.

Syntax

    file.seek(offset, from)

Her
* offset indicates the number of bytes to be moved
* from specifies the reference position from where the bytes are to be moved

If `from = 0` then it means the beginning of the file, if `from = 1` then it means the current position and if `from = 2` that means end of the file.

You can rename or delete file using Python's **os module**.

## Rename method

The rename method renames a file.

Syntax

    import os
    os.rename('old_file_name.txt','new_file_name.txt')

## Remove method

The remove method deletes a file.

Syntax

    import os
    os.remove('some_file.txt')


<hr>
<a href="../regular-expressions" style="float:left;"> &laquo; Prev </a>
<a href="../file-handling-advanced" style="float:right;"> Next &raquo; </a>