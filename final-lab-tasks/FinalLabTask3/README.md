# 🧊 Finals Lab Task 3 — Simple Polymorphism in Python
### 🎵 Chirp and Tweet

---

## 📘 Overview

This lab focuses on **polymorphism**, a core principle of **object-oriented programming (OOP)** in Python.  
It demonstrates how different classes can implement the same method in their own way, allowing objects of different types to be treated uniformly through a common interface using **abstract base classes**.

---

## 🧩 Problem Description

The task requires creating a **Bird Sound System** that:
- Implements an **abstract base class** (`Bird`) with an abstract method
- Creates **concrete subclasses** (`Sparrow`, `Parrot`) that implement the abstract method differently
- Uses **polymorphism** to handle different bird types uniformly
- Implements a `BirdCage` class that processes a list of birds polymorphically
- Follows **camelCase** naming conventions for file names (e.g., `birdCage.py`)

**Note:** Test cases are provided by a hidden test file to validate your implementation.

📄 Refer to [`FinalLabTask3_Instructions.pdf`](./FinalLabTask3_Instructions.pdf) for the complete task requirements.

---

## 💻 Output Preview

📄 [Output PDF](./FinalLabTask3_Output.pdf)

---

## 🐍 Optional — Source Code Example

### 🦅 `bird.py`
```python
from abc import ABC, abstractmethod

class Bird(ABC):
    @abstractmethod
    def make_sound(self) -> str:
        pass
```

### 🐦 `sparrow.py`
```python
from bird import Bird

class Sparrow(Bird):
    def make_sound(self) -> str:
        return "Chirp Chirp"
```

### 🦜 `parrot.py`
```python
from bird import Bird

class Parrot(Bird):
    def make_sound(self) -> str:
        return "Tweet Tweet"
```

### 🏠 `birdCage.py`
```python
from typing import List
from bird import Bird

class BirdCage:
    def make_bird_sounds(self, birds: List[Bird]) -> List[str]:
        return [bird.make_sound() for bird in birds]
```

---

## 🎯 Key Concepts Demonstrated

- **Abstract Base Class**: `Bird` defines the contract using `ABC` and `@abstractmethod`
- **Polymorphism**: Different bird types implement `make_sound()` differently
- **Interface Uniformity**: `BirdCage` treats all birds the same way
- **Type Hinting**: Using `List[Bird]` for proper type annotation
- **Method Overriding**: Subclasses provide their own implementation of abstract methods

---

---

## 🧪 Example Usage

```python
from sparrow import Sparrow
from parrot import Parrot
from birdCage import BirdCage

# Create different bird instances
sparrow = Sparrow()
parrot = Parrot()

# Create a bird cage
cage = BirdCage()

# Polymorphic behavior - same method, different results
birds = [sparrow, parrot, sparrow]
sounds = cage.make_bird_sounds(birds)
print(sounds)  # ['Chirp Chirp', 'Tweet Tweet', 'Chirp Chirp']
```
