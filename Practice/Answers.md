Consider these answers as guiding lights, but feel free to craft your own solutions as long as they deliver the desired results.
1. **Class Inheritance and Method Overriding:**
Create a base class `Vehicle` with attributes `make`, `model`, and a method `display_info()` that prints the make and model. Then, create two subclasses `Car` and `Motorcycle` that inherit from `Vehicle`. Override the `display_info()` method in each subclass to display additional information specific to cars and motorcycles.

```python
class Vehicle:
    def __init__(self, make, model):
        self.make = make
        self.model = model
        
    def display_info(self):
        print(f"{self.make} {self.model}")
        
class Car(Vehicle):
    def __init__(self, make, model):
        super().__init__(make, model)
        
    def display_info(self):
        print(f"This is a car: {self.make} {self.model}")
        
class Motorcycle(Vehicle):
    def __init__(self, make, model):
        super().__init__(make, model)
        
    def display_info(self):
        print(f"This is a motorcycle: {self.make} {self.model}")

# Creating instances of the classes
car = Car("Toyota", "Corolla")
motorcycle = Motorcycle("Harley-Davidson", "Sportster")

# Calling the display_info method
car.display_info()
motorcycle.display_info()
```

2. **Abstract Base Class and Polymorphism:**
Define an abstract base class `Shape` with an abstract method `area()`. Create subclasses `Circle`, `Rectangle`, and `Triangle` that inherit from `Shape`. Implement the `area()` method in each subclass to calculate and return the area of the respective shapes. Write a function that takes a list of shapes and prints their areas.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        ar = 3.14 * (self.radius ** 2)
        print(ar)

class Rectangle(Shape):
    def __init__(self, length, breadth):
        self.length = length
        self.breadth = breadth

    def area(self):
        ar = self.length * self.breadth
        print(ar)

class Triangle(Shape):
    def __init__(self, base, height):
        self.base = base
        self.height = height

    def area(self):
        ar = self.base * self.height * 0.5
        print(ar)

# Create instances and calculate areas
circle = Circle(5)
triangle = Triangle(10, 20)
rectangle = Rectangle(10, 20)

circle.area()
triangle.area()
rectangle.area()
```

3. **Exception Handling:**
Write a program that prompts the user for an integer input. Use a `try` and `except` block to handle the case where the user enters a non-integer value. Print an error message if the input cannot be converted to an integer.

```python
try:
    user_input = input("Enter an integer: ")
    integer_value = int(user_input)
    print(f"You entered an integer: {integer_value}")
except ValueError:
    print("Error: Invalid input. Please enter a valid integer.") 
```

4. **File Handling:**
Write a program that reads a text file and counts the number of occurrences of each word in the file. Create a dictionary where the keys are the words and the values are the counts. Print the dictionary.

```python
def count_word_occurrences(filename):
    word_counts = {}
    with open(filename, 'r') as file:
        for line in file:
            words = line.strip().split()
            for word in words:
                word = word.lower()  # Convert to lowercase to handle case-insensitive counts
                if word in word_counts:
                    word_counts[word] += 1
                else:
                    word_counts[word] = 1
    return word_counts

def main():
    filename = 'sample.txt'  # Replace with the path to your text file
    word_counts = count_word_occurrences(filename)
    
    print("Word Occurrences:")
    for word, count in word_counts.items():
        print(f"{word}: {count}")

if __name__ == "__main__":
    main()
```

5. **Functional Programming:**
Write a function that takes a list of numbers and returns a new list containing only the even numbers. Use the `filter()` function along with a lambda function to achieve this.

```python
#-----------------using lambda-------------------
def even(inp_list):
    temp = list(filter(lambda x:x%2 ==0, inp_list))
    return temp
    
print(even([1,2,3,4,5,6,7,8,9,10]))

#---------------------using function--------------
def is_even(number):
    return number % 2 == 0

