# 🧊 Finals Lab Task 2 — Inheritance in Python
### 🎤 School Performance Hierarchy

---

## 📘 Overview

This lab focuses on **inheritance**, a fundamental principle of **object-oriented programming (OOP)** in Python.  
It demonstrates how to create a class hierarchy where subclasses inherit attributes and methods from a parent class, promoting code reuse and logical organization.

---

## 🧩 Problem Description

The task requires creating a **School Performance** system that:
- Implements a **base class** (`Performer`) with common attributes
- Creates **two subclasses** (`Singer` and `Dancer`) that inherit from the base class
- Adds specialized attributes and methods to each subclass
- Demonstrates inheritance relationships using a test file with multiple test cases
- Verifies subclass relationships using `issubclass()`

📄 [Refer to `FinalLabTask2_Instructions.pdf`](./FinalLabTask2_Instructions.pdf)

---

## 💻 Output Preview

📄 [Output PDF](./FinalLabTask2_Output.pdf)

---

## 🐍 Optional — Source Code Example

### 🎪 `performer.py`
```python
class Performer:
    def __init__(self, name: str, age: int):
        self.name = name
        self.age = age
    
    def get_name(self) -> str:
        return self.name
    
    def get_age(self) -> int:
        return self.age
```

### 🎤 `singer.py`
```python
from performer import Performer

class Singer(Performer):
    def __init__(self, name: str, age: int, vocal_range: str):
        super().__init__(name, age)
        self.vocal_range = vocal_range
    
    def get_vocal_range(self) -> str:
        return self.vocal_range
    
    def sing(self) -> None:
        print(f"{self.name} is singing with a {self.vocal_range} range.")
```

### 💃 `dancer.py`
```python
from performer import Performer

class Dancer(Performer):
    def __init__(self, name: str, age: int, dance_style: str):
        super().__init__(name, age)
        self.dance_style = dance_style
    
    def get_dance_style(self) -> str:
        return self.dance_style
    
    def dance(self) -> None:
        print(f"{self.name} is performing {self.dance_style} dance.")
```

### 🧪 `test_class.py`
```python
from performer import Performer
from singer import Singer
from dancer import Dancer

# Test case 1: Performer instantiation
p = Performer("John", 25)
print([p.get_name(), p.get_age()])  # ['John', 25]

# Test case 2: Dancer with inherited attributes
d = Dancer("Emily", 28, "Ballet")
print([d.get_name(), d.get_age(), d.get_dance_style()])  # ['Emily', 28, 'Ballet']

# Test case 3: Dancer-specific method
d.dance()  # Emily is performing Ballet dance.

# Test case 4: Verify inheritance relationship
print(issubclass(Dancer, Performer))  # True

# Test case 5: Singer with inherited attributes
s = Singer("Linda", 35, "Soprano")
print([s.get_name(), s.get_age(), s.get_vocal_range()])  # ['Linda', 35, 'Soprano']

# Test case 6: Singer-specific method
s.sing()  # Linda is singing with a Soprano range.
```

---

## 🎯 Key Concepts Demonstrated

- **Base Class**: `Performer` provides common attributes (`name`, `age`)
- **Inheritance**: `Singer` and `Dancer` extend `Performer` using `super()`
- **Method Extension**: Each subclass adds specialized methods (`sing()`, `dance()`)
- **Code Reuse**: Getter methods are inherited, not redefined
- **Type Checking**: Using `issubclass()` to verify class relationships

---

