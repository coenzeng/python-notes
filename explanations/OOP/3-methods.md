# Class Methods

To create a class method, first use a class decorator, then write a regular method, except the first parameter, is a class, not an instance. So the first variable is `cls` and not `self.` We can't use `class` because that is a keyword in python.
```python
class Tron:
  
    program = "mechatronics"
    
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod 
    def what_program(cls, program):
        cls.program = program

coen = Tron("Coen", 17)
```python
Tron.what_program("software")
print(coen.program)
```
we can also use class methods as an alterative constructor.

class Tron:
  
    program = "mechatronics"
    
    def __init__(self, name, age):
        self.name = name
        self.age = age

    @classmethod 
    def what_program(cls, program):
        cls.program = program

    @classmethod
    def from_string(cls, emp_str):
        first, age= emp_str.split("-")
        return cls(first, age)

coen = "coen-19"

new_student = Tron.from_string(coen)
print(new_student.name)
print(new_student.age)
```
In this example, coen is a string that has it's name seperated with a hypen. So I used the `from_string` class method to split the name and age. This way we can access them seperately.

#Static Methods

Whereas instance methods pass in an instance and class methods pass in a class as the first variable, static classes don't pass in anything first automatically. They are used when you don't need access to any instances or the class. That is, it's a function that is independant of other variables, but still placed inside the class because it's related.
```python
import datetime

class Tron:
    @staticmethod
    def is_workday(day):
        if day.weekday() == 5 or day.weekday == 6:
            return False
        return True

date = datetime.date(2020, 8, 29)
print(Tron.is_workday(date))
```
This example checks if the date is a weekday or not. If is a weekday, it will return true, and if not, false. `@staticmethod` is the decorator.
