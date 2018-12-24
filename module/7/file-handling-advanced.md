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

**csv.reader**
The csv.reader module takes the following parameters:

* csvfile: This is usually an object which supports the iterator protocol and usually returns a string each time its __next__() method is called.
* dialect='excel': An optional parameter used to define a set of parameters specific to a particular CSV dialect.
* fmtparams: An optional parameter that can be used to override existing formatting parameters.
Here is an example of how to use the csv.reader module.

	import csv
 
	with open('example.csv', newline='') as File:
	    reader = csv.reader(File)
	    for row in reader:
		print(row)

**csv.writer module**
This module is similar to the csv.reader module and is used to write data to a CSV. It takes three parameters:

* csvfile: This can be any object with a write() method.
* dialect='excel': An optional parameter used to define a set of parameters specific to a particular CSV.
* fmtparam: An optional parameter that can be used to override existing formatting parameters.


