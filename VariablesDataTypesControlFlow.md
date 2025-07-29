# 🐍 Python Deep Dive: Variables, Data Types & Control Flow

-
## 📌 Section 1: Variable Fundamentals

### ✅ What's the difference between `=`, `==`, and `is`?

| Operator | Meaning             | Example  | Notes                                                          |
| -------- | ------------------- | -------- | -------------------------------------------------------------- |
| `=`      | Assignment operator | `a = 5`  | Assigns value to variable                                      |
| `==`     | Equality operator   | `a == b` | Compares values                                                |
| `is`     | Identity operator   | `a is b` | Checks if two variables point to the **same object in memory** |

---

### ✅ How does Python handle variable assignment and memory allocation?

* Python uses **references**. When you assign a variable, it **binds the name** to an object in memory.
* For example:

  ```python
  a = [1, 2]
  b = a  # Both point to the same list
  ```
* Python uses automatic **garbage collection** to manage memory.

---

### ✅ What are mutable vs immutable types? Give examples.

| Type     | Mutable             | Immutable                                 |
| -------- | ------------------- | ----------------------------------------- |
| Examples | list, dict, set     | int, float, str, tuple, frozenset         |
| Behavior | Can change in place | Cannot change without creating new object |

```python
# Immutable
x = "hello"
x = x.upper()  # Creates a new string object

# Mutable
lst = [1, 2]
lst.append(3)  # Modifies the original object
```

---

### ✅ Explain variable scope: local, global, and nonlocal

* **Local**: Defined within a function or block
* **Global**: Defined at the top level of the script
* **nonlocal**: Refers to variables in the **enclosing (non-global) scope**

```python
x = 10  # Global

def outer():
    x = 5  # Enclosing scope
    def inner():
        nonlocal x
        x += 1
    inner()
    print(x)
```

---

### ✅ What happens when you assign one variable to another in Python?

* The new variable **references the same object** (no copy made).

```python
a = [1, 2]
b = a
b.append(3)
print(a)  # Output: [1, 2, 3]
```

* To make a **copy**, use `copy()` or slicing: `b = a[:]`.

---

## 📌 Section 2: Data Types Deep Dive

### ✅ What are the built-in numeric types in Python and their differences?

| Type      | Description                 |
| --------- | --------------------------- |
| `int`     | Integer (unlimited size)    |
| `float`   | Floating-point number       |
| `complex` | Complex numbers like `3+4j` |

---

### ✅ How does Python handle integer overflow?

* Python’s `int` type **automatically grows** in size.
* Unlike C/Java, Python avoids overflow errors by allocating more memory as needed.

```python
print(10 ** 100)  # Works without overflow
```

---

### ✅ What's the difference between `str`, `bytes`, and `bytearray`?

| Type        | Description                 | Mutable? |
| ----------- | --------------------------- | -------- |
| `str`       | Unicode text                | ❌        |
| `bytes`     | Immutable sequence of bytes | ❌        |
| `bytearray` | Mutable version of bytes    | ✅        |

Used when dealing with **binary data**, like files or network packets.

---

### ✅ When would you use `None`, and how is it different from empty values?

* `None` represents **absence of value**.
* It's not the same as `0`, `''`, or `[]`.

```python
x = None
if x is None:
    print("No value")
```

---

### ✅ What are type hints and how do they work?

* Syntax for **optional type checking** (not enforced at runtime).
* Tools like `mypy` or IDEs use it for analysis.

```python
def greet(name: str) -> str:
    return f"Hello, {name}"
```

---

## 📌 Section 3: Control Flow Mastery

### ✅ if/elif/else vs nested conditionals

* `if/elif/else`: clean, readable, flat structure
* Nested `if`: deeper indentation, harder to read

```python
# Preferred
if score > 90:
    grade = 'A'
elif score > 80:
    grade = 'B'
else:
    grade = 'C'
```

---

### ✅ How do `and`, `or`, `not` work with short-circuiting?

* **Short-circuiting** means evaluation **stops as soon as result is known**.

```python
a = True or print("Won't print")  # Short-circuited
b = False and print("Won't print")  # Short-circuited
```

---

### ✅ Truthy and Falsy Values

**Falsy values**:

* `False`
* `None`
* `0` (int, float, complex)
* `''` (empty string)
* `[]` (empty list)
* `{}` (empty dict)
* `set()`, `tuple()`

Everything else is **truthy**.

---

### ✅ How do for loops work differently with different data types?

* `for` loops iterate over **iterables**.

```python
for i in [1, 2, 3]:      # list
for c in "hello":        # string
for k in {'a': 1}:       # dictionary keys
```

---

### ✅ When to use while vs for loops?

| Use `for` when...             | Use `while` when...           |
| ----------------------------- | ----------------------------- |
| Iterating over known sequence | Condition-based looping       |
| You know the number of steps  | Loop depends on dynamic state |

---

## 📌 Section 4: Advanced Control Flow

### ✅ What are `break`, `continue`, and `pass`?

| Keyword    | Purpose                    |
| ---------- | -------------------------- |
| `break`    | Exit the loop immediately  |
| `continue` | Skip the current iteration |
| `pass`     | Do nothing (placeholder)   |

---

### ✅ How does the `else` clause work with loops and `try/except`?

```python
# Loops
for i in range(5):
    if i == 3:
        break
else:
    print("Completed loop without break")  # Only runs if no break

# Try/except
try:
    x = 1 / 1
except ZeroDivisionError:
    pass
else:
    print("No exception occurred")
```

---

### ✅ What are nested loops and how to control them?

* Loops inside loops.
* Use flags, `break`, or `return` to manage flow.

```python
for i in range(3):
    for j in range(3):
        if j == 1:
            break
```

---

### ✅ How do you handle multiple conditions efficiently?

Use logical operators:

```python
if a > 5 and b < 10 and c != 0:
    ...
```

Avoid deeply nested `if`s. Use early `return`, `continue`, or `guard clauses`.

---

### ✅ What’s the walrus operator (`:=`) and when to use it?

Introduced in Python 3.8.

* Assign and return a value in a single expression.

```python
if (n := len(data)) > 10:
    print(f"List is too long: {n} items")
```

Useful for:

* Loop conditions
* Reducing redundancy
* Assigning in expressions

---

