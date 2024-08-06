# Object-Oriented Programming (OOP) Vocabulary

## Class
A class is a blueprint consisting of methods and attributes. It defines the structure and behavior that objects created from the class will have.

## Object
An object is an instance of a class. It represents a specific realization of the class, which can be thought of as something tangible or abstract, such as a yellow pencil or a concept like a network node.

## Attribute
An attribute is a descriptor or characteristic of a class or object. Examples include color, length, and size, which can have specific values like blue, 3 inches, or large.

## Method
A method is an action that a class or object can perform. It defines the operations that can be carried out on or by the object.

## OOP
OOP stands for object-oriented programming, a programming paradigm that uses objects and classes to structure code.

## Encapsulation
Encapsulation is a core concept in OOP that involves combining functions and data into a single entity, or class. It allows hiding the internal implementation details, similar to how libraries like scikit-learn abstract away the details of machine learning algorithms.

*In English, attributes may also be referred to as properties, descriptions, features, qualities, traits, or characteristics, all conveying the same concept.*

# Object-Oriented Programming (OOP) Syntax

## Function versus Method
In Python, both functions and methods use the `def` keyword and have inputs and outputs. The key difference is that a method is defined within a class and operates on instances of that class, while a function is defined outside of a class. For instance, `__init__` is not a function but a method because it is defined within a class and initializes the class's attributes.

## What is `self`?
In OOP, `self` is a reference to the instance of the class on which a method is being called. It differentiates between instances by pointing to the specific object. For example, in the following code:

shirt_one = Shirt('red', 'S', 'short-sleeve', 15)
shirt_two = Shirt('yellow', 'M', 'long-sleeve', 20)
When you call shirt_one.change_price(12), Python uses self to refer to shirt_one within the change_price method:
def change_price(self, new_price):
    self.price = new_price
This way, Python knows to update the price attribute of shirt_one rather than shirt_two. The self parameter is automatically passed to methods when they are called, and while it is just a convention, using self is standard practice to avoid confusion.

self acts as a reference to the current instance of the class. When you create an object from a class, self allows methods within the class to access and modify the instance's attributes and other methods. When you call a method on an object, Python automatically passes the instance as the first argument to the method. This instance is received by self. For example, if you call shirt_one.change_price(12), shirt_one is implicitly passed as self to the change_price method.

# Set and Get Methods

The last part of the video mentioned that accessing attributes in Python can be somewhat different than in other programming languages like Java and C++. This section goes into further detail.

The `Shirt` class has a method to change the price of the shirt: `shirt_one.change_price(20)`. In Python, you can also change the values of an attribute with the following syntax:

```python
shirt_one.price = 10
shirt_one.price = 20
shirt_one.color = 'red'
shirt_one.size = 'M'
shirt_one.style = 'long_sleeve'
```

This code accesses and changes the price, color, size, and style attributes directly. Accessing attributes directly would be frowned upon in many other languages, but not in Python. Instead, the general object-oriented programming convention is to use methods to access attributes or change attribute values. These methods are called set and get methods or setter and getter methods.

A get method is for obtaining an attribute value, and a set method is for changing an attribute value. If you were writing a Shirt class, you could use the following code:
```python
class Shirt:
    def __init__(self, shirt_color, shirt_size, shirt_style, shirt_price):
        self._price = shirt_price

    def get_price(self):
        return self._price

    def set_price(self, new_price):
        self._price = new_price
```
Instantiating and using an object might look like the following code:
```
shirt_one = Shirt('yellow', 'M', 'long-sleeve', 15)
print(shirt_one.get_price())
shirt_one.set_price(10)
```

In the class definition, the underscore in front of price is a somewhat controversial Python convention. In other languages like C++ or Java, price could be explicitly labeled as a private variable. This would prohibit an object from accessing the price attribute directly like shirt_one._price = 15. Unlike other languages, Python does not distinguish between private and public variables. Therefore, there is some controversy about using the underscore convention as well as get and set methods in Python. Why use get and set methods in Python when Python wasn't designed to use them?

At the same time, you'll find that some Python programmers develop object-oriented programs using get and set methods anyway. Following the Python convention, the underscore in front of price is to let a programmer know that price should only be accessed with get and set methods rather than accessing price directly with shirt_one._price. However, a programmer could still access _price directly because there is nothing in the Python language to prevent the direct access.

To reiterate, a programmer could technically still do something like shirt_one._price = 10, and the code would work. But accessing price directly, in this case, would not be following the intent of how the Shirt class was designed.

One of the benefits of set and get methods is that, as previously mentioned in the course, you can hide the implementation from your user. Perhaps, originally, a variable was coded as a list and later became a dictionary. With set and get methods, you could easily change how that variable gets accessed. Without set and get methods, you'd have to go to every place in the code that accessed the variable directly and change the code.


