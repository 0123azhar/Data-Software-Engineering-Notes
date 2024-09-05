2024-08-24 10:36
# Class

Advantage of Class over function is that objects of a class store data internally to keep track of their state throughout their lifetime. 

Ex: shoppingCart class can have methods like add items, delete items, update quantities, calculate total etc. and store the state 
functions simply take input and provide output.

Class example:
```python
class Dog: 
    def __init__(self, name, age):
        self.name = name
        self.age = age 
    def bark(self):
        sound = 'WOF!'
        return sound

roger = Dog('Roger', 8) 
print(roger.bark())
```

Primary constructor:
```python
Class maths(): 
  def __init__ (self, x, y, …): 
    Self.x =x 
    ... 
```
## **Variables in class:**
#### Instance variable
has self. prefix when defined. 
Ex: `self.colour = blue` 
#### Class variable
normal variable without any prefix defined inside a class. 
There is no concept of static variable in python like java or c 
## **Methods in class:**
### Instance method
any method inside a class without the class/static decorators. The first argument is self. they operate on object/instance of a class
```python
Class maths(): 
    def __init__ (self, x, y, …): 
        Self.x =x 
    def add(self, x, y):
        result = x + y
        return result
```

## class method
==@classmethod== decorator place on top of instance method to make it class method. The first argument is not self like instance method, it is cls. 
```python
Class maths(): 
    def __init__ (self, x, y, …): 
        Self.x =x
         
    @classmethod
    def add(cls, x, y):
        result = x + y
        return result
```
This method is bound to the class and not to the object/instance of the class so only it is used when we need to update/ interact with class variables/attributes.
## static method
==@staticmethod== decorator to convert to static method and first argument is neither self nor cls. This method is also ==bound to the class not to the object==/instance of the class.
```
Class maths(): 
    def __init__ (self, x, y, …): 
        Self.x =x
         
    @staticmethod
    def add(x, y):
        result = x + y
        return result
```
Static method can be accessed/==called without creating instance of the class== or instantiating.

