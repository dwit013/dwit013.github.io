---
layout: page
---

## Module 7

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## File Handling

## 7.1 Regular Expressions

A regular expression, regex or regexp is a sequence of characters that define a search pattern. 

The expression is a string of characters. There are two types of characters:

* Meta characters which have a special meaning, example square brackets ([])
* Regular characters which have a literal meaning, example lowercase characters ('a')

## Example

Say you want to search for cellphone numbers in a document full of text. You would define a regular expression for it as `(\+977-)?98[0-9]{8}$`.

* It matches cellnumbers starting with +977- or 98, and
* Having 8 digits after 98.

Fields of application range from validation to parsing/replacing strings, passing through translating data to other formats and web scraping.

Let us look at the operators and use case of regular expressions with examples:

## Anchors - ^ and $

    ^The        matches any string that starts with The   
    end$        matches any string that ends with 'end'
    ^The end$   matches exact string 'The end'
    world       matches any string with the text 'world'

## Quantifiers - *, +, ? and {}

    yipe*         matches a string that has yip followed by zero or more e
    yipe+         matches a string that has yip followed by one or more e
    yipe?         matches a string that has yip followed by zero or one e
    yipe{3}       matches a string that has yip followed by three e
    yipe{3,}      matches a string that has yip followed by three or more e
    yipe{3,6}     matches a string that has yip followed by three to six e
    yip(ye)*      matches a string that has yip followed by zero or more copies 
                  of the sequence ye

## OR operator - | and []

    yip(e|i)      matches a string that has yip followed by e or i
    yip[ei]       same as above  
    
## Character classes

    \d            matches a single character that is a digit
    \D            matches any character which is not a decimal digit
    \w            matches a word character (alphanumeric character plus underscore)
    \W            matches any character which is not a word character
    \s            matches a whitespace character (includes tabs and line breaks)
    \S            matches any character which is not a whitespace character
    .             matches any character
    \b            matches the empty string, but only at the beginning or end of a 
                  word              
    \B            matches the empty string, but only when it is not at the 
                  beginning or end of a word
    \A            matches only at the start of the string
    \Z            matches only at the end of the string

## Escaping characters

In order to be taken literally, you must escape the characters `^.[$()|*+?{\` with a backslash `\` as they have special meaning.

    \+977         matches the string '+977'

# Range

    [0-9]         matches a single digit from 0 to 9
    [a-zA-Z]      matches a letter from a to z or from A to Z
    [^a-zA-Z]     matches a string not containing a letter from a to z or A - Z

Here, `^` is used as a negation. 

# re Module

In Python, **re** module provides functions to use regular expressions.

## match function

The match function attempts to match regular expression pattern to the given string. It checks for a match only at the beginning of the string.

    re.match(pattern, string, flags=0)

Here

* pattern is the regular expression to be matched
* string is the string to be searched to match the pattern at the beginning of the string
* flags are modifiers 

The re.match function returns a match object on success, **None** on failure. 

## group

We use group(num) or groups() function of match object to get matched expression. 

Adding parentheses will create groups in the regex: ` (\+977-) ? (98[0-9]{8}$) `. Then you can use the group() match object method to grab the matching text from just one group. The first set of parentheses in a regex string will be group 1. The second set will be group 2 and so on.

* group(num) returns specific subgroup of matched object. The subgroup is specified by **num**. If **num** is not specified, it returns entire match.
* groups() return all matching subgroups in a tuple.

Example I

    matchObj = re.match('(\+977-)?(98[0-9]{8}$)', '9841234567')
    
    if matchObj:
        print ('Valid phone number: ', matchObj.group())
    else:
        print ('Invalid phone number')

Example II

    matchObj = re.match('(\+977-)?(98[0-9]{8}$)', '+977-9841234567')
    
    if matchObj:
        print ('Valid phone number.')
        print ('Country code: ', matchObj.group(1))
        print ('Phone Number: ', matchObj.group(2))
    else:
        print ('Invalid phone number')

## search function

Search function searches for first occurrence of regular expression pattern within the given string. While **match** checks for a match only at the beginning of the string, **search** checks for a match anywhere in the string.

    re.search(pattern, string, flags=0)

Here

* pattern is the regular expression to be searched
* string is the string to be searched to match the pattern anywhere in the string
* flags are modifiers 

The re.search function returns a match object on success, **None** on failure. 

    note = "Come to college tomorrow and call me at 9841234567"
    matchObj = re.search('(\+977-)?(98[0-9]{8}$)', note)
    
    if matchObj:
        print ('Phone number found: ', matchObj.group())
    else:
        print ('No phone number found.')
    
# Further Reading

* [re - Regular expression operations](https://docs.python.org/3/library/re.html)
* [Regular Expressions Info](https://www.regular-expressions.info/)

<hr>
<a href="../../../module/6/virtual-environment" style="float:left;"> &laquo; Prev </a>
<a href="../file-handling-basic" style="float:right;"> Next &raquo; </a>