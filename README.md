# Python Common Errors Guide

A comprehensive guide to understanding and fixing common Python errors. This guide is designed for both beginners and experienced developers.

---

## Table of Contents

1. [Syntax Errors](#syntax-errors)
2. [Indentation Errors](#indentation-errors)
3. [Name Errors](#name-errors)
4. [Type Errors](#type-errors)
5. [Index Errors](#index-errors)
6. [Key Errors](#key-errors)
7. [Attribute Errors](#attribute-errors)
8. [Value Errors](#value-errors)
9. [Zero Division Error](#zero-division-error)
10. [Import Errors](#import-errors)
11. [File Not Found Error](#file-not-found-error)
12. [Runtime Errors](#runtime-errors)

---

## Syntax Errors

**What it means:** You've written code that doesn't follow Python's grammar rules.

### Example 1: Missing Colon

```python
# ❌ WRONG CODE
if x > 5
    print("x is greater than 5")
```

**Error Message:**
```
SyntaxError: invalid syntax
```

**✅ CORRECT CODE:**
```python
if x > 5:
    print("x is greater than 5")
```

### Example 2: Missing Quotes

```python
# ❌ WRONG CODE
name = Rahul
```

**Error Message:**
```
SyntaxError: invalid syntax
```

**✅ CORRECT CODE:**
```python
name = "Rahul"
```

### Example 3: Missing Parentheses

```python
# ❌ WRONG CODE
print "Namaste World"
```

**Error Message:**
```
SyntaxError: Missing parentheses in call to 'print'
```

**✅ CORRECT CODE:**
```python
print("Namaste World")
```

---

## Indentation Errors

**What it means:** Python uses indentation (spaces/tabs) to define code blocks. Inconsistent indentation causes errors.

### Example 1: Missing Indentation

```python
# ❌ WRONG CODE
def greet():
print("Namaste")
```

**Error Message:**
```
IndentationError: expected an indented block
```

**✅ CORRECT CODE:**
```python
def greet():
    print("Namaste")
```

### Example 2: Mixing Tabs and Spaces

```python
# ❌ WRONG CODE
def calculate():
    x = 10
	y = 20  # This line uses tab instead of spaces
    return x + y
```

**Error Message:**
```
IndentationError: unindent does not match any outer indentation level
```

**✅ CORRECT CODE:**
```python
def calculate():
    x = 10
    y = 20  # Use consistent spacing (4 spaces recommended)
    return x + y
```

---

## Name Errors

**What it means:** You're trying to use a variable or function that doesn't exist or hasn't been defined yet.

### Example 1: Variable Not Defined

```python
# ❌ WRONG CODE
print(age)
```

**Error Message:**
```
NameError: name 'age' is not defined
```

**✅ CORRECT CODE:**
```python
age = 25
print(age)
```

### Example 2: Typo in Variable Name

```python
# ❌ WRONG CODE
user_name = "Priya"
print(username)  # Typo: underscore missing
```

**Error Message:**
```
NameError: name 'username' is not defined
```

**✅ CORRECT CODE:**
```python
user_name = "Priya"
print(user_name)
```

---

## Type Errors

**What it means:** You're trying to perform an operation on incompatible data types.

### Example 1: Adding String and Integer

```python
# ❌ WRONG CODE
age = 25
message = "I am " + age + " years old"
```

**Error Message:**
```
TypeError: can only concatenate str (not "int") to str
```

**✅ CORRECT CODE:**
```python
age = 25
message = "I am " + str(age) + " years old"
# OR
message = f"I am {age} years old"
```

### Example 2: Wrong Number of Arguments

```python
# ❌ WRONG CODE
def add(a, b):
    return a + b

result = add(5)
```

**Error Message:**
```
TypeError: add() missing 1 required positional argument: 'b'
```

**✅ CORRECT CODE:**
```python
def add(a, b):
    return a + b

result = add(5, 3)
```

### Example 3: Calling Non-Callable Object

```python
# ❌ WRONG CODE
number = 42
result = number()
```

**Error Message:**
```
TypeError: 'int' object is not callable
```

**✅ CORRECT CODE:**
```python
number = 42
result = number * 2
```

---

## Index Errors

**What it means:** You're trying to access an element in a list/string using an index that doesn't exist.

### Example 1: List Index Out of Range

```python
# ❌ WRONG CODE
fruits = ["apple", "banana", "orange"]
print(fruits[3])
```

**Error Message:**
```
IndexError: list index out of range
```

**✅ CORRECT CODE:**
```python
fruits = ["apple", "banana", "orange"]
print(fruits[2])  # Remember: indexing starts at 0
# OR check length first
if len(fruits) > 3:
    print(fruits[3])
```

### Example 2: String Index Out of Range

```python
# ❌ WRONG CODE
word = "Namaste"
print(word[10])
```

**Error Message:**
```
IndexError: string index out of range
```

**✅ CORRECT CODE:**
```python
word = "Namaste"
print(word[6])  # Last character
# OR
print(word[-1])  # Access last character using negative indexing
```

---

## Key Errors

**What it means:** You're trying to access a dictionary key that doesn't exist.

### Example 1: Missing Dictionary Key

```python
# ❌ WRONG CODE
person = {"name": "Arjun", "age": 30}
print(person["email"])
```

**Error Message:**
```
KeyError: 'email'
```

**✅ CORRECT CODE:**
```python
person = {"name": "Arjun", "age": 30}

# Option 1: Use get() method
print(person.get("email", "Not provided"))

# Option 2: Check if key exists
if "email" in person:
    print(person["email"])
else:
    print("Email not found")
```

---

## Best Practices to Avoid Errors

### 1. Use Try-Except Blocks

```python
try:
    result = risky_operation()
except SpecificError as e:
    print(f"Error occurred: {e}")
```

### 2. Validate Input

```python
age = input("Enter your age: ")
if age.isdigit():
    age = int(age)
else:
    print("Please enter a valid number")
```

### 3. Use Type Hints (Python 3.5+)

```python
def add_numbers(a: int, b: int) -> int:
    return a + b
```

### 4. Check Before Accessing

```python
# For lists
if len(my_list) > index:
    value = my_list[index]

# For dictionaries
if key in my_dict:
    value = my_dict[key]
```

### 5. Use Debugging Tools

```python
# Add print statements
print(f"Debug: variable value is {variable}")

# Use debugger
import pdb; pdb.set_trace()
```

---

## Quick Reference: Error Types Summary

| Error Type | Common Cause | Quick Fix |
|------------|--------------|-----------|
| `SyntaxError` | Missing colons, quotes, parentheses | Check syntax carefully |
| `IndentationError` | Wrong spacing | Use 4 spaces consistently |
| `NameError` | Variable not defined | Define variable before use |
| `TypeError` | Wrong data type operation | Convert types properly |
| `IndexError` | Index out of range | Check list/string length |

---

## Additional Resources

- [Official Python Documentation](https://docs.python.org/3/)
- [Python Error Handling](https://docs.python.org/3/tutorial/errors.html)
- [PEP 8 Style Guide](https://pep8.org/)

---
