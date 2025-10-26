# 🧊 Lab Task 1 — Escape Sequences, Placeholders & Conditional Statements

### 📘 Overview
This lab introduces:
- Proper use of **escape sequences** (`\n`, `\t`, etc.)
- Applying **string placeholders** (`%s`, `%d`, `%f`)
- Handling **user input** and **if–elif–else** statements

---

### 🧩 Problems
**Problem 1:** Use appropriate escape sequences  
**Problem 2:** Use placeholders for email details  
**Problem 3:** Implement book reservation with input  
**Problem 4:** Create a day identifier  

Refer to [`lab-task-1-instructions.pdf`](./lab-task-1-instructions.pdf) for full task details.

---

### 💻 Output Preview
You can view my program results here:  
📄 [Output PDF](./lab-task-1-output.pdf)

---

### 🐍 Optional — Source Code Example
```python
# Problem 4: Day Identifier
day_num = int(input("Enter day: "))

if day_num == 1:
    print("Monday")
elif day_num == 2:
    print("Tuesday")
elif day_num == 3:
    print("Wednesday")
elif day_num == 4:
    print("Thursday")
elif day_num == 5:
    print("Friday")
elif day_num == 6:
    print("Saturday")
elif day_num == 7:
    print("Sunday")
else:
    print("Invalid input")
