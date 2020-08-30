# Inheritance
Inheritance is the priciple that allows us to create a new class that shares the same attributes and methods of the original class. This new "sub class" can have additional functionality and won't interfere with the original class.

How to inherit from a class:
```python
class stream-4(Tron):
```
Here, stream-4 is a sub-class which is inheriting all the attributes and methods of the Tron class.
### Method Resolution Order
Python uses method resolution order to define the order in which classes are searched to execute a method. In the example below, the methods from stream4 are invoked before the Tron class.

class Tron: 
    def program(self): 
        print(" In mechatronics.")
        
class Stream4(Tron): 
    def program(self): 
        print(" In stream-4 mechatronics.") 
  
coen = Stream4() 
coen.program() 
```
The output will be `In stream-4 mechatronics.`

For subclasses to inherit methods from the super class, we can use the `__super__` reserved method.
```python
class Tron: 
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
class Stream4(Tron): 
    def __init__(self, name, age, coop):
        super().__init__(name, age)
        self.coop = coop
  
coen = Stream4("Coen", "17", "Tiktok") 
print(coen.name)
print(coen.coop)
```
In the Stream4 class, we don't have to redefine attributes name and age, we can just take them from the super class.

In the next example, let's create a new class `Professor` and pass methods where we can add, remove, and print the students that are being taught by them.

```python
class Tron: 
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
class Stream4(Tron): 

    def __init__(self, name, age, coop):
        super().__init__(name, age)
        self.coop = coop

class Professor(Tron):
    def __init__(self, name, age, students=None): 
        super().__init__(name, age)
        if students is None: #Ideally don't pass in a parameter that is mutable, that's why we set students=None first instead of letting it equal an empty list.
            self.students = []
        else:
            self.students = students

    def add_student(self, stu): # student
        if stu not in self.students:
            self.students.append(stu)

    def remove_student(self, stu): # student
        if stu in self.students:
            self.students.remove(stu)
    
    def print_student(self):
        for stu in self.students:
            print(stu.name)

coen = Stream4("Coen", 17, "TikTok")
dave = Stream4("Dave", 18, "Goggles")

prof_1 = Professor("Sue", 45, [coen])
prof_1.add_student(dave)
prof_1.remove_student(coen)
prof_1.print_student()
```
The `isinstance()` and `issubclass()` functions can check if an an object is an instance of a class, and if a class is a subclass of a class, respectively.
```python
print(isinstance(prof_1, Professor)) #True
print(isinstance(prof_1, Tron)) #True
print(isinstance(prof_1, Stream4)) #False

print(issubclass(Professor, Tron)) #True
print(issubclass(Professor, Stream4)) #False
```
