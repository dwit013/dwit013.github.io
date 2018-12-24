---
layout: page
---

## What Is a CSV File?

A CSV (comma separated values) file allows data to be saved in a tabular structure with a .csv extension. CSV files have been used extensively in e-commerce applications because they are considered very easy to process. Some of the areas where they have been used include:

* importing and exporting customer data
* importing and exporting products
* exporting orders
* exporting e-commerce analytic reports

## Where Do CSV Files Come From?

The CSV format is the most commonly used import and export format for databases and spreadsheets. This tutorial will give a detailed introduction to CSV’s and the modules and classes available for reading and writing data to CSV files. It will also cover a working example to show you how to read and write data to a CSV file in Python.

## Reader and Writer Modules
The CSV module has several functions and classes available for reading and writing CSVs, and they include:

* csv.reader function
* csv.writer function
* csv.Dictwriter class
* csv.DictReader class

## Module Contents
The csv module defines the following functions:

##csv.reader
Syntax:

	csv.reader(csvfile, dialect='excel', **fmtparams)

* Return a reader object which will iterate over lines in the given csvfile. csvfile can be any object which supports the iterator protocol and returns a string each time its __next__() method is called — file objects and list objects are both suitable. If csvfile is a file object, it should be opened with **newline=''**. 
* An optional dialect parameter can be given which is used to define a set of parameters specific to a particular CSV dialect.
* The other optional fmtparams keyword arguments can be given to override individual formatting parameters in the current dialect.

A short usage example:

	>>> import csv
	>>> with open('eggs.csv', newline='') as csvfile:
	...     spamreader = csv.reader(csvfile, delimiter=' ', quotechar='|')
	...     for row in spamreader:
	...         print(', '.join(row))
	Spam, Spam, Spam, Spam, Spam, Baked Beans
	Spam, Lovely Spam, Wonderful Spam

##csv.writer
Syntax:

	csv.writer(csvfile, dialect='excel', **fmtparams)

* Return a writer object responsible for converting the user’s data into delimited strings on the given file-like object. csvfile can be any object with a write() method. If csvfile is a file object, it should be opened with newline=''.
* An optional dialect parameter can be given which is used to define a set of parameters specific to a particular CSV dialect.
* The other optional fmtparams keyword arguments can be given to override individual formatting parameters in the current dialect.

A short usage example:

	>>> import csv
	>>> with open('eggs.csv', 'w', newline='') as csvfile:
	...    spamwriter = csv.writer(csvfile, delimiter=' ',
	...	                    quotechar='|', quoting=csv.QUOTE_MINIMAL)
	...    spamwriter.writerow(['Spam'] * 5 + ['Baked Beans'])
	...    spamwriter.writerow(['Spam', 'Lovely Spam', 'Wonderful Spam'])



	