# Attributes

There are some drawbacks to accessing attributes directly versus writing a method for accessing attributes.

In terms of object-oriented programming, the rules in Python are a bit looser than in other programming languages. As previously mentioned, in some languages, like C++, you can explicitly state whether or not an object should be allowed to change or access an attribute's values directly. Python does not have this option.

Why might it be better to change a value with a method instead of directly? Changing values via a method gives you more flexibility in the long term. What if the units of measurement change, like if the store was originally meant to work in US dollars and now has to handle Euros? Here's an example:

Example: Dollars versus Euros
If you've changed attribute values directly, you'll have to go through your code and find all the places where US dollars were used, such as in the following:
```shirt_one.price = 10 # US dollars```
If you had used a method, then you would only have to change the method to convert from dollars to Euros:
```def change_price(self, new_price):
    self.price = new_price * 0.81 # convert dollars to Euros

shirt_one.change_price(10)
```

For the purposes of this introduction to object-oriented programming, you don't need to worry about updating attributes directly versus with a method; however, if you decide to further your study of object-oriented programming, especially in another language such as C++ or Java, you'll have to take this into consideration.

# Modularized Code

Thus far in the lesson, all of the code has been in Jupyter Notebooks. For example, in the previous exercise, a code cell loaded the Shirt class, which gave you access to the Shirt class throughout the rest of the notebook.

If you were developing a software program, you would want to modularize this code. You would put the Shirt class into its own Python script, which you might call shirt.py. In another Python script, you would import the Shirt class with a line like:
```
from shirt import Shirt
```

# The Gaussian Class
Important formulae:
1. Gaussian distribution formulas
- probability density function
2. Binomial distribution formulas
- mean
- variance
- standard deviation
- probability density function

# Magic Methods

Magic methods, also known as dunder (double underscore) methods, are special methods in Python that begin and end with double underscores (`__`). They are used to define the behavior of objects for built-in operations and functions. Here’s an overview of some common magic methods:

## Common Magic Methods

- `__init__`: The constructor method. It initializes a newly created object. For example:
  ```python
  def __init__(self, name, age):
      self.name = name
      self.age = age
  ```
- `__str__`: Defines the string representation of an object. This method is called by the str() function and print() function to get a readable string representation of the object. For example:
```
def __str__(self):
    return f'{self.name}, {self.age} years old'
```

- `__repr__`: Defines the official string representation of an object that is ideally unambiguous and could be used to recreate the object. It is called by the repr() function and in the interactive interpreter. For example:
```
def __repr__(self):
    return f'Shirt(name={self.name!r}, age={self.age!r})'
```
- `__len__`: Defines the behavior of the len() function. It should return the length or size of the object. For example:
```
def __len__(self):
    return len(self.items)
```

- `__getitem__`: Allows access to an item using the indexing operator (`[]`). For example:
```
def __getitem__(self, index):
    return self.items[index]
```

- `__setitem__`: Allows setting an item using the indexing operator (`[]`). For example:
```
def __setitem__(self, index, value):
    self.items[index] = value
```
- `__delitem__`: Allows deletion of an item using the indexing operator ([]). For example:
```
def __delitem__(self, index):
    del self.items[index]
```

- `__add__`: Defines the behavior of the + operator. For example:
```
def __add__(self, other):
    return self.value + other.value
```

- `__eq__`: Defines the behavior of the equality operator (`==`). For example:
```
def __eq__(self, other):
    return self.value == other.value
```

- `__call__`: Allows an object to be called as if it were a function. For example:
```
def __call__(self, *args, **kwargs):
    return self.execute(*args, **kwargs)
```

Magic methods allow objects to interact with Python's built-in functions and operators. They enable objects to be used in a more intuitive and natural way, such as using arithmetic operators, indexing, and function calls.

By implementing these methods, you can control how your objects behave in different contexts, making your classes more versatile and expressive.

# Inheritance in Python

Inheritance is a fundamental concept in object-oriented programming (OOP) that allows a class (known as a child or subclass) to inherit attributes and methods from another class (known as a parent or superclass). This promotes code reuse and establishes a natural hierarchy between classes.

## Basic Inheritance

To define a class that inherits from another class, use the following syntax:

```
class ParentClass:
    def __init__(self, value):
        self.value = value

    def display(self):
        print(f"Value: {self.value}")

class ChildClass(ParentClass):
    def __init__(self, value, extra_value):
        super().__init__(value)
        self.extra_value = extra_value

    def display_extra(self):
        print(f"Extra Value: {self.extra_value}")
```
In this example, `ChildClass` inherits from `ParentClass` and has access to its attributes and methods. The `super()` function is used to call the parent class's `__init__` method.

## Method Overriding

