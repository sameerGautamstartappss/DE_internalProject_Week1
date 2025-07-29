# DE_internalProject_Week1
# 🐍 Python Week 1: Intermediate Bootcamp

## Overview

This 5-day bootcamp takes you from a solid Python foundation through key intermediate concepts like functional programming, OOP, advanced Pandas, and working with APIs. Each day includes both **theory** and **practical questions**, concluding in a **capstone project** to integrate all your learning.

---

## 📅 Day 1: Python Fundamentals & Data Structures

### 🔍 Theory:

* Recap: Variables, Data Types, Control Flow (if-else, loops)
* Data Structures Deep Dive:

  * **Lists**: slicing, comprehensions, methods
  * **Dictionaries**: key-value logic, comprehensions
  * **Tuples**: immutability, packing/unpacking
  * **Sets**: uniqueness, operations

### 💻 Practical Questions:

1. **Dictionary Comprehension**:

   ```python
   squares = {x: x**2 for x in range(1, 11)}
   ```
2. **Sorting a List of Dictionaries**:

   ```python
   sorted_list = sorted(data_list, key=lambda x: x['key_name'])
   ```
3. **Explain Time Complexity**:

   * `list`: O(n) for checking membership (`x in list`)
   * `set`: O(1) average time for membership (`x in set`) due to hashing

---

## 📅 Day 2: Functions, OOP & Error Handling

### 🔍 Theory:

* **Lambda functions**
* **map()**, **filter()**, **reduce()**
* **Classes, Objects, Inheritance**
* **Exception Handling**: `try-except-else-finally`, `raise`

### 💻 Practical Questions:

1. **`DataExtractor` Class**:

   ```python
   import json, csv

   class DataExtractor:
       def read_csv(self, filename):
           with open(filename, 'r') as f:
               return list(csv.DictReader(f))

       def read_json(self, filename):
           with open(filename, 'r') as f:
               return json.load(f)
   ```
2. **Execution Time Decorator**:

   ```python
   import time

   def timer(func):
       def wrapper(*args, **kwargs):
           start = time.time()
           result = func(*args, **kwargs)
           print(f"Executed in {time.time() - start:.4f}s")
           return result
       return wrapper
   ```
3. **Custom Exceptions**:

   ```python
   class MyCustomError(Exception):
       pass

   raise MyCustomError("Something went wrong!")
   ```

---

## 📅 Day 3: Advanced Pandas

### 🔍 Theory:

* **MultiIndex**, **GroupBy**, **Merging**
* `merge()`, `join()`, `concat()`
* `pivot_table()` for summaries

### 💻 Practical Questions:

1. **Outer Join Two DataFrames**:

   ```python
   pd.merge(df1, df2, how='outer', on='key_column')
   ```
2. **Pivot Table Example**:

   ```python
   df.pivot_table(values='Sales', index='Region', columns='Category', aggfunc='sum')
   ```
3. **merge() vs join()**:

   * `merge()` is more flexible, SQL-style joins.
   * `join()` is simpler and aligns on index by default.

---

## 📅 Day 4: Working with APIs

### 🔍 Theory:

* **HTTP Methods**: `GET`, `POST`
* **Requests Library**: `.get()`, `.post()`
* **Parsing JSON**
* **Authentication**: API Keys, OAuth
* **Rate Limiting Handling**

### 💻 Practical Questions:

1. **Fetch from Public API**:

   ```python
   import requests
   response = requests.get("https://api.github.com/users/octocat")
   print(response.json())
   ```
2. **GET Request with Params**:

   ```python
   params = {'q': 'python'}
   r = requests.get('https://api.example.com/search', params=params)
   ```
3. **Handle Rate Limiting**:

   * Check headers like `X-RateLimit-Remaining`
   * Use `time.sleep()` to wait
   * Exponential backoff strategy

---

## 📅 Day 5: Weekly Project 1 – Public API Data Aggregator

### 🧠 Project Goal:

Build a script to fetch and enrich post and comment data from a public API. Combine and save the results using Pandas.

### 📌 Tasks:

1. **Fetch posts and comments**:

   ```python
   posts = requests.get("https://jsonplaceholder.typicode.com/posts").json()
   comments = requests.get("https://jsonplaceholder.typicode.com/comments").json()
   ```

2. **Count comments per post**:

   ```python
   from collections import defaultdict

   comment_count = defaultdict(int)
   for comment in comments:
       comment_count[comment['postId']] += 1
   ```

3. **Create and enrich DataFrame**:

   ```python
   import pandas as pd

   df_posts = pd.DataFrame(posts)
   df_posts['comment_count'] = df_posts['id'].map(comment_count)
   ```

4. **Save to CSV**:

   ```python
   df_posts.to_csv("posts_with_comment_counts.csv", index=False)
   ```

### ✅ Topics Covered:

* Data structures (dict, list)
* OOP (optional modular approach)
* File I/O
* API requests
* JSON parsing
* Pandas operations (DataFrames, merge, map)
* CSV export

---

## 📚 Resources

* [Python Docs](https://docs.python.org/3/)
* [Pandas Guide](https://pandas.pydata.org/docs/)
* [Requests Library](https://requests.readthedocs.io/)
* [JSONPlaceholder API](https://jsonplaceholder.typicode.com/)

---