def even(numbers):
		even_numbers = list(filter(is_even, numbers))
		return even_numbers

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(even(numbers))  # Output: [2, 4, 6, 8, 10]
```

6. **Advanced Data Structures:**
Implement a simple stack data structure using a Python list. Create methods `push()`, `pop()`, and `peek()` to manipulate the stack. Test your stack by pushing and popping elements.

```python
class Stack:
    def __init__(self):
        self.my_list = []

    def push(self, val):
        self.my_list.append(val)

    def pop(self):
        if len(self.my_list) > 0:
            return self.my_list.pop()
        else:
            print("Nothing to pop.")
            return None  # Return None to indicate no value was popped

    def peek(self):
        if len(self.my_list) > 0:
            return self.my_list[-1]
        else:
            print("Stack is empty.")
            return None  # Return None to indicate an empty stack

# Test the stack
stack = Stack()
stack.push(5)
stack.push(6)
print("Peek:", stack.peek())  # Output: Peek: 6
print("Pop:", stack.pop())    # Output: Pop: 6
print("Pop:", stack.pop())    # Output: Pop: 5
print("Pop:", stack.pop())    # Output: Nothing to pop.
print("Peek:", stack.peek())  # Output: Stack is empty.
```

7. **Object-Oriented Design:**
Design a simple banking system with classes `Bank`, `Account`, and `Transaction`. Create methods for opening accounts, depositing and withdrawing funds, and displaying account details. Use encapsulation and proper design principles.

```python
class Bank:
    def __init__(self, name, branch):
        self.name = name
        self.branch = branch
        self.accounts = []

    def create_account(self, account_id, username, initial_balance=0.0):
        account = Account(account_id, username, initial_balance)
        self.accounts.append(account)
        return account

    def find_account(self, account_id):
        for account in self.accounts:
            if account.account_id == account_id:
                return account
        return None

class Account:
    def __init__(self, account_id, username, balance=0.0):
        self.account_id = account_id
        self.username = username
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print("Deposit successful.")
        else:
            print("Invalid amount for deposit.")

    def withdraw(self, amount):
        if amount > 0 and self.balance >= amount:
            self.balance -= amount
            print("Withdrawal successful.")
        else:
            print("Insufficient funds or invalid amount for withdrawal.")

    def display_details(self):
        print("================ Account Details ================")
        print(f"Account ID: {self.account_id}")
        print(f"Username: {self.username}")
        print(f"Balance: {self.balance}")
        print("===============================================")

class Transaction:
    @staticmethod
    def transfer(sender, receiver, amount):
        if amount > 0 and sender.balance >= amount:
            sender.withdraw(amount)
            receiver.deposit(amount)
            print("Transfer successful.")
        else:
            print("Insufficient funds or invalid amount for transfer.")

# Create Bank instance
my_bank = Bank("MyBank", "Main Branch")

# Open Accounts
account1 = my_bank.create_account("A1001", "Alice", 5000)
account2 = my_bank.create_account("A1002", "Bob")

# Deposit and Withdraw
account1.deposit(1000)
account2.withdraw(500)

# Display Account Details
account1.display_details()
account2.display_details()

# Perform Transfer
Transaction.transfer(account1, account2, 1500)

# Display Account Details Again
account1.display_details()
account2.display_details()
```

8. **Regular Expressions:**
Write a program that validates email addresses. Prompt the user to enter an email address and check if it matches a valid email pattern using regular expressions.

 ```python
import re

def validate_email(email):
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    if re.match(pattern, email):
        return True
    else:
        return False

def main():
    email = input("Enter an email address: ")
    if validate_email(email):
        print("Valid email address.")
    else:
        print("Invalid email address.")

if __name__ == "__main__":
    main()
```

9. **Modules and Packages:**
Create a Python module that defines functions for basic arithmetic operations (addition, subtraction, multiplication, division). Use this module in another script to perform calculations.

```python
# my_module.py

def greet(name):
    return f"Hello, {name}!"
```

```python
# main_script.py
import my_module

name = input("Enter your name: ")
greeting = my_module.greet(name)
print(greeting)
```

10. **Lambda Functions and Sorting:**
Create a list of tuples, each containing a name and an age. Sort the list based on age using the `sorted()` function and a lambda function as the key.

```python
# Create a list of tuples (name, age)
people = [("Alice", 25), ("Bob", 22), ("Charlie", 28), ("David", 20)]

# Sort the list based on age using a lambda function as the sorting key
sorted_people = sorted(people, key=lambda x: x[1])

# Print the sorted list
for person in sorted_people:
    print(f"Name: {person[0]}, Age: {person[1]}")
```
