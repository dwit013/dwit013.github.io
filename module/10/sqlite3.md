---
layout: page
---

# Module 10

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

# Database

## 10.1 SQLite

SQLite is a C-language library that implements a small, fast, self-contained, high-reliability, full-featured, SQL database engine. SQLite doesn’t require a separate server process and allows accessing the database using a nonstandard variant of the SQL query language. 

Some applications can use SQLite for internal data storage. It’s also possible to prototype an application using SQLite and then port the code to a larger database such as PostgreSQL or Oracle.

SQLite is a database, which is zero-configured, which means like other databases you do not need to configure it in your system.

## SQLite3

You do not need to install this module separately because it is shipped by default along with Python version 2.5.x onwards.

Create a Python file named `database.py` and write the following.

```python
import sqlite3

conn = sqlite3.connect('student.db')
```

Running the above code should create a file **student.db** in the project folder.

Here, the `connect()` function is used to create a connection object that represents the database.

You can also supply database name as the special name **:memory:** to create a database in RAM.

```python
import sqlite3

conn = sqlite3.connect(':memory:')
```

Optionally, you can create a cursor object, which will help you in executing all the SQL statements.

```python

c = conn.cursor()

```

> Note: Cursor objects allow you to keep track of which result set is which, since it's possible to run multiple queries before you're done fetching the results of the first. The examples to follow will make it clear.

### Executing Queries

We use `execute()` function to execute an SQL statement. Let us run an SQL query to create a table.

```python
c.execute("""CREATE TABLE student (
            id integer
            first_name text,
            last_name text,
            batch integer
    )""")

conn.commit()

conn.close()
```

Here:

* the statement passed as the argument of the `execute()` function is an SQL statement to create a table **student**.
* we must commit the changes we made by running `conn.commit()`. This action is necessary in execute so that the changes you made is persistent and is available in subsequent sessions.
* finally, you must close the database connection with `conn.close()`.
  
> Note: close() this does not automatically call commit(). If you just close your database connection without calling commit() first, your changes will be lost!

### Storage Classes and Datatypes

In the above SQL statement **integer** and **text** are keywords denoting respective datatypes of the columns in the table.

Each value stored in an SQLite database has one of the following storage classes:

* NULL. The value is a NULL value.
* INTEGER. The value is a signed integer value.
* REAL. The value is a floating point value.
* TEXT. The value is a text string.
* BLOB. The value is a blob of data, stored exactly as it was input.

### Create a table

We can create tables in the database by running the following program.

```python
import sqlite3

conn = sqlite3.connect('student.db')

c = conn.cursor()

c.execute("""CREATE TABLE student (
            id integer,
            first_name text,
            last_name text,
            batch integer
    )""")

conn.commit()

conn.close()
```

### INSERT Operation

We can insert values in the tables by running the following program. Comment the `c.execute()` function in the above example and add the following.

```python
c.execute("""INSERT INTO student VALUES (
        001, 'John', 'Doe', 2021
    )""")
c.execute("""INSERT INTO student VALUES (
        002, 'Jane', 'Smith', 2020
    )""")
```

### SELECT operation

We can fetch and display records from a table by running the following program. Comment the `c.execute()` function in the above example and add the following.

```python
c = conn.execute("""SELECT id, first_name, last_name, batch from student""")

for row in c:
   print ("ID = ", row[0])
   print ("NAME = {} {}".format(row[1], row[2]))
   print ("BATCH = ", row[3], "\n")
```

The execution of a SELECT operation returns a list of rows from the table. If the query returns 0 rows then 'None' is returned.

### UPDATE operation

We can update a row in a table by running the following program.

```python

c.execute("""UPDATE student SET batch = 2021 WHERE ID = 2""")
conn.commit()

print ("Total number of rows updated :", conn.total_changes)

c = conn.execute("""SELECT id, first_name, last_name, batch from student""")

for row in c:
   print ("ID = ", row[0])
   print ("NAME = {} {}".format(row[1], row[2]))
   print ("BATCH = ", row[3], "\n")
```

Here, `conn.total_changes` returns the total number of database rows that have been modified, inserted, or deleted since the database connection was opened.

### DELETE operation

We can delete a row in a table by running the following program.

```python

c.execute("""DELETE FROM student WHERE ID = 2""")
conn.commit()

print ("Total number of rows updated :", conn.total_changes)

c = conn.execute("""SELECT id, first_name, last_name, batch from student""")

for row in c:
   print ("ID = ", row[0])
   print ("NAME = {} {}".format(row[1], row[2]))
   print ("BATCH = ", row[3], "\n")
```

## SQLite operations

Following are important sqlite3 module operations.

