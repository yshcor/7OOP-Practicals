# 🧊 Lab Task 3 — Python List Collections

### 📘 Overview
This lab focuses on the use of **Python list collections** to manage, organize, and manipulate data.  
The task required creating a program that allows adding, searching, deleting, displaying, and sorting items within a list using menu-driven interaction.

---

### 🧩 Problems
**Problem 1:** Create a program that performs list operations such as **add**, **search**, **remove**, **display**, and **sort**.  
The program should allow the user to manage a list of items interactively through a console menu.

Refer to [`LabTask3_Instructions.pdf`](./LabTask3_Instructions.pdf) for the complete set of instructions.

---

### 💻 Output Preview
You can view my program results here:  
📄 [Output PDF](./LabTask3_Output.pdf)

---

### 🐍 Optional — Source Code Example

#### 📚 Problem 1: Book Collection Manager
```python
books = []

def add_books():
    """Function to add books to the list"""
    print("\n--- ADD BOOKS ---")
    while True:
        book = input("Enter book title (type 'x' to stop): ")
        if book.lower() == "x":
            break
        books.append(book)
        print(f"Added: {book}")
    print(f"Total books: {len(books)}")

def search_book():
    """Function to search for a book"""
    if len(books) == 0:
        print("No books in collection!")
        return
    
    search = input("Enter book to search: ")
    count = 0

    for book in books:
        if search.lower() in book.lower():
            count = count + 1

    if count > 0:
        print(f"FOUND! '{search}' appears {count} time(s)")
    else:
        print(f"NOT FOUND! '{search}' is not in collection")

def remove_book():
    """Function to remove a book"""
    if len(books) == 0:
        print("No books in collection!")
        return
    
    remove = input("Enter book to remove: ")
    found = False

    for book in books:
        if book.lower() == remove.lower():
            books.remove(book)
            print("Item found and deleted")
            found = True
            break

    if not found:
        print("Item not found - deletion unsuccessful")

def view_books():
    """Function to display all books sorted"""
    if len(books) == 0:
        print("No books in collection!")
        return
    
    sort_choice = input("Sort A-Z (1) or Z-A (2)? Enter 1 or 2: ")

    if sort_choice == "1":
        sorted_books = sorted(books)
        print("\n--- Books (A-Z) ---")
    elif sort_choice == "2":
        sorted_books = sorted(books, reverse=True)
        print("\n--- Books (Z-A) ---")
    else:
        sorted_books = books
        print("\n--- Books ---")

    for i in range(len(sorted_books)):
        print(f"{i+1}. {sorted_books[i]}")

    print(f"Total: {len(books)} books")

def display_menu():
    """Function to show the menu"""
    print("\n--- BOOK COLLECTION MANAGER ---")
    print("1 – Add Books")
    print("2 – Search for a Book")
    print("3 – Remove a Book")
    print("4 – View all Books (Sorted A-Z | Z-A)")
    print("0 – Exit Program")

while True:
    display_menu()
    choice = input("Pick one [0 to quit]: ")

    if choice == "1":
        add_books()
    elif choice == "2":
        search_book()
    elif choice == "3":
        remove_book()
    elif choice == "4":
        view_books()
    elif choice == "0":
        print("Thank you! Goodbye!")
        break
    else:
        print("Invalid choice! Please pick 0-4")

print("Program ended.")
