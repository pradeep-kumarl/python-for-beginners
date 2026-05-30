# 🐍 Python Notes

> Handwritten classroom notes — transcribed and organized

---

## Table of Contents

1. [Running Python](#1-running-python)
2. [Batch Mode](#2-batch-mode)
3. [help() System](#3-help-system)
4. [Keywords](#4-keywords)
5. [Modules & Builtins](#5-modules--builtins)
6. [Indentation](#6-indentation)
7. [Comments](#7-comments)
8. [print() Interface](#8-print-interface)
9. [print() Parameters](#9-print-parameters)
10. [Statement Separator](#10-statement-separator)
11. [Variables & Data Types](#11-variables--data-types)
12. [Memory & IDs](#12-memory--ids)
13. [Variable Naming Rules](#13-variable-naming-rules)
14. [Input from User](#14-input-from-user)
15. [Operators](#15-operators)

---

## 1. Running Python

- Open command prompt → type `python` → opens interpreter
- Can use **Notepad++** or **Jupyter Notebook** (`.ipynb`)
- Run modes: **File mode / Batch mode / Script mode**
- Python documentation can be used in interpreter mode

---

## 2. Batch Mode

- Must explicitly say what to do

```python
print(7 + 4)
```

---

## 3. help() System

| Command | Description |
|---|---|
| `help()` | Activates help mode (1,63,000+ modules) |
| `help > print` | Details of print function |
| `help > input` | Shows 3rd party module info |
| `help > modules` | Lists all modules |
| `help > keywords` | Lists all reserved keywords |
| `help > symbols` | Lists all symbols (`+`, `-`, `**`, etc.) |
| `help > topics` | Shows all topics |

```python
import math
math.__doc__    # shows documentation of math module
```

---

## 4. Keywords

- Python keywords cannot be used as variable names → causes **Invalid Syntax**
- Technically you *can* use a keyword as a variable name (bad practice)

```python
for print = 45        # bad practice — don't do this
type(print)           # → <class 'builtin_function_method'>

print = 45            # reassigning print
print(print)          # → TypeError: 'int' object is not callable
```

---

## 5. Modules & Builtins

```python
import builtins
dir(builtins)           # lists all built-in functions

builtins.print(print)   # call print using builtins module
```

> To use any function from any module → must `import` it first

---

## 6. Indentation

- Python uses indentation to define code blocks
- Extra space before code → **IndentationError**
- Indentation is only required for: **branching, looping, selection statements**
- Types of errors: `SyntaxError`, `IndentationError`, `TypeError`

```python
# ❌ Wrong
 print(7+4)      # IndentationError

# ✅ Correct
print(7+4)
```

---

## 7. Comments

```python
# Single line comment

'''
Multiline
comment (actually a string)
'''

"""
Also multiline
"""
```

> ⚠️ There is **no true multiline comment** in Python.  
> `'''` is just a **pure string** — if not assigned to a variable, Python ignores it.

```python
# If assigned → acts as multiline string
s1 = '''
print(2.6)
print("Pradeep")
'''
```

---

## 8. print() Interface

```
Function → input (arguments) → [ ??? ] → output (return value)
Interface = Input + Output
```

```python
print(10, 13, 17, 19, 90)
# input  → arguments
# output → return value (None)

print(print(10, 13, 17, 19, 90))
# Output:
# 10 13 17 19 90
# None
```

> `None` → the function returned nothing (important concept)

```python
a = None
print(a, type(a))   # None <class 'NoneType'>
```

---

## 9. print() Parameters

```python
print(*args, sep=' ', end='\n')
```

```python
print(10, 13, 17, 19, 90, sep='▼', end='ended!')
# Output: 10▼13▼17▼19▼90ended!

print(10, 13, 17, 19, 90, sep='|', end='\t')
# Output: 10|13|17|19|90	

# Adding (:) between numbers
print(10, 13, 17, 19, 90, sep='|11|')
# Output: 10|11|13|11|17|11|19|11|90
```

---

## 10. Statement Separator

```python
print(10, 11, 17, 19, 20); print("This is num")
# Output:
# 10 11 17 19 20
# This is num
```

> ⚠️ Capital `Print` → **NameError** (not SyntaxError)  
> Python assumes it's a function name → Runtime error  
> Runtime error = **Exception** (TypeError, IndexError, NameError, etc.)

> 🔑 **Python is case sensitive**

---

## 11. Variables & Data Types

```python
age = 45
# Right side → literal value / constant
# Left side  → variable
```

### Types of Constants

| Type | Example | Output of type() |
|---|---|---|
| int | `age = 1` | `<class 'int'>` |
| float | `age = 1.2` | `<class 'float'>` |
| str | `age = "hello"` | `<class 'str'>` |
| complex | `age = 3+4j` | `<class 'complex'>` |
| bool | `age = True` | `<class 'bool'>` |

```python
print(type(False))   # <class 'bool'>
print(type(age))     # check type of variable
```

> **Dynamic execution** → same variable can hold different types at runtime  
> Type changes → operation and memory changes too

---

## 12. Memory & IDs

```python
import sys
age = 45
print(sys.getsizeof(age))   # → 28 bytes
```

> Python uses **object-oriented paradigm** → everything is an object → more memory than other languages

```python
a = 1
print(age, id(a))   # id = unique memory address identifier
```

### ID Behaviour

```python
a = 5
b = 5
# → same IDs (Python optimization for -256 to 255)

a = 8998
b = 8998
# → different IDs (large numbers get new memory)
```

```python
>>> dir(int)   # shows all functions/methods belonging to int class
```

---

## 13. Variable Naming Rules

| Rule | Example | Result |
|---|---|---|
| Cannot start with number | `1number = 10` | ❌ Invalid Syntax |
| Cannot start with space | `[space]number = 10` | ❌ Invalid Syntax |
| Can use underscore prefix | `_number = 10` | ✅ (but means *private* — not recommended) |
| Normal naming | `number = 10` | ✅ |

---

## 14. Input from User

```python
print("Enter the number")
number = input()
print(number, type(number))
# Output: 67 <class 'str'>
```

> ⚠️ `input()` **always returns string** in Python 3

### Converting Input Type

```python
number = int(input())       # type conversion / constructor function
```

> Problem: if user types text (e.g. `Pradeep`) when int expected → **ValueError**

### Using eval()

```python
print("Enter the number")
number = eval(input())
print(number, type(number))
# Input: 67   → int
# Input: 67.8 → float
# Input: 4+5j → complex
```

> ⚠️ **Avoid `eval()`** in Python 3 — it exists but is a security risk. Not recommended for production.

---

## 15. Operators

### Types of Operators

| # | Type | Symbols |
|---|---|---|
| 1 | Arithmetic | `+`, `-`, `*`, `/`, `//`, `%`, `**` |
| 2 | Relational | `>`, `<`, `>=`, `<=`, `==`, `!=` |
| 3 | Logical | `and`, `or`, `not` |
| 4 | Identity | `is`, `is not` |
| 5 | Shorthand | `+=`, `-=`, `*=`, `//=` |
| 6 | Assignment | `=` |
| 7 | Membership | `in`, `not in` |
| 8 | Bitwise | `&`, `\|` (integers only) |

### Arithmetic Examples

```python
10 ** 3     # → 1000  (power)
10 // 3     # → 3     (floor division)
10 % 3      # → 1     (modulo / remainder)
10 / 3      # → 3.33  (float division)
```

### String Operators

```python
"3" + "5"       # → "35"    (concatenation)
"3" * 5         # → "33333" (repetition)
(3+5) + (1+4)   # → 13      (int addition)
```

> ⚠️ `int + str` → **TypeError** (not allowed)  
> `*` works as **repetition operator** for strings

### Bitwise AND Truth Table

| A | B | A and B |
|---|---|---|
| 1 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 1 | 1 |
| 0 | 0 | 0 |

### Short Circuit (and)

```python
1 and 67        # → 67
67 and 1        # → 1

a = 5
67 and (a == 5) # → 67 and True → 67
```

### String Comparison (Lexicographical)

```python
"pes" > "abc"   # → True  (compares ord values)
ord("p")        # → 112
ord("a")        # → 97

"PES" == "PES"  # → True
"PES" != "PES"  # → False
```

### OS System Command

```python
import os
os.system('cls')    # clears CMD screen (Windows)
```

---

## Key Takeaways

- Python is **case sensitive**
- Everything in Python is an **object**
- `input()` always returns **string**
- Use `int()`, `float()`, `eval()` for type conversion
- **Indentation** defines blocks (not `{}` like other languages)
- `None` means a function returned **no value**
- `id()` gives the **memory address** of an object
- Small integers (-256 to 255) share the **same ID** (optimization)

---

*Notes from Python classroom session — PESIT*