<table>
    <thead>
        <th>Sr.No.</th>
        <th>Operation and Description</th>
    </thead>
    <tr>
        <td>1</td>
        <td><p><b>sqlite3.connect(database [,timeout ,other optional arguments])</b></p>
        <p>This operation opens a connection to the SQLite database file. You can use ":memory:" to open a database connection to a database that resides in RAM instead of on disk. If database is opened successfully, it returns a connection object.</p>
        <p>If the given database name does not exist then this call will create the database. You can specify filename with the required path as well if you want to create a database anywhere else except in the current directory.</p>
        </td>
    </tr>
    <tr>
        <td>2</td>
        <td><p><b>connection.cursor([cursorClass])</b></p>
        <p>This operation creates a <b>cursor</b> which will be used throughout of your database programming with Python. This method accepts a single optional parameter cursorClass. If supplied, this must be a custom cursor class that extends sqlite3.Cursor.</p>
        </td>
    </tr>
    <tr>
        <td>3</td>
        <td><p><b>cursor.execute(sql [, optional parameters])</b></p>
        <p>This operation executes an SQL statement. The SQL statement may be parameterized (i. e. placeholders instead of SQL literals). The sqlite3 module supports two kinds of placeholders: question marks and named placeholders (named style).</p>
        </td>
    </tr>
    <tr>
        <td>4</td>
        <td><p><b>connection.execute(sql [, optional parameters])</b></p>
        <p>This operation is a shortcut of the above execute method provided by the cursor object and it creates an intermediate cursor object by calling the cursor method, then calls the cursor's execute method with the parameters given.</p>
        </td>
    </tr>
    <tr>
        <td>5</td>
        <td><p><b>cursor.executemany(sql, seq_of_parameters)</b></p>
        <p>This operation executes an SQL command against all parameter sequences or mappings found in the sequence sql.</p>
        </td>
    </tr>
    <tr>
        <td>6</td>
        <td><p><b>connection.executemany(sql[, parameters])</b></p>
        <p>This operation is a shortcut that creates an intermediate cursor object by calling the cursor method, then calls the cursor's executemany method with the parameters given.</p>
        </td>
    </tr>
    <tr>
        <td>7</td>
        <td><p><b>cursor.executescript(sql_script)</b></p>
        <p>This operation executes multiple SQL statements at once provided in the form of script. It issues a COMMIT statement first, then executes the SQL script it gets as a parameter. All the SQL statements should be separated by a semi colon (;).</p>
        </td>
    </tr>
    <tr>
        <td>8</td>
        <td><p><b>connection.executescript(sql_script)</b></p>
        <p>This operation is a shortcut that creates an intermediate cursor object by calling the cursor method, then calls the cursor's executescript method with the parameters given.</p>
        </td>
    </tr>
    <tr>
        <td>9</td>
        <td><p><b>connection.total_changes()</b></p>
        <p>This operation returns the total number of database rows that have been modified, inserted, or deleted since the database connection was opened.</p>
        </td>
    </tr>
    <tr>
        <td>10</td>
        <td><p><b>connection.commit()</b></p>
        <p>This method commits the current transaction. If you don't call this method, anything you did since the last call to commit() is not visible from other database connections.</p>
        </td>
    </tr>
    <tr>
        <td>11</td>
        <td><p><b>connection.rollback()</b></p>
        <p>This method rolls back any changes to the database since the last call to commit().</p>
        </td>
    </tr>
    <tr>
        <td>12</td>
        <td><p><b>connection.close()</b></p>
        <p>This method closes the database connection. Note that this does not automatically call commit(). If you just close your database connection without calling commit() first, your changes will be lost!</p>
        </td>
    </tr>
    <tr>
        <td>13</td>
        <td><p><b>cursor.fetchone()</b></p>
        <p>This method fetches the next row of a query result set, returning a single sequence, or None when no more data is available.</p>
        </td>
    </tr>
    <tr>
        <td>14</td>
        <td><p><b>cursor.fetchmany([size = cursor.arraysize])</b></p><p>This routine fetches the next set of rows of a query result, returning a list. An empty list is returned when no more rows are available. The method tries to fetch as many rows as indicated by the size parameter.</p></td>
    </tr>
    <tr>
        <td>15</td>
        <td><p><b>cursor.fetchall()</b></p>
        <p>This routine fetches all (remaining) rows of a query result, returning a list. An empty list is returned when no rows are available.</p></td>
    </tr>
</table>

<hr>
<a href="../../../module/9/logging" style="float:left;"> &laquo; Prev </a>
<a href="../sqlite3-parameterized" style="float:right;"> Next &raquo; </a>