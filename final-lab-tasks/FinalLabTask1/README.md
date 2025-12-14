# 🧊 Finals Lab Task 1 — Encapsulation in Python
### 🚗 A Car That Works

---

## 📘 Overview
This lab focuses on **encapsulation**, one of the core principles of **object-oriented programming (OOP)** in Python.  
It demonstrates how to protect object data using private attributes and how to interact with them safely through **getter and setter methods**.

---

## 🧩 Problem Description
The task requires creating a `Car` class that:
- Uses **private attributes** for car details
- Provides **getter and setter methods**
- Formats object output using the `__str__()` method
- Demonstrates object instantiation and display using a test file

A separate test program is used to create multiple car objects and display their details.

📄 Refer to [`FinalLabTask1_Instructions.pdf`](./FinalLabTask1_Instructions.pdf) for the complete task requirements.

---

## 💻 Output Preview
You can view the program execution and sample output here:  
📄 [Output PDF](./FinalLabTask1_Output.pdf)

---

## 🐍 Optional — Source Code Example

### 🚘 `car.py`
```python
class Car:
    def __init__(self, color: str, price: float, size: str):
        self._color = color
        self._price = float(price)
        self._size = size.upper()

    def get_color(self) -> str:
        return self._color

    def get_price(self) -> float:
        return self._price

    def get_size(self) -> str:
        return self._size

    def set_color(self, color: str) -> None:
        self._color = color

    def set_price(self, price: float) -> None:
        self._price = float(price)

    def set_size(self, size: str) -> None:
        self._size = size.upper()

    def __str__(self) -> str:
        size_map = {'S': 'small', 'M': 'medium', 'L': 'large'}
        size_desc = size_map.get(self._size, 'unknown')
        return f"Car ({self._color}) - P{self._price:.2f} - {size_desc}"
