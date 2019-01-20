---
layout: page
---

# Module 11

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

# Web Scraping

Web scraping is downloading content from the web and processing it. It the overall process of downloading structured data from the web, filtering the required data and passing the data for further processing.

Web scraping focuses more on the transformation of unstructured data on the web, typically in HTML format, into structured data that can be stored and analyzed in a central local database or spreadsheet. (Wikipedia)

> Notice: You should be careful when downloading content from other web pages. The legality of the procedure varies from country to country and company to company. Check the website's site policies and terms of use.

We will scrape the TU's CSIT website and get notices related to B. Sc. CSIT course.

Before proceeding further, let us study the HTML document we will scrape. We must study the document structure in order to extract the required information. 

We can view the HTML structure in Google Chrome using Google's Developer tools (`Press Ctrl + Shift + I`).

## Required Modules

* requests for HTTP requests
* BeautifulSoup4 for handling HTML processing
* re for string matching

```bash
$ pip install requests
$ pip install beautifulsoup4
$ pip install re
```

Now, create a new file named `scrapper.py` and import the following code.

```python
import requests, re
from bs4 import BeautifulSoup
```

Next we will use `requests` module's get method to get the content from a website.

```python
url = 'https://www.tuiost.edu.np/'
raw_html = requests.get(url)
print (raw_html.text)
```

* The `get` method returns a Response object which contains all the information we need.

[Read more about requests](http://docs.python-requests.org/en/master/user/quickstart/)

Next we will pass the response body as bytes to the BeautifulSoup constructor to parse the HTML document.

```python
html = BeautifulSoup(raw_html.content, 'html.parser')
```

Beautiful Soup is a Python library for pulling data out of HTML and XML files.
To parse a document, we can pass it into the BeautifulSoup constructor in a string or as non-text content.

Next we will use `find` and `select` method of BeautifulSoup object to select a particular HTML element with id='notices' and then further select all the anchor tags.

```python
notice_section = html.find(id="notices")
links = notice_section.select('a')
```

If you print the `notice_section` you will see the HTML code inside of `<section id='notices'>`. Similarly, with `print(links)` you will get a list of all the anchor tags inside the `notice_section`. 

If you check the type of **links**, we see that it a <TAG> object.

We have narrowed down the information to the links in the notice section where our required notice lies.

Next, write the following code.

```python
for link in links:
    if link.attrs['class'] != 'page-link':
        if link.b:
            print(link.b.text + " => " + link.attrs['href'])
```

Here, we will loop through all the anchor tags we acquired in links.

Here, we will filter out the links with actual notices by not including the pagination links. By studying the HTML document, we know that the pagination links have the class 'page-link'. We can exclude the links with this class with a simple string comparison (`link.attrs['class'] != 'page-link':`).

We are accessing the class value by using `attrs` attribute of the <TAG> object link.

Now we will filter out only notices related to **B. Sc. CSIT** using regular expression **module re** as follows:

```python
for link in links:
    if link.attrs['class'] != 'page-link':
        if link.b:
            matchObj = re.match('B.Sc. CSIT', link.b.text)
            if matchObj:
                print(link.b.text + " => " + link.attrs['href'])
            else:
                pass
```

<hr>
<a href="../../../module/10/sqlite3-parameterized" style="float:left;"> &laquo; Prev </a>
<a href="" style="float:right;"> Next &raquo; </a>