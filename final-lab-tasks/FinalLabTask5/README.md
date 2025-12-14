# 🧊 Finals Lab Task 5 — CLI using MySQL and Python
### 🗄️ Movie Database CRUD Application

---

## 📘 Overview

This lab focuses on **database integration** in Python, demonstrating how to connect and interact with **MySQL databases** using the `mysql-connector` library.  
It showcases essential **CRUD operations** (Create, Read, Update, Delete) through a **command-line interface (CLI)**, along with advanced features like searching and counting records.

---

## 🧩 Problem Description

The task requires creating a **Movie Database CLI Application** that:
- Connects to a **MySQL database** (`moviesDB`) using mysql-connector
- Implements a **complete CRUD system** for movie records
- Provides a **menu-driven CLI** with 7 options
- Supports **searching** movies by title or actor using SQL LIKE statements
- Displays **total record count** using SQL COUNT function
- Uses **parameterized queries** to prevent SQL injection
- Handles database operations with proper commit and cursor management

**Database Structure:**
- **Table**: `movies`
- **Fields**: movie_id (PK), title, main_actor, director, genre, gross_sales, ratings
- **Ratings**: G, PG, R13, R16, X

**Prerequisites:**
- mysql-connector-python installed
- XAMPP running (Apache + MySQL)
- Database user with admin privileges

📄 [Refer to `FinalLabTask5_Instructions.pdf`](./FinalLabTask5_Instructions.pdf)

---

## 💻 Output Preview

📄 [Output PDF](./FinalLabTask5_Output.pdf)

---

## 🐍 Optional — Source Code Example

### 🎥 `TestDb_Demo.py`

```python
import mysql.connector

# Database connection
conn = mysql.connector.connect(
    host="localhost",
    user="test",
    password="asdf",
    database="moviesdb"
)
cursor = conn.cursor()

def add_movie():
    """Add a new movie record to the database"""
    title = input("Enter movie title: ")
    actor = input("Enter main actor: ")
    director = input("Enter director: ")
    genre = input("Enter genre: ")
    gross = float(input("Enter gross sales: "))
    rating = input("Enter rating (G, PG, R13, R16, X): ")
    
    cursor.execute("""INSERT INTO movies 
                      (title, main_actor, director, genre, gross_sales, ratings) 
                      VALUES (%s,%s,%s,%s,%s,%s)""",
                   (title, actor, director, genre, gross, rating))
    conn.commit()
    print("Movie added successfully!\n")

def view_movies():
    """Display all movies in the database"""
    cursor.execute("SELECT * FROM movies")
    rows = cursor.fetchall()
    
    if rows:
        print("\n--- Movie List ---")
        for row in rows:
            print(row)
    else:
        print("No movies found.\n")

def update_movie():
    """Update an existing movie record"""
    movie_id = input("Enter movie ID to update: ")
    new_title = input("Enter new title: ")
    new_actor = input("Enter new main actor: ")
    new_director = input("Enter new director: ")
    new_genre = input("Enter new genre: ")
    new_gross = float(input("Enter new gross sales: "))
    new_rating = input("Enter new rating: ")
    
    cursor.execute("""UPDATE movies 
                      SET title=%s, main_actor=%s, director=%s, genre=%s, 
                          gross_sales=%s, ratings=%s 
                      WHERE movie_id=%s""",
                   (new_title, new_actor, new_director, new_genre, 
                    new_gross, new_rating, movie_id))
    conn.commit()
    print("Movie updated successfully!\n")

def delete_movie():
    """Delete a movie record from the database"""
    movie_id = input("Enter movie ID to delete: ")
    cursor.execute("DELETE FROM movies WHERE movie_id=%s", (movie_id,))
    conn.commit()
    print("Movie deleted successfully!\n")

def search_movie():
    """Search for movies by title or actor"""
    keyword = input("Enter movie title or actor to search: ")
    cursor.execute("""SELECT * FROM movies 
                      WHERE title LIKE %s OR main_actor LIKE %s""",
                   (f"%{keyword}%", f"%{keyword}%"))
    row = cursor.fetchone()
    
    if row:
        print("Search Result:", row)
    else:
        print("No matching movie found.\n")

def total_records():
    """Display total number of movies in database"""
    cursor.execute("SELECT COUNT(*) FROM movies")
    count = cursor.fetchone()[0]
    print(f"Total Movies in Database: {count}\n")

def menu():
    """Main menu loop"""
    while True:
        print("""
----- MOVIE DATABASE CLI -----
1. Add Movie
2. View Movies
3. Update Movie
4. Delete Movie
5. Search Movie
6. Display Total Records
7. Exit
        """)
        
        choice = input("Select an option (1-7): ")
        
        if choice == "1":
            add_movie()
        elif choice == "2":
            view_movies()
        elif choice == "3":
            update_movie()
        elif choice == "4":
            delete_movie()
        elif choice == "5":
            search_movie()
        elif choice == "6":
            total_records()
        elif choice == "7":
            print("Exiting program...")
            break
        else:
            print("Invalid choice. Try again.\n")

if __name__ == "__main__":
    menu()
```

---

## 🗃️ Database Setup

### Create Database and Table

```sql
CREATE DATABASE moviesDB;

USE moviesDB;

CREATE TABLE movies (
    movie_id INT(10) PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(50) NOT NULL,
    main_actor VARCHAR(50) NOT NULL,
    director VARCHAR(50) NOT NULL,
    genre VARCHAR(25) NOT NULL,
    gross_sales FLOAT,
    ratings VARCHAR(5)
);
```

### Create User and Grant Privileges

```sql
CREATE USER 'test_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON moviesDB.* TO 'test_user'@'localhost';
FLUSH PRIVILEGES;
```

### Sample Data Insertion

```sql
INSERT INTO movies (title, main_actor, director, genre, gross_sales, ratings)
VALUES 
    ('The Matrix', 'Keanu Reeves', 'Wachowskis', 'Sci-Fi', 463.5, 'R13'),
    ('Inception', 'Leonardo DiCaprio', 'Christopher Nolan', 'Sci-Fi', 836.8, 'PG'),
    ('Avengers', 'Robert Downey Jr.', 'Joss Whedon', 'Action', 1518.8, 'PG'),
    ('Parasite', 'Song Kang-ho', 'Bong Joon-ho', 'Thriller', 258.8, 'R16'),
    ('Toy Story', 'Tom Hanks', 'John Lasseter', 'Animation', 373.6, 'G');
```

---

## 🎯 Key Concepts Demonstrated

- **Database Connection**: Using mysql-connector to connect to MySQL
- **CRUD Operations**: Complete Create, Read, Update, Delete functionality
- **SQL Queries**: SELECT, INSERT, UPDATE, DELETE, COUNT
- **Parameterized Queries**: Using `%s` placeholders to prevent SQL injection
- **Search Functionality**: Using SQL LIKE operator with wildcards
- **Aggregate Functions**: COUNT(*) for total records
- **Cursor Management**: Using cursor.execute() and cursor.fetchall()/fetchone()
- **Transaction Control**: Using conn.commit() for data persistence
- **CLI Design**: Menu-driven user interface with input validation

---

---

## 💡 Features

✅ **Add Records** - Insert new movie entries with validation  
✅ **View All** - Display complete movie database  
✅ **Update Records** - Modify existing movie information  
✅ **Delete Records** - Remove movies by ID  
✅ **Search Functionality** - Find movies by title or actor (LIKE query)  
✅ **Count Records** - Display total number of movies (COUNT function)  
✅ **SQL Injection Protection** - Parameterized queries for security  
✅ **User-Friendly CLI** - Clean menu-driven interface

---
