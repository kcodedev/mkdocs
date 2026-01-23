# Object-Oriented Programming

Object-Oriented Programming (OOP) is a programming paradigm that organizes software design around data, or objects, rather than functions and logic. It models real-world entities as software objects that have both data and behavior.

## Core Concepts

### Classes and Objects

A **class** is a blueprint or template for creating objects. An **object** is an instance of a class.

```python
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.speed = 0

# Creating objects (instances)
car1 = Car("Toyota", "Corolla", 2020)
car2 = Car("Honda", "Civic", 2019)
```

### Attributes and Methods

- **Attributes**: Variables that belong to an object (instance variables) or class (class variables).
- **Methods**: Functions that belong to a class and operate on its data.

```python
class Car:
    # Class attribute
    wheels = 4

    def __init__(self, make, model, year):
        # Instance attributes
        self.make = make
        self.model = model
        self.year = year
        self.speed = 0

    def accelerate(self, increment):
        """Increase the car's speed."""
        self.speed += increment

    def brake(self, decrement):
        """Decrease the car's speed."""
        self.speed = max(0, self.speed - decrement)

    def get_info(self):
        """Return car information."""
        return f"{self.year} {self.make} {self.model}"
```

## Four Pillars of OOP

### 1. Encapsulation

Encapsulation is the bundling of data and methods that operate on that data within a single unit (class). It restricts direct access to some of an object's components.

```python
class BankAccount:
    def __init__(self, balance=0):
        self.__balance = balance  # Private attribute

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def withdraw(self, amount):
        if 0 < amount <= self.__balance:
            self.__balance -= amount
            return True
        return False

    def get_balance(self):
        return self.__balance

# Usage
account = BankAccount(1000)
account.deposit(500)
account.withdraw(200)
print(account.get_balance())  # 1300
# print(account.__balance)  # AttributeError: 'BankAccount' object has no attribute '__balance'
```

### 2. Inheritance

Inheritance allows a class (subclass/derived class) to inherit attributes and methods from another class (superclass/base class).

```python
class Vehicle:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def start_engine(self):
        return "Engine started"

class Car(Vehicle):  # Car inherits from Vehicle
    def __init__(self, make, model, year, num_doors):
        super().__init__(make, model, year)  # Call parent constructor
        self.num_doors = num_doors

    def honk(self):
        return "Honk! Honk!"

class Motorcycle(Vehicle):  # Motorcycle also inherits from Vehicle
    def __init__(self, make, model, year, has_sidecar):
        super().__init__(make, model, year)
        self.has_sidecar = has_sidecar

    def wheelie(self):
        return "Doing a wheelie!"

# Usage
car = Car("Toyota", "Corolla", 2020, 4)
print(car.start_engine())  # Inherited method
print(car.honk())         # Car-specific method

motorcycle = Motorcycle("Harley-Davidson", "Sportster", 2019, False)
print(motorcycle.start_engine())  # Inherited method
print(motorcycle.wheelie())      # Motorcycle-specific method
```

### 3. Polymorphism

Polymorphism allows objects of different classes to be treated as objects of a common superclass. It enables the same method name to behave differently based on the object.

```python
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

class Bird(Animal):
    def speak(self):
        return "Tweet!"

def animal_sound(animal):
    return animal.speak()

# Usage
animals = [Dog(), Cat(), Bird()]

for animal in animals:
    print(animal_sound(animal))
```

### 4. Abstraction

Abstraction focuses on the essential features of an object while hiding unnecessary details. It allows us to represent complex real-world entities in a simplified way.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14159 * self.radius ** 2

    def perimeter(self):
        return 2 * 3.14159 * self.radius

# Usage
shapes = [Rectangle(5, 3), Circle(4)]

for shape in shapes:
    print(f"Area: {shape.area()}, Perimeter: {shape.perimeter()}")
```

## Advanced OOP Concepts

### Class Methods and Static Methods

```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

    @classmethod
    def create_from_string(cls, expression):
        # Class method that can create instances
        a, b = map(int, expression.split('+'))
        return cls(a, b)

# Usage
result = MathUtils.add(5, 3)  # Static method
# utils = MathUtils.create_from_string("5+3")  # Class method
```

### Multiple Inheritance

A class can inherit from multiple parent classes.

```python
class Flyable:
    def fly(self):
        return "Flying"

class Swimmable:
    def swim(self):
        return "Swimming"

class Duck(Flyable, Swimmable):
    def quack(self):
        return "Quack!"

duck = Duck()
print(duck.fly())   # From Flyable
print(duck.swim())  # From Swimmable
print(duck.quack()) # From Duck
```

## Advantages of OOP

1. **Modularity**: Code is organized into self-contained objects.
2. **Reusability**: Classes can be reused in different programs.
3. **Maintainability**: Changes to one class don't affect others.
4. **Scalability**: Easy to add new features and extend existing code.
5. **Real-world Modeling**: Mirrors real-world relationships and hierarchies.

## Disadvantages of OOP

1. **Complexity**: Can be overkill for simple programs.
2. **Performance Overhead**: Object creation and method calls have some overhead.
3. **Learning Curve**: More concepts to learn compared to procedural programming.
4. **Memory Usage**: Objects consume more memory than simple data structures.

## Common OOP Languages

- Java
- C++
- Python
- C#
- Ruby
- PHP

## Design Patterns

OOP often uses design patterns to solve common problems:

- **Singleton**: Ensures only one instance of a class exists.
- **Factory**: Creates objects without specifying exact classes.
- **Observer**: Defines a one-to-many relationship between objects.
- **Decorator**: Adds behavior to objects dynamically.

## Conclusion

Object-Oriented Programming provides a powerful way to structure complex software systems. By modeling real-world entities as objects with data and behavior, OOP promotes code reusability, maintainability, and scalability. Understanding the four pillars—encapsulation, inheritance, polymorphism, and abstraction—is essential for effective OOP design.