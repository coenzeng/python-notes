# Class variables
Class variables are declared before the init method and are variables that apply to the entire class, not just an instance. 

```python
class Tron:
  
    program = "mechatronics"
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def what_program(self):
        return f"{self.name} is in the {self.program}'s program."

coen = Tron("Coen", 17)
print(coen.what_program())
```
Every Tron kid is in the `mechatronics` program, so this class variable applies to every instance of the class.

What if we were to set the program using an Class?

```python
Tron.program = "software"
```
This will override the class variable.

We can also set the program using an instance.
```python
coen.program = "software"
```
Now only the `coen` instance has a program of `software`, but all other instances will still have the normal class variable, `mechatronics`.

This is because it created the `program` attribute within the instance `coen`. If we print out the `coen` namespace using .__dict__, like so:
```python
class Tron:
  
    program = "mechatronics"
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def what_program(self):
        return f"{self.name} is in the {self.program}'s program."


coen = Tron("Coen", 17)
coen.program = "software"
print(coen.__dict__)
```
The outout is:
```python
{'name': 'Coen', 'age': 17, 'program': 'software'}
```
So it will look within its namespace first and return that value, before going and searching the class. Keeping the `self` in `self.program` allows us to change the variable depending on the instance. If it was instead `Tron.program` the output would always be `mechatronics`.
