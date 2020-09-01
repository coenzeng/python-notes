# What is OOP?
Object Oreinted Programming is a programming model that involves designing software around objects/data instead of functions/methods.

# Why use OOP?
The benefits of Object Oriented Programming include code resuability, scalibablity, and efficiency. It is also easier to collaberate on with multiple developers. 

# The 4 main aspects of OOP
### 1. Encapsulation
Encapsulation is when an object keeps in state **private** within its class. Other objects don't have access to this state. Instead, they call only public functions, called methods. Encapsulation provides better data security and prevents data corruption. 

### 2. Abstraction
Abstraction means that an object will only expose the high-level mechanisms for using it. It hides away unnecessary implementation code. This helps developers make changes easier over time. 

### 3. Inheritance
Inheritance allows for the reuse of code by establishing a parent and child relationship between classes. A hierarchy is formed because the child class can reuse all forms and methods in the parent class, and also implement its own fields and methods.

### 4. Polymorism
Objects can take on different forms depending on the context. This usually happens when a parent class is reused by different child classes. Each child class will implement a different version of the parent method. An example is a parent class of calculating area, but the child classes include a triangle, cicle and square. Each child class inherits the parent class and will call the **same** method, but depending on the parameters they pass in, the method will be adjusted to calculate the area of their specific shape. 
