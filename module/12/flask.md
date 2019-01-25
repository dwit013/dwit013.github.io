---
layout: page
---

# Module 12

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

# Flask

Flask is a lightweight micro framework for Python used to develop web applications. It provides features of basic URL routing and page rendering.

Flask is called a "micro" framework because Flask keeps it simple. It does not have any database abstraction, form validation or other extra features. Flask wants you to choose your own database abstraction layer, you own form validation package. It encourages **Configuration over Convention**. 

In this module, you will learn to create a simple website in Flask and learn about routing, using templates, generating static pages, and accessing request data. For a comprehensive tutorial visit [Flask's main website](http://flask.pocoo.org/docs/1.0/quickstart/).

## Installing Flask module

```bash
$ pip install flask
```

## Creating a simple Flask app

First of all, create a new project folder.

We will now create a simple "Hello World!" flask app. Create a new Python file `app.py` inside the project folder and write the following code.

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def home():
    return "Hello World!"
```

Now run the `app.py` file from the terminal using `python3 -m flask run` (For macOS/Linux) or `python -m flask run` (For Windows).

You will see an output similar to the following:

```bash
$ python3 -m flask run
 * Environment: production
   WARNING: Do not use the development server in a production environment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

Now, `Ctrl + click` on the link.

So what did we do in the above code. Let us dissect the code line by line.

* In line 1, we imported the **Flask** class from **flask** module. 
* Next we created an instance of the class **Flask** and gave it an arbitrary name *app*.
  The first argument denotes the name of the module or package we are using which is given by the dunder variable `__name__`. This argument tells Flask where to look for templates, static files, and so on.
* We then use the route() decorator to tell Flask what URL should trigger our function.
* Next the function is defined which is triggered by a URL. It generates URLs for that particular function, and returns the message we want to display in the user’s browser.

## Routing

Use the decorator `route()` to bind a function to a URL. 

Add the following route to `app.py`.

```python
@app.route('/user')
def hello_user():
    return "Hello DWIT"
```

You can make parts of the URL dynamic and attach multiple rules a function.

### Variable Rules

You can add variable sections to a URL by marking sections with `<variable_name>`. Your function then receives the `<variable_name>` as a keyword argument.

Add the following route to `app.py`.

```python
@app.route('/user/<name>')
def hello_user_with_name(name):
    return 'Hello %s' % name
```

Optionally, you can use a converter to specify the type of the argument like `<converter:variable_name>`.

```python
@app.route('/user/<int:user_id>')
def hello_user_with_id(user_id):
    return 'Hello User %d' % user_id
```

### Binding multiple URLs to a single function

You have written three different route decorators to basically do similar task i.e. "Say hello". You can instead bind all the URLs to a single function.

```python
@app.route('/user')
@app.route('/user/<username>')
@app.route('/user/<int:user_id>')
def hello_user(username=None, user_id=None):
    if username:
        return 'Hello %s' % username
    elif user_id:
        return 'Hello User %d' % user_id
    else:
        return "Hello, DWIT"
```

## Converter Types

<table>
    <thead>
        <th> Converter Type </th>
        <th> Description </th>
    </thead>
    <tbody>
        <tr>
            <td>string</td>
            <td>(default) accepts any text without a slash</td>
        </tr>
        <tr>
            <td>int</td>
            <td>accepts positive integers</td>
        </tr>
        <tr>
            <td>float</td>
            <td>accepts positive floating point values</td>
        </tr>
        <tr>
            <td>path</td>
            <td>similar to strings but accepts strings</td>
        </tr>
        <tr>
            <td>uuid</td>
            <td>accepts UUID strings</td>
        </tr>
    </tbody>
</table>

Until now we have only worked with plain text web pages. It is not a good idea to send HTML code in this approach. Instead we will separate HTML markup and our back end code. Flask uses **Templates** to create this abstraction. 

## Templates

A template is basically an HTML file with placeholders for values that the back end code provides during run time. Flask uses **Jinja2** as its default template engine which is installed along with **Flask** module.

To render a template we will use the `render_template()` method. For that we have to import the method from **flask** module. Add the following to the top of `app.py`.

```python
from flask import render_template
```

Templates are stored in a folder named **templates**. 

* Create a folder **templates** in your project directory.
* Create a new HTML file in the templates directory `hello.html`.
* And write the following code into the file.
  
```html
<!DOCTYPE html>
<html>
    <head>
        <title>Hello Page</title>
    </head>
    <body>
        <p>
        {% raw %}       
            {% if name %}
                <strong>Hello {{ name }}!</strong>.
            {% else %}
                What's your name? Provide it after /user/ in the URL.
            {% endif %}
        {% endraw %}
        </p>
    </body>
</html>
```

Now rewrite the above route as follows:

```python
@app.route('/user')
@app.route('/user/<username>')
@app.route('/user/<int:user_id>')
def hello_user(username=None, user_id=None):
    return render_template('hello.html', name=username)
```

And run the app. `python3 -m flask run`

## Static files

Web applications need static files such as CSS and Javascript files. In Flask, static files are stored in **static** folder and **Flask** has a built-in function to serve these static files.

* Create a folder **static** in your project directory.
* Create a new CSS file in the static directory `style.css`.
* And write the following CSS into the file.
  
```css
p {
    color: red;
    text-decoration: underline;
}
```

Now, add the following code in the `<head>` section of `hello.html` page.

```html
<link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='style.css')}}" />
```

`url_for('static', filename='style.css')` is used to generate URLs for static files. It uses the special 'static' endpoint name.

## Accessing Request Data

In a web application, client and server constantly communicate. In Flask, this communication is facilitated by the **request** object.

### The Request Object

Request object is built-in to Flask module and can be imported as follows:

```python
from flask import request
```

The current request method is available by using the **method** attribute.

Add the following code to `app.py`.

```python
@app.route('/login')
def login():
    return render_template('login.html')

@app.route('/auth', methods=['POST'])
def auth():
    username = request.form['username']
    password = request.form['password']

    if username == 'admin' and password == 'pass':
        return render_template('hello.html', name=username)
```

Create a new file `login.html` in templates folder and write the following.

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Login</title>
    </head>
    <body> 
        <form method="POST" action="auth">
            Username: <input name="username" type="text">
            Password: <input name="password" type="password">
            <input type="submit" value="Login">
        </form>
    </body>
</html>
```

Run the app and give it a try.

<hr>
<a href="../../../module/11/web-scraping" style="float:left;"> &laquo; Prev </a>
