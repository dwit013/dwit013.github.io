---
layout: page
---

## Module 8

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Object-Oriented Programming

## 8.1 Class and Object

Object-oriented Programming, or **OOP** for short, is a [programming paradigm](http://en.wikipedia.org/wiki/Programming_paradigm) which provides a means of structuring programs so that properties and behaviors are bundled into individual **objects**.

For instance, an object could represent a person with a name property, age, address, etc., with behaviors like walking, talking, breathing, and running. Or an email with properties like recipient list, subject, body, etc., and behaviors like adding attachments and sending.

Put another way, object-oriented programming is an approach for modeling concrete, real-world things like cars as well as relations between things like companies and employees, students and teachers, etc. OOP models real-world entities as software objects, which have some data associated with them and can perform certain functions.

Another common programming paradigm is **procedural programming** which structures a program like a recipe in that it provides a set of steps, in the form of functions and code blocks, which flow sequentially in order to complete a task.

The key takeaway is that objects are at the center of the object-oriented programming paradigm, not only representing the data, as in procedural programming, but in the overall structure of the program as well.

## Classes in Python

Focusing first on the data, each thing or object is an instance of some **class**.

The primitive data structures available in Python, like numbers, strings, and lists are designed to represent simple things like the cost of something, the name of a poem, and your favorite colors, respectively.

What if you wanted to represent something much more complicated?

For example, let’s say you wanted to track a number of different animals. If you used a list, the first element could be the animal’s name while the second element could represent its age.

How would you know which element is supposed to be which? What if you had 100 different animals? Are you certain each animal has both a name and an age, and so forth? What if you wanted to add other properties to these animals? This lacks organization, and it’s the exact need for **classes**.

Classes are used to create new user-defined data structures that contain arbitrary information about something. In the case of an animal, we could create an `Animal()` class to track properties about the Animal like the name and age.

It’s important to note that a class just provides structure—it’s a blueprint for how something should be defined, but it doesn’t actually provide any real content itself. The `Animal()` class may specify that the name and age are necessary for defining an animal, but it will not actually state what a specific animal’s name or age is.

It may help to think of a class as an **idea** for how something should be defined.

## Python Objects (Instances)

While the class is the blueprint, an **instance** is a copy of the class with _actual_ values, literally an object belonging to a specific class. It’s not an idea anymore; it’s an actual animal, like a dog named Roger who’s eight years old.

Put another way, a class is like a form or questionnaire. It defines the needed information. After you fill out the form, your specific copy is an instance of the class; it contains actual information relevant to you.

You can fill out multiple copies to create many different instances, but without the form as a guide, you would be lost, not knowing what information is required. Thus, before you can create individual instances of an object, we must first specify what is needed by defining a class.

## How To Define a Class in Python

Defining a class is simple in Python:

	class Dog:
	    pass

You start with the `class` keyword to indicate that you are creating a class, then you add the name of the class (using [CamelCase notation](https://en.wikipedia.org/wiki/Camel_case), starting with a capital letter.)

Also, we used the Python keyword `pass` here. This is very often used as a place holder where code will eventually go. It allows us to run this code without throwing an error.

### Instance Attributes

All classes create objects, and all objects contain characteristics called attributes (referred to as properties in the opening paragraph). Use the `__init__()` method to initialize (e.g., specify) an object’s initial attributes by giving them their default value (or state). This method must have at least one argument as well as the `self` variable, which refers to the object itself (e.g., Dog).

	class Dog:
	    # Initializer/Instance Attributes
	    def __init__(self, name, age):
			self.name = name
			self.age = age

In the case of our `Dog()` class, each dog has a specific name and age, which is obviously important to know for when you start actually creating different dogs. Remember: the class is just for defining the Dog, not actually creating _instances_ of individual dogs with specific names and ages.

Similarly, the `self` variable is also an instance of the class. Since instances of a class have varying values we could state `Dog.name = name` rather than `self.name = name`. But since not all dogs share the same name, we need to be able to assign different values to different instances. Hence the need for the special `self` variable, which will help to keep track of individual instances of each class.

> **NOTE**: You will never have to call the `__init__()` method; it gets called automatically when you create a new ‘Dog’ instance.

### Class Attributes

While instance attributes are specific to each object, class attributes are the same for all instances—which in this case is _all_ dogs.

	class Dog:
	    # Class Attribute
	    species \= 'mammal'

	    # Initializer/Instance Attributes
	    def __init__(self, name, age):
			self.name = name
			self.age = age

So while each dog has a unique name and age, every dog will be a mammal.

Let’s create some dogs…

### Instantiating Objects

Instantiating is a fancy term for creating a new, unique instance of a class.

For example:

	>>> class Dog:
			pass
	>>>
	>>> Dog()
		<main__.Dog object at 0x1004ccc50>
	>>> a = Dog()
	>>> b = Dog()
	>>> a == b
	False

We started by defining a new `Dog()` class, then created two new dogs, each assigned to different objects. So, to create an instance of a class, you use the the class name, followed by parentheses. Then to demonstrate that each instance is actually different, we instantiated two more dogs, assigning each to a variable, then tested if those variables are equal.

What do you think the type of a class instance is?

	>>> class Dog:
	...     pass
	...
	>>> a = Dog()
	>>> type(a)
	<class '__main__.Dog'>

Let’s look at a slightly more complex example.

	class Dog:
	    # Class Attribute
	    species = 'mammal'

	    # Initializer/Instance Attributes
	    def __init__(self, name, age):
			self.name = name
			self.age = age

	# Instantiate the Dog object
	bruno = Dog("Bruno", 5)
	mikey = Dog("Mikey", 6)

	# Access the instance attributes
	print("{} is {} and {} is {}.".format(bruno.name, bruno.age, mikey.name, mikey.age))

	# Is Bruno a mammal?
	if bruno.species == "mammal":
	    print("{0} is a {1}!".format(bruno.name, bruno.species))

> **NOTE**: Notice how we use dot notation to access attributes from each object.

Save this as `dog_class.py`, then run the program. You should see:

	Bruno is 5 and Mikey is 6.
	Bruno is a mammal!

### What’s Going On?

We created a new instance of the `Dog()` class and assigned it to the variable `bruno`. We then passed it two arguments, `"Bruno"` and `5`, which represent that dog’s name and age, respectively.

These attributes are passed to the `__init__` method, which gets called any time you create a new instance, attaching the name and age to the object. You might be wondering why we didn’t have to pass in the `self` argument.

This is Python magic; when you create a new instance of the class, Python automatically determines what `self` is (a Dog in this case) and passes it to the `__init__` method.

## Instance Methods

Instance methods are defined inside a class and are used to get the contents of an instance. They can also be used to perform operations with the attributes of our objects. Like the `__init__` method, the first argument is always `self`:

	class Dog:
		# Class Attribute
	    species = 'mammal'

	    # Initializer/Instance Attributes
	    def __init__(self, name, age):
			self.name = name
			self.age = age

	    # instance method
	    def description(self):
			return "{} is {} years old".format(self.name, self.age)

	    # instance method
	    def speak(self, sound):
			return "{} says {}".format(self.name, sound)

	# Instantiate the Dog object
	mikey = Dog("Mikey", 6)

	# call our instance methods
	print(mikey.description())
	print(mikey.speak("Gruff Gruff"))

Save this as `dog_instance_methods.py`, then run it:

	Mikey is 6 years old
	Mikey says Gruff Gruff

In the latter method, `speak()`, we are defining behavior. What other behaviors could you assign to a dog? Look back to the beginning paragraph to see some example behaviors for other objects.

### Modifying Attributes

You can change the value of attributes based on some behavior:

	>>> class Email:
	...     def __init__(self):
	...         self.is_sent = False
	...     def send_email(self):
	...         self.is_sent = True
	...
	>>> my_email = Email()
	>>> my_email.is_sent
	False
	>>> my_email.send_email()
	>>> my_email.is_sent
	True

Here, we added a method to send an email, which updates the `is_sent` variable to `True`.

<hr>
<a href="../../../module/7/file-handling-advanced" style="float:left;"> &laquo; Prev </a>
<a href="../inheritance" style="float:right;"> Next &raquo; </a>

