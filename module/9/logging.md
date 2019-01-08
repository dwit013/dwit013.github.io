---
layout: page
---

# Module 9

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

# Debugging

## 9.3 Logging

If you’ve ever put a `print()` statement in your code to output some variable’s value while your program is running, you’ve used a form of _logging_ to debug your code. 

Logging is a great way to understand what’s happening in your program and in what order its happening. Python’s `logging` module makes it easy to create a record of custom messages that you write. These log messages will describe when the program execution has reached the logging function call and list any variables you have specified at that point in time. On the other hand, a missing log message indicates a part of the code was skipped and never executed.

### The logging Module

Import the logging module as

```python
import logging
```

With the logging module imported, you can use something called a “logger” to log messages that you want to see. By default, there are 5 standard levels indicating the severity of events. Each has a corresponding method that can be used to log events at that level of severity. The defined levels, in order of increasing severity, are the following:

<table>
    <thead>
        <th> Level </th>
        <th> Logging Function </th>
        <th> Description </th>
    </thead>
    <tbody>
        <tr>
            <td>DEBUG</td>
            <td>`logging.debug()`</td>
            <td>The lowest level. Used for small details. Usually you care about these messages only when diagnosing problems.</td>
        </tr>
        <tr>
            <td>INFO</td>
            <td>`logging.info()`</td>
            <td>Used to record information on general events in your program or confirm that things are working at their point in the program.
            </td>
        </tr>
        <tr>
            <td>WARNING</td>
            <td>`logging.warning()`</td>
            <td>Used to indicate a potential problem that doesn’t prevent the program from working but might do so in the future.</td>
        </tr>
        <tr>
            <td>ERROR</td>
            <td>`logging.error()`</td>
            <td>Used to record an error that caused the program to fail to do something.</td>
        </tr>
        <tr>
            <td>CRITICAL</td>
            <td>`logging.critical()`</td>
            <td>The highest level. Used to indicate a fatal error that has caused or is about to cause the program to stop running entirely.</td>
        </tr>
    </tbody>
</table>

The corresponding methods for each level can be called as shown in the following example:

```python
import logging

logging.debug('This is a debug message')
logging.info('This is an info message')
logging.warning('This is a warning message')
logging.error('This is an error message')
logging.critical('This is a critical message')
```

Output

    WARNING:root:This is a warning message
    ERROR:root:This is an error message
    CRITICAL:root:This is a critical message

The output shows the severity level before each message along with root, which is the name the logging module gives to its default logger. 

Notice that the debug() and info() messages didn’t get logged. This is because, by default, the logging module logs the messages with a severity level of WARNING or above. 

The benefit of logging levels is that you can change what priority of logging message you want to see.

### Basic Configurations

You can use the basicConfig(**kwargs) method to configure the logging:

Some of the commonly used parameters for basicConfig() are the following:

* level: The root logger will be set to the specified severity level.
* filename: This specifies the file.
* filemode: If filename is given, the file is opened in this mode. The default is a, which means append.
* format: This is the format of the log message.

By using the level parameter, you can set what level of log messages you want to record.

```python
import logging

logging.basicConfig(level=logging.DEBUG)
logging.debug('This will get logged')
```

All events at or above DEBUG level will now get logged.

    DEBUG:root:This will get logged

Similarly, for logging to a file rather than the console, filename and filemode can be used, and you can decide the format of the message using format. 

```python
import logging

logging.basicConfig(filename='app.log', filemode='w', format='%(name)s - %(levelname)s - %(message)s')
logging.warning('This will get logged to a file')
```

The message will look like below but will be written to a file named app.log instead of the console. 

    root - ERROR - This will get logged to a file