A child class can override methods from the parent class to provide a specific implementation:
```
class ParentClass:
    def greet(self):
        print("Hello from Parent")

class ChildClass(ParentClass):
    def greet(self):
        print("Hello from Child")

child = ChildClass()
child.greet()  # Output: Hello from Child
```

In this case, the greet method in `ChildClass` overrides the greet method in `ParentClass`.

### Using `super()`

The `super()` function is used to call methods from the parent class within the child class. It helps in accessing the parent class's methods and initializing its attributes:
```
class ParentClass:
    def __init__(self, value):
        self.value = value

    def display(self):
        print(f"Value: {self.value}")

class ChildClass(ParentClass):
    def __init__(self, value, extra_value):
        super().__init__(value)
        self.extra_value = extra_value

    def display(self):
        super().display()
        print(f"Extra Value: {self.extra_value}")

child = ChildClass(10, 20)
child.display()
# Output:
# Value: 10
# Extra Value: 20
```

## Multiple Inheritance

```
class A:
    def method_a(self):
        print("Method A")

class B:
    def method_b(self):
        print("Method B")

class C(A, B):
    pass

obj = C()
obj.method_a()  # Output: Method A
obj.method_b()  # Output: Method B
```
In this example, class `C` inherits from both `A` and `B`, gaining access to methods from both parent classes.

# Windows vs. macOS vs. Linux

Linux, Windows, and macOS are different operating systems with their own unique features and command line interfaces. Understanding the differences between these can help you navigate and use each system effectively.

## Linux

- **Open Source**: Linux is free and open source, meaning anyone can view, modify, and distribute its source code.
- **Command Line**: Linux uses a command line interface (CLI) similar to the one in the Udacity classroom workspaces. Commands are often executed in the Terminal.
- **Workspace Advantage**: In the classroom workspace, you have full control over the environment, including installing and modifying software. If something goes wrong, you can reset the workspace, but ensure to backup your code files to avoid loss.

## macOS

- **Unix-Based**: macOS is also Unix-based, which means it shares similarities with Linux. Commands used in macOS's Terminal are often the same as those in Linux.
- **Terminal**: The Terminal application in macOS allows you to execute commands similarly to Linux. This is useful for running scripts or performing system operations.

## Windows

- **Proprietary**: Windows is owned by Microsoft and is a closed-source operating system. It is not open to the same level of customization as Linux.
- **Console**: Windows uses the Command Prompt (Console) for command-line operations. Commands may differ from those in Linux and macOS. You may need to search for equivalent commands or use PowerShell for more advanced functionality.

### Summary

While Linux and macOS offer similar command-line interfaces, Windows uses different commands and interfaces. When working in classroom workspaces, the environment is Linux-based, so ensure you understand the differences if you need to run commands locally on a different operating system. Always back up your code files before resetting any workspace to avoid data loss.

# Virtual Python Environments

When working with Python, managing your environment is crucial, especially when dealing with packages and dependencies. Virtual environments allow you to isolate your Python projects, avoiding conflicts between package versions and maintaining a clean workspace.

## Conda

Conda is a versatile environment manager and package manager. It simplifies the process of installing and managing Python packages and environments, especially for data science projects. 

**Commands:**
```
conda create --name environmentname
source activate environmentname
conda install numpy
```

> Advantages:
> 1. Handles both packages and environments.
> 2. Useful for data science due to its support for non-Python libraries.
> Disadvantages:
> 1. Can be complex for general Python software development.
> 2. May require additional setup to integrate with pip for installing packages.

## Venv and Pip

`venv` is a built-in environment manager for Python 3, and `pip` is a package manager for Python. `pip` can only manage Python packages, while `conda` is more comprehensive.

``` 
python3 -m venv environmentname
source environmentname/bin/activate
pip install numpy
```

> Advantages:
> 1. `venv` is simple and built into Python 3.
> 2. `pip` is straightforward for managing Python packages.
> Disadvantages:
> 1. `pip` doesn't handle non-Python dependencies.
> 2. Requires managing environments separately from package installation.

## Choosing Between Conda and Venv

The choice between `venv` and `conda` depends on your project needs:

- Conda is preferred for data science projects due to its comprehensive package management, including non-Python libraries.
- Venv with `pip` is ideal for generic Python software development.

> Note: When using conda, if you install a package with pip after creating the conda environment, ensure that pip installs packages within the conda environment:
```conda create --name environmentname pip```
Using `venv` with `pip` generally works as expected without such concerns.

## Instructions for Venv

For setting up virtual environments with venv:

- Python 3.3+ comes with `venv` preinstalled.
- To create a virtual environment: `python3 -m venv env`.
- Activate it: `source env/bin/activate`.
- Use `pip` to install packages.

You can practice creating and using virtual environments in your classroom workspace. Remember to download or commit your code to GitHub or GitLab before resetting your workspace to avoid losing your work.
