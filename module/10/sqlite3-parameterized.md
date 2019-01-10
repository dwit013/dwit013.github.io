---
layout: page
---

# Module 10

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

# Database

## 10.2 SQLite Parameterized Queries

Consider the previous INSERT operation.

```python
c.execute("""INSERT INTO student VALUES (
        001, 'John', 'Doe', 2021
    )""")
```

Here the values to be inserted into the table are static. We can make the values dynamic by using format function.

```python
id, first_name, last_name, batch = 003, 'Rob', 'Green', 2022

c.execute("""INSERT INTO student VALUES (
        {}, `{}`, `{}`, {}
    )""".format(id, first_name, last_name, batch))
```

This is a bad practice when using database. If you are accepting any values from the end-user, then the above code is vulnerable to SQL injection. SQL injection is a code injection technique that might destroy your database.

To protect from SQL injection, you can use parameters/placeholders. Parameters are values that are added to a query at execution time, in a controlled manner.

The database engine checks each parameter to ensure that it is correct for its column and are treated literally, and not as part of the query to be executed.

The sqlite3 module supports two kinds of placeholders: question marks and named placeholders (named style). We will understand better with the following examples.

## Using question mark

We can use question mark symbol to act as a placeholder for the data to be passed into the query.

```python

id, first_name, last_name, batch = 004, 'Mia', 'Sanchez', 2020

c.execute("""INSERT INTO student VALUES 
        (?, ?, ?, ?)""", 
        (id, first_name, last_name, batch))
```

Here each question mark is associated with a variable declared later in the function. The end-user cannot make any modification to the query. Hence, the query behaves as specified an not in any other ways. 

## Using named placeholders

We can also use named placeholder to act as a placeholder for the data to be passed into the query.

```python
id, first_name, last_name, batch = 005, 'Bob', 'Cole', 2022

c.execute("""INSERT INTO student VALUES 
    (:id, :first, :last, :batch)""",
    {'id': id, 'first': first, 'last': last, 'batch': batch})
```

<hr>
<a href="../sqlite3" style="float:left;"> &laquo; Prev </a>
<a href="../sqlite3-parameterized" style="float:right;"> Next &raquo; </a>