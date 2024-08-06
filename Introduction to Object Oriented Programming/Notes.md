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
