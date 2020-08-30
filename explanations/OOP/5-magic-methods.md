# Magic Methods
Magic methods, also known as dunder methods, are speical methods that do something unique. For example, `__init__`is a magic method that is called automatically when the class is called.

There are two other commonly used magic methods, called `__str__` and `__repr__`.

`__repr__` goal is to be unambigous. It should be in every object you implement. Used for developers to help with debugging/logging.

`__str__` goal is to be readable. Optional if you want something that can be read by users.

```python
class Tron: 
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __repr__(self):
        return f"Tron({self.name}, {self.age})"
    
    def __str__(self):
        return f"{self.name} - {self.age}"

coen = Tron("Coen", 17)

print(coen)

```
What happens when an instance has both a `__repr__` and a `__str__` and the object is printed. Well, it defaults the readable `__str__` version so the output would be `Coen - 17`

There are a ton of magic methods - read up on documentation.

```python
class Tron: 
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __repr__(self):
        return f"Tron({self.name}, {self.age})"
    
    def __str__(self):
        return f"{self.name} - {self.age}"

    def __len__(self):
        return len(self.name)


coen = Tron("Coen", 17)

print(len(coen))
```
Here, the `__len__` gives the length of name. Otherwise, if we didn't have the `__len__` method, it wouldn't know what to print out because haven't specified anything. In this example I am using the len method to print out the length of the name.
