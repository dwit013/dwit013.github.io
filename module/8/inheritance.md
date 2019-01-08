---
layout: page
---

## Module 8

<a href="../../../toc" style="float: right;" target="_blank">Table of Contents</a>

## Object-Oriented Programming

## 8.2 Inheritance

Inheritance is the process by which one class takes on the attributes and methods of another. Newly formed classes are called **child classes**, and the classes that child classes are derived from are called **parent classes**.

It’s important to note that child classes override _or_ extend the functionality (e.g., attributes and behaviors) of parent classes. In other words, child classes inherit all of the parent’s attributes and behaviors but can also specify different behavior to follow. The most basic type of class is an `object`, which generally all other classes inherit as their parent.

When you define a new class, Python 3 it implicitly uses `object` as the parent class. So the following two definitions are equivalent:

	class Dog(object):
	    pass

In Python 3, this is the same as:

	class Dog:
	    pass

### Dog Park Example

Let’s pretend that we’re at a dog park. There are multiple Dog objects engaging in Dog behaviors,each with different attributes. In regular-speak that means some dogs are running, while some are stretching and some are just watching other dogs. Furthermore, each dog has been named by its owner and, since each dog is living and breathing, each ages.

What’s another way to differentiate one dog from another? How about the dog’s breed:

	>>> class Dog:
	...     def __init__(self, breed):
	...         self.breed = breed
	...
	>>> spencer = Dog("German Shepard")
	>>> spencer.breed
	'German Shepard'
	>>> sara = Dog("Boston Terrier")
	>>> sara.breed
	'Boston Terrier'

Each breed of dog has slightly different behaviors. To take these into account, let’s create separate classes for each breed. These are child classes of the parent `Dog` class.

### Extending the Functionality of a Parent Class

Create a new file called `dog_inheritance.py`:

    # Parent class
	class Dog:
        # Class attribute
        species = 'mammal'

        # Initializer/Instance attributes
        def __init__(self, name, age):
            self.name = name
            self.age = age

        # Instance method
        def description(self):
            return "{} is {} years old".format(self.name, self.age)

        # Instance method
        def speak(self, sound):
            return "{} says {}".format(self.name, sound)

	# Child class (inherits from Dog class)
    class RussellTerrier(Dog):
        def run(self, speed):
            return "{} runs {}".format(self.name, speed)

	# Child class (inherits from Dog class)
    class Bulldog(Dog):
        def run(self, speed):
            return "{} runs {}".format(self.name, speed)

	# Child classes inherit attributes and
	# behaviors from the parent class
	jim = Bulldog("Jim", 12)
	print(jim.description())

	# Child classes have specific attributes
	# and behaviors as well
	print(jim.run("slowly"))

Output:

	Jim is 12 years old
	Jim runs slowly

We haven’t added any special attributes or methods to differentiate a `RussellTerrier` from a `Bulldog`, but since they’re now two different classes, we could for instance give them different class attributes defining their respective speeds.

### Parent vs. Child Classes

The `isinstance()` function is used to determine if an instance is also an instance of a certain parent class.

Add this to `dog_inheritance.py`:

	# Is jim an instance of Dog()?
	print(isinstance(jim, Dog))

	# Is julie an instance of Dog()?
	julie = Dog("Julie", 100)
	print(isinstance(julie, Dog))

	# Is johnny walker an instance of Bulldog()
	johnnywalker = RussellTerrier("Johnny Walker", 4)
	print(isinstance(johnnywalker, Bulldog))

	# Is julie and instance of jim?
	print(isinstance(julie, jim))

Output:

	('Jim', 12)
	Jim runs slowly
	True
	True
	False
	Traceback (most recent call last):
	  File "dog_inheritance.py", line 50, in <module>
	    print(isinstance(julie, jim))
	TypeError: isinstance() arg 2 must be a class, type, or tuple of classes and types

Make sense? Both `jim` and `julie` are instances of the `Dog()` class, while `johnnywalker` is not an instance of the `Bulldog()` class. Then as a sanity check, we tested if `julie` is an instance of `jim`, which is impossible since `jim` is an `instance` of a class rather than a class itself—hence the reason for the `TypeError`.

### Overriding the Functionality of a Parent Class

Remember that child classes can also override attributes and behaviors from the parent class. For examples:

	>>> class Dog:
	...     species = 'mammal'
	...
	>>> class SomeBreed(Dog):
	...     pass
	...
	>>> class SomeOtherBreed(Dog):
	...     species = 'reptile'
	...
	>>> frank = SomeBreed()
	>>> frank.species
	'mammal'
	>>> beans = SomeOtherBreed()
	>>> beans.species
	'reptile'

The `SomeBreed()` class inherits the `species` from the parent class, while the `SomeOtherBreed()` class overrides the `species`, setting it to `reptile`.

<hr>
<a href="../class-and-object" style="float:left;"> &laquo; Prev </a>
<a href="../../../module/9/exceptions" style="float:right;"> Next &raquo; </a>

