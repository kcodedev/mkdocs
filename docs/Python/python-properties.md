# Python Properties

In object-oriented programming, objects are designed to represent real-world entities by encapsulating both data and behavior. For many entities, the validity of the data is critical—certain values are necessary for the object to exist meaningfully, while invalid values must be prevented.

This often requires validation logic in setter methods to ensure data integrity. However, Python provides properties as a more elegant way to encapsulate getters and setters, allowing attribute-like access while maintaining control over data assignment and retrieval.

## Basic Property Usage

Properties use the `@property` decorator for getters and `@<property_name>.setter` for setters.

```python
class Person:
    def __init__(self, name: str, age: int):
        self.name = name
        self.age = age

    @property
    def age(self) -> int:
        return self._age

    @age.setter
    def age(self, value: int) -> None:
        if not isinstance(value, int) or value < 0:
            raise ValueError("Age must be a non-negative integer")
        self._age = value

# Usage
person = Person("Alice", 30)
print(person.age)  # 30
person.age = 25    # Valid
# person.age = -5  # Raises ValueError
```

!!! note "Use Type Hints"
    Using type hints in properties enhances code clarity, enables better IDE support, and allows static type checkers like mypy to catch type-related errors early.

## Comparison with Direct Attribute Access

Without properties, validation requires explicit method calls, which is less intuitive:

```python
class PersonWithoutProperties:
    def __init__(self, name, age):
        self.name = name
        self.set_age(age)

    def set_age(self, value):
        if not isinstance(value, int) or value < 0:
            raise ValueError("Age must be a non-negative integer")
        self._age = value

    def get_age(self):
        return self._age

# Usage
person = PersonWithoutProperties("Bob", 40)
print(person.get_age())  # 40
person.set_age(35)       # Valid
# person.set_age(-10)    # Raises ValueError
```

Properties provide a cleaner interface, making the class behave like it has direct attribute access while enforcing rules internally.