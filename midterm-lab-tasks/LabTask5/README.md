# 🧊 Lab Task 5 — Creating Classes and Instantiating Objects in Python

### 📘 Overview
This lab focuses on the creation and usage of **Python classes and objects** to represent users in a social media system.  
The task required defining a class with attributes and methods, as well as testing object instantiation and method functionality through a separate testing class.

---

### 🧩 Problems
**Problem 1:** Create a program that defines a **User** class with attributes such as `first_name`, `last_name`, `followers_count`, and `friends_name [LIST]`.  
It should include methods to introduce the user and view their full profile.  
A **TestUser** class should also be implemented to handle user input, create objects, and display all users in the program.

Refer to [`LabTask5_Instructions.pdf`](./LabTask5_Instructions.pdf) for the complete set of instructions.

---

### 💻 Output Preview
You can view my program results here:  
📄 [Output PDF](./LabTask5_Output.pdf)

---

### 🐍 Optional — Source Code Example

#### 📚 Problem 1: Users in Social Media
```python
class User:
    def __init__(self, first_name, last_name, followers_count, friends_name):
        """Constructor to initialize user attributes"""
        self.first_name = first_name
        self.last_name = last_name
        self.followers_count = followers_count
        self.friends_name = friends_name

    def introduce_self(self):
        """Outputs user's introduction"""
        print(f"Hi I am {self.first_name} {self.last_name}")

    def view_full_profile(self):
        """Displays user's complete profile"""
        print(f"Profile Name is: {self.first_name} {self.last_name} with {self.followers_count} followers")
        print(f"Your friends are: {' '.join(self.friends_name)}")


class TestUser:
    def __init__(self):
        """Constructor to initialize list of users"""
        self.users = []

    def create_users(self):
        """Method to create user objects based on user input"""
        while True:
            choice = input("Insert a Record?[y|n]:").lower()
            if choice == 'y':
                # Get user input
                first_name = input("First Name: ")
                last_name = input("Last Name: ")
                followers_count = int(input("Followers:"))
                # Get friends list
                print("Friends:")
                friends_name = []
                while True:
                    friend = input()
                    if friend == "":
                        break
                    friends_name.append(friend)
                # Create user object and add to list
                user = User(first_name, last_name, followers_count, friends_name)
                self.users.append(user)
            elif choice == 'n':
                break
            else:
                print("Invalid choice. Please enter 'y' or 'n'.")

    def display_all_users(self):
        """Displays all user profiles"""
        if self.users:
            print("Here are the Records....")
            for user in self.users:
                user.introduce_self()
                user.view_full_profile()
                print("\n")
            print(f"There are currently {len(self.users)} Members in the Social Media page")
        else:
            print("No users to display.")


# Main program execution
if __name__ == "__main__":
    test = TestUser()
    test.create_users()
    test.display_all_users()
