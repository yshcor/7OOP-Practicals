# 🧊 Lab Task 2 — Using Functions in Python

### 📘 Overview
This lab demonstrates how to use **functions** in Python to make code modular, organized, and reusable.  
It covers the creation of user-defined functions for performing specific tasks, as well as the use of loops and conditionals to manage program flow.

---

### 🧩 Problems
**Problem 1:** Create a multiplication table using functions and nested loops.  
**Problem 2:** Develop a simple ATM program that uses functions to perform operations such as showing balance, deposit, and withdrawal.

Refer to [`LabTask2_Instructions.pdf`](./LabTask2_Instructions.pdf) for the complete set of instructions.

---

### 💻 Output Preview
You can view my program results here:  
📄 [Output PDF](./LabTask2_Output.pdf)

---

### 🐍 Optional — Source Code Example

#### 🧱 Problem 1: Multiplication Table
```python
rows = int(input("How many rows: "))
cols = int(input("How many cols: "))

print("Multiplication Table\n")

for r in range(1, rows + 1):
    for c in range(1, cols + 1):
        print(r * c, end="\t")
    print()
