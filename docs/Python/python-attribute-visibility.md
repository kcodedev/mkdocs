# Python Attribute Visibility

In Python, all attributes of an object—whether properties or methods—are inherently public. This contrasts with languages like Java or C++, where you can explicitly mark attributes as private or protected to restrict access. Python does not enforce any access controls; any external code can freely access and modify an object's attributes without restrictions.

```python
class Example:
    def __init__(self):
        self.public_attr = "I am public"

obj = Example()
print(obj.public_attr)  # Accessible from outside
obj.public_attr = "Modified"  # Can be modified
print(obj.public_attr)
```

However, Python relies on naming conventions to indicate intended visibility:

- Attributes prefixed with a single underscore (`_`) are considered private by convention. They signal to other developers that these attributes are internal to the object and should not be accessed directly from outside. Despite this convention, Python does not prevent external access—it's purely a guideline.

```python
class Example:
    def __init__(self):
        self._private_attr = "I am private by convention"

obj = Example()
print(obj._private_attr)  # Still accessible, but not recommended
```

- Attributes with double underscores (`__`) undergo name mangling, which makes them harder to access accidentally. This provides a stronger hint of privacy, though it's still not a strict enforcement mechanism.

```python
class Example:
    def __init__(self):
        self.__mangled_attr = "I am mangled"

obj = Example()
# print(obj.__mangled_attr)  # AttributeError: 'Example' object has no attribute '__mangled_attr'
print(obj._Example__mangled_attr)  # Accessible via mangled name
```

Before exploring properties in detail, it's essential to grasp these underscore conventions and how attribute scoping works in Python, as they form the foundation for managing object interfaces effectively.

## Pythonic Approach to Attribute Visibility

In Python, the most pythonic approach is to keep attributes public by default and rely on conventions rather than enforcement. Use single underscores for attributes that are internal to the class but may be accessed if necessary. Double underscores should be used judiciously, primarily to prevent accidental overriding in subclasses, not for strict privacy.

This philosophy aligns with Python's "we're all consenting adults" principle, emphasizing trust and simplicity over rigid access controls.