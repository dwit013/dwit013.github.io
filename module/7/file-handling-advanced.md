---
layout: page
---

## Module 7

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## File Handling

## 7.3 File Handling Advanced

### CSV File

A CSV (comma separated values) file allows data to be saved in a tabular structure with a .csv extension. 

The CSV format is the most commonly used import and export format for databases and spreadsheets. CSV files are very easy to work with programmatically. 

	CSV File

	column 1 name, column 2 name, column 3 name, ...
	first row data 1, first row data 2, first row data 3, ...
	second row data 1, second row data 2, second row data 3, ...

Usually the first line is the name of the data columns and every subsequent line after that is the actual data.

Generally, comma is used the separate the data values and it is known as the delimeter. However, other delimeters may also be used such as colon (:), tab (\t) and semi-colon (;).

## CSV module

The CSV module is import as

	import csv

The CSV module has several functions and classes available for reading and writing CSVs, and they include:

* csv.reader function
* csv.writer function
* csv.Dictwriter class
* csv.DictReader class

### csv.reader

The csv reader function reads data from a text file which is opened as a **file** object using open() function. 

Syntax:

	csv.reader(csvfile, dialect='excel', **fmtparams)

* Return a reader object which will iterate over lines in the given csvfile.  
* An optional dialect parameter can be given which is used to define a set of parameters specific to a particular CSV dialect.
* The other optional fmtparams keyword arguments can be given to override individual formatting parameters in the current dialect.

A short usage example:

	student.csv file

	name, batch, roll_no
	John Doe, 2019, 532
	Jane Doe, 2020, 623
	Adam Smith, 2021, 712

	import csv
	with open('student.csv', newline='') as csvfile:
		csv_reader = csv.reader(csvfile, delimiter=',')
		line_count = 0
		for row in csv_reader:
			if line_count == 0:
				print(f'Column names are {", ".join(row)}')
			else:
				print(f'{row[2]}. {row[0]} is from Class of {row[1]}.')
			line_count += 1

Output

	Column names are name, batch, roll_no
	532. John Doe is from Class of 2019.
	623. Jane Doe is from Class of 2020.
	712. Adam Smith is from Class of 2021.

### Optional CSV reader parameters

* delimiter specifies the character used to separate each field. The default is the comma (',').
 `delimiter=':'`
* quotechar specifies the character used to surround fields that contain the delimiter character. The default is a double quote (' " '). `quotechar='\t'`
* escapechar specifies the character used to escape the delimiter character, in case quotes aren’t used. The default is no escape character. `escapechar='\'`

### csv.writer

The csv writer function writes data from a text file which is opened as a **file** object using open() function.

Syntax:

	csv.writer(csvfile, dialect='excel', **fmtparams)

* Return a writer object responsible for converting the user’s data into delimited strings on the given file-like object. 
* An optional dialect parameter can be given which is used to define a set of parameters specific to a particular CSV dialect.
* The other optional fmtparams keyword arguments can be given to override individual formatting parameters in the current dialect.

We write to a CSV file using a writer object and the `.write_row()` method:

A short usage example:

	import csv

	with open('student.csv', mode='w') as student_file:
		csv_writer = csv.writer(student_file, delimiter=',')

		csv_writer.writerow(['John Doe', '2019', '532'])
		csv_writer.writerow(['Jane Doe', '2020', '623'])
		csv_writer.writerow(['Adam Smith', '2021', '712'])

<hr>
<a href="../file-handling-basic" style="float:left;"> &laquo; Prev </a>
<a href="../../../module/8/class-and-object" style="float:right;"> Next &raquo; </a>


	

