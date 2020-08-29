# Classes
Classes are a user-defined data-structure. A class defines functions called **methods**, which are the actions that an object created from the class can do with the data. A method is a function associated with a class.

In other terms. a class is a form or questionnaire, and instances are sets of answers to that form.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

good_boy = Dog("Choco", 19)
```
The property that all Dog objects must have are defined in the function .__init__(). The __init__ method is called automatically when an instance is created. 
When we create methods, they recieve the instance as the first argument automatically. The keyword `self` represents `good_boy`. `self.name` represents `good_boy.name` and so on. The purpose of self is that it's a parameter that stores the instance, so that it can be distingushed from other instances.

Lets say we wanted to print out a string with good_boy's information. This can be achieved with f-literal strings, like so:

```python
print(f"{good_boy.name} is {good_boy.age} old.")
```
Instead of doing this, we can create a method in the class that can be called every time we want to do this action.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def print_sentence(self):
        return print(f"{self.name} is {self.age} old.")

good_boy = Dog("Choco", 19)
good_boy.print_sentence()
```
Remember, self is referring the instance, aka good_boy. If we didn't use self, it wouldn't know whose information to deal with.
We can run these methods using the class name itself. In this case, you would have the pass in the instance as a parameter.
```python
Dog.print_sentence(good_boy)
```