You can customize the root logger even further by using more parameters for basicConfig(), which can be found [here](https://docs.python.org/3/library/logging.html#logging.basicConfig).

> Note: Calling basicConfig() to configure the root logger works only if the root logger has not been configured before. Basically, this function can only be called once.

## Example

```python
import logging
logging.basicConfig(level=logging.DEBUG, format=' %(asctime)s - %(levelname)s - %(message)s')

logging.debug('Start of program')

def factorial(n):
    logging.debug('Start of factorial(%s)' % (n))
    total = 1
    for i in range(n + 1):
        total *= i
        logging.debug('i is ' + str(i) + ', total is ' + str(total))
    logging.debug('End of factorial(%s)' % (n))
    return total

print(factorial(5))

logging.debug('End of program')

```

Here, we use the `logging.debug()` function when we want to print log information. This `debug()` function will call `basicConfig()`, and a line of information will be printed. This information will be in the format we specified in `basicConfig()` and will include the messages we passed to `debug()`. 

The `print(factorial(5))` call is part of the original program, so the result is displayed even if logging messages are disabled.

The output of this program looks like this:

    2019-01-09 00:01:13,664 - DEBUG - Start of program
    2019-01-09 00:01:13,664 - DEBUG - Start of factorial(5)
    2019-01-09 00:01:13,665 - DEBUG - i is 0, total is 0
    2019-01-09 00:01:13,668 - DEBUG - i is 1, total is 0
    2019-01-09 00:01:13,670 - DEBUG - i is 2, total is 0
    2019-01-09 00:01:13,673 - DEBUG - i is 3, total is 0
    2019-01-09 00:01:13,675 - DEBUG - i is 4, total is 0
    2019-01-09 00:01:13,678 - DEBUG - i is 5, total is 0
    2019-01-09 00:01:13,680 - DEBUG - End of factorial(5)
    0
    2019-01-09 00:01:13,684 - DEBUG - End of program

The `factorial()` function is returning `0` as the factorial of `5`, which isn’t right. The `for` loop should be multiplying the value in `total` by the numbers from `1` to `5`. But the log messages displayed by `logging.debug()` show that the `i` variable is starting at `0` instead of `1`. Since zero times anything is zero, the rest of the iterations also have the wrong value for `total`. Logging messages provide a trail of breadcrumbs that can help you figure out when things started to go wrong.

Change the `for i in range(n + 1):` line to `for i in range(1, n + 1):`, and run the program again. The output will look like this:

    2019-01-09 00:10:40,650 - DEBUG - Start of program
    2019-01-09 00:10:40,651 - DEBUG - Start of factorial(5)
    2019-01-09 00:10:40,651 - DEBUG - i is 1, total is 1
    2019-01-09 00:10:40,654 - DEBUG - i is 2, total is 2
    2019-01-09 00:10:40,656 - DEBUG - i is 3, total is 6
    2019-01-09 00:10:40,659 - DEBUG - i is 4, total is 24
    2019-01-09 00:10:40,661 - DEBUG - i is 5, total is 120
    2019-01-09 00:10:40,661 - DEBUG - End of factorial(5)
    120
    2019-01-09 00:10:40,666 - DEBUG - End of program

The `factorial(5)` call correctly returns `120`. The log messages showed what was going on inside the loop, which led straight to the bug.

You can see that the `logging.debug()` calls printed out not just the strings passed to them but also a timestamp and the word _DEBUG_.

### Don’t Debug with print()

Typing `import logging` and `logging.basicConfig(level=logging.DEBUG, format= '%(asctime)s - %(levelname)s - %(message)s')` is somewhat unwieldy. You may want to use `print()` calls instead, but don’t give in to this temptation! Once you’re done debugging, you’ll end up spending a lot of time removing `print()` calls from your code for each log message. You might even accidentally remove some `print()` calls that were being used for non-log messages. 

The nice thing about log messages is that you’re free to fill your program with as many as you like, and you can always disable them later by adding a single `logging.disable(logging.CRITICAL)` call. Unlike `print()`, the `logging` module makes it easy to switch between showing and hiding log messages.

Log messages are intended for the programmer, not the user. The user won’t care about the contents of some dictionary value you need to see to help with debugging; use a log message for something like that. For messages that the user will want to see, like _File not found_ or _Invalid input, please enter a number_, you should use a `print()` call. You don’t want to deprive the user of useful information after you’ve disabled log messages.


The benefit of logging levels is that you can change what priority of logging message you want to see. Passing `logging.DEBUG` to the `basicConfig()` function’s `level` keyword argument will show messages from all the logging levels (DEBUG being the lowest level). But after developing your program some more, you may be interested only in errors. In that case, you can set `basicConfig()`’s `level` argument to `logging.ERROR`. This will show only ERROR and CRITICAL messages and skip the DEBUG, INFO, and WARNING messages.

### Disabling Logging

After you’ve debugged your program, you probably don’t want all these log messages cluttering the screen. The `logging.disable()` function disables these so that you don’t have to go into your program and remove all the logging calls by hand. You simply pass `logging.disable()` a logging level, and it will suppress all log messages at that level or lower. So if you want to disable logging entirely, just add `logging.disable(logging.CRITICAL)` to your program. For example, enter the following into the interactive shell:

```python
>>> import logging
>>> logging.basicConfig(level=logging.INFO, format=' %(asctime)s -** %(levelname)s - %(message)s')
>>> logging.critical('Critical error! Critical error!')
2019-01-09 00:20:43,054 - CRITICAL - Critical error! Critical error!
>>> logging.disable(logging.CRITICAL)
>>> logging.critical('Critical error! Critical error!')
>>> logging.error('Error! Error!')
```

Since `logging.disable()` will disable all messages after it, you will probably want to add it near the `import logging` line of code in your program. This way, you can easily find it to comment out or uncomment that call to enable or disable logging messages as needed.

<hr>
<a href="../exceptions" style="float:left;"> &laquo; Prev </a>
<a href="../../../module/9/logging" style="float:right;"> Next &raquo; </a>