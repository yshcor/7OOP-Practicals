# 🧊 Lab Task 2 — Using Functions in Python

### 📘 Overview
This lab focuses on the use of **functions** to organize and structure Python programs.  
It includes exercises that require defining, calling, and managing functions for both computational and interactive tasks.

---

### 🧩 Problems Summary
| Problem | Focus | Description |
|:--------:|--------|-------------|
| 1 | Multiplication Table | Generate a multiplication table based on user-defined rows and columns using nested loops. |
| 2 | Simple ATM System | Implement a menu-driven banking program that uses functions for deposit, withdrawal, and balance display. |

📘 [Instructions (PDF)](./LabTask2_Instructions.pdf)

---

### 💻 Code Samples

#### 🧱 Problem 1 — Multiplication Table
```python
rows = int(input("How many rows: "))
cols = int(input("How many cols: "))

print("Multiplication Table\n")

for r in range(1, rows + 1):
    for c in range(1, cols + 1):
        print(r * c, end="\t")
    print()
