# NumPy in Python

## Table of Contents

- [NumPy in Python](#numpy-in-python)
  - [Table of Contents](#table-of-contents)
  - [1. What Is NumPy?](#1-what-is-numpy)
  - [2. What Is NumPy Used For?](#2-what-is-numpy-used-for)
    - [2.1 Working With Arrays](#21-working-with-arrays)
    - [2.2 Mathematical Computation](#22-mathematical-computation)
    - [2.3 Statistical Analysis](#23-statistical-analysis)
    - [2.4 Matrix and Linear Algebra](#24-matrix-and-linear-algebra)
    - [2.5 Data Science and Machine Learning](#25-data-science-and-machine-learning)
  - [3. Creating NumPy Arrays](#3-creating-numpy-arrays)
    - [3.1 Create an Array From a Python List](#31-create-an-array-from-a-python-list)
    - [3.2 Create Arrays With `zeros()`](#32-create-arrays-with-zeros)
    - [3.3 Create Arrays With `ones()`](#33-create-arrays-with-ones)
    - [3.4 Create Arrays With `arange()`](#34-create-arrays-with-arange)
    - [3.5 Create Arrays With `linspace()`](#35-create-arrays-with-linspace)
    - [3.6 Create an Identity Matrix](#36-create-an-identity-matrix)
  - [4. NumPy Array Properties](#4-numpy-array-properties)
    - [4.1 Number of Dimensions](#41-number-of-dimensions)
    - [4.2 Shape](#42-shape)
    - [4.3 Number of Elements](#43-number-of-elements)
    - [4.4 Data Type](#44-data-type)
    - [4.5 Change the Data Type](#45-change-the-data-type)
  - [5. Indexing, Slicing, and Reshaping](#5-indexing-slicing-and-reshaping)
    - [5.1 One-Dimensional Indexing](#51-one-dimensional-indexing)
    - [5.2 Two-Dimensional Indexing](#52-two-dimensional-indexing)
    - [5.3 Slicing](#53-slicing)
    - [5.4 Reshaping](#54-reshaping)
    - [5.5 Flattening an Array](#55-flattening-an-array)
  - [6. Mathematical Operations and Broadcasting](#6-mathematical-operations-and-broadcasting)
    - [6.1 Arithmetic Operations](#61-arithmetic-operations)
    - [6.2 Scalar Operations](#62-scalar-operations)
    - [6.3 Broadcasting](#63-broadcasting)
    - [6.4 Comparison Operations](#64-comparison-operations)
    - [6.5 Aggregation](#65-aggregation)
  - [7. Commonly Used NumPy Functions](#7-commonly-used-numpy-functions)
  - [8. Exercises](#8-exercises)
    - [Exercise 1 — Create an Array](#exercise-1--create-an-array)
    - [Exercise 2 — Array Properties](#exercise-2--array-properties)
    - [Exercise 3 — Zeros and Ones](#exercise-3--zeros-and-ones)
    - [Exercise 4 — Generate a Sequence](#exercise-4--generate-a-sequence)
    - [Exercise 5 — Generate Evenly Spaced Values](#exercise-5--generate-evenly-spaced-values)
    - [Exercise 6 — Indexing](#exercise-6--indexing)
    - [Exercise 7 — Slicing](#exercise-7--slicing)
    - [Exercise 8 — Matrix Indexing](#exercise-8--matrix-indexing)
    - [Exercise 9 — Reshape an Array](#exercise-9--reshape-an-array)
    - [Exercise 10 — Mathematical Operations](#exercise-10--mathematical-operations)
    - [Exercise 11 — Statistics](#exercise-11--statistics)
    - [Exercise 12 — Filtering](#exercise-12--filtering)
    - [Exercise 13 — Replace Values With `np.where()`](#exercise-13--replace-values-with-npwhere)
    - [Exercise 14 — Row and Column Operations](#exercise-14--row-and-column-operations)
    - [Exercise 15 — Find Maximum and Minimum Indices](#exercise-15--find-maximum-and-minimum-indices)
    - [Exercise 16 — Unique Values and Sorting](#exercise-16--unique-values-and-sorting)
    - [Exercise 17 — Matrix Multiplication](#exercise-17--matrix-multiplication)
    - [Exercise 18 — Random Dataset](#exercise-18--random-dataset)
    - [Exercise 19 — Normalize Data](#exercise-19--normalize-data)
    - [Exercise 20 — Mini Data-Science Task](#exercise-20--mini-data-science-task)
  - [Learning Path](#learning-path)

NumPy (Numerical Python) is one of the fundamental libraries for numerical computing in Python. It provides powerful data structures and functions for working with arrays, matrices, numerical calculations, statistics, linear algebra, and scientific computing.

---

## 1. What Is NumPy?

**NumPy** stands for **Numerical Python**.

It provides:

* The `ndarray` object for storing multidimensional numerical data.
* Fast mathematical operations on arrays.
* Functions for statistics and aggregation.
* Linear algebra operations.
* Random number generation.
* Array reshaping, slicing, indexing, and broadcasting.
* Tools that are widely used by libraries such as Pandas, Scikit-learn, SciPy, and many machine-learning frameworks.

Install NumPy with:

```bash
pip install numpy
```

Check the installed version:

```python
import numpy as np

print(np.__version__)
```

The common convention is to import NumPy using the alias:

```python
import numpy as np
```

---

## 2. What Is NumPy Used For?

NumPy is mainly used for **efficient numerical and array-based computation**.

### 2.1 Working With Arrays

Instead of processing numbers one by one using Python lists, NumPy allows you to operate on entire arrays.

```python
import numpy as np

numbers = np.array([1, 2, 3, 4, 5])

print(numbers)
print(numbers * 2)
```

Output:

```text
[1 2 3 4 5]
[ 2  4  6  8 10]
```

This is useful when working with large amounts of numerical data.

### 2.2 Mathematical Computation

NumPy provides mathematical functions such as:

```python
np.sqrt()
np.log()
np.exp()
np.sin()
np.cos()
```

Example:

```python
numbers = np.array([1, 4, 9, 16])

print(np.sqrt(numbers))
```

### 2.3 Statistical Analysis

NumPy provides common statistical operations:

```python
np.mean()
np.median()
np.std()
np.var()
np.min()
np.max()
np.sum()
```

Example:

```python
scores = np.array([70, 80, 90, 85, 75])

print("Mean:", np.mean(scores))
print("Maximum:", np.max(scores))
print("Minimum:", np.min(scores))
```

### 2.4 Matrix and Linear Algebra

NumPy can perform matrix operations used in mathematics, engineering, and machine learning.

```python
A = np.array([
    [1, 2],
    [3, 4]
])

B = np.array([
    [5, 6],
    [7, 8]
])

print(A + B)
print(A @ B)
```

### 2.5 Data Science and Machine Learning

NumPy is commonly used as a foundation for:

* Data preprocessing
* Feature engineering
* Numerical transformations
* Machine-learning algorithms
* Scientific computing
* Image processing
* Signal processing
* Statistical calculations

For example, a machine-learning dataset can be represented as a matrix:

```text
         Feature 1   Feature 2   Feature 3
Sample 1     10          20          30
Sample 2     15          25          35
Sample 3     12          22          32
```

This can be represented by a NumPy array:

```python
X = np.array([
    [10, 20, 30],
    [15, 25, 35],
    [12, 22, 32]
])
```

---

## 3. Creating NumPy Arrays

The main data structure in NumPy is the **NumPy array**, represented by `ndarray`.

### 3.1 Create an Array From a Python List

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(arr)
```

Create a two-dimensional array:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(matrix)
```

### 3.2 Create Arrays With `zeros()`

```python
arr = np.zeros(5)

print(arr)
```

Output:

```text
[0. 0. 0. 0. 0.]
```

Create a 2D array:

```python
matrix = np.zeros((2, 3))
```

### 3.3 Create Arrays With `ones()`

```python
arr = np.ones(5)

print(arr)
```

Create a 2D array:

```python
matrix = np.ones((3, 4))
```

### 3.4 Create Arrays With `arange()`

`np.arange()` creates evenly spaced values within a specified range.

```python
arr = np.arange(0, 10)

print(arr)
```

Output:

```text
[0 1 2 3 4 5 6 7 8 9]
```

You can specify a step:

```python
arr = np.arange(0, 10, 2)

print(arr)
```

Output:

```text
[0 2 4 6 8]
```

### 3.5 Create Arrays With `linspace()`

`np.linspace()` creates a specified number of evenly spaced values.

```python
arr = np.linspace(0, 1, 5)

print(arr)
```

Output:

```text
[0.   0.25 0.5  0.75 1.  ]
```

### 3.6 Create an Identity Matrix

```python
identity = np.eye(3)

print(identity)
```

Output:

```text
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

---

## 4. NumPy Array Properties

Understanding an array's properties is essential when working with NumPy.

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])
```

### 4.1 Number of Dimensions

Use `.ndim`:

```python
print(arr.ndim)
```

Output:

```text
2
```

### 4.2 Shape

Use `.shape`:

```python
print(arr.shape)
```

Output:

```text
(2, 3)
```

This means:

```text
2 rows
3 columns
```

### 4.3 Number of Elements

Use `.size`:

```python
print(arr.size)
```

Output:

```text
6
```

### 4.4 Data Type

Use `.dtype`:

```python
print(arr.dtype)
```

For example:

```text
int64
```

The exact integer type can vary depending on the operating system and NumPy build.

### 4.5 Change the Data Type

Use `.astype()`:

```python
arr = np.array([1, 2, 3, 4])

float_arr = arr.astype(float)

print(float_arr)
```

---

## 5. Indexing, Slicing, and Reshaping

### 5.1 One-Dimensional Indexing

```python
arr = np.array([10, 20, 30, 40, 50])

print(arr[0])
print(arr[2])
print(arr[-1])
```

Output:

```text
10
30
50
```

NumPy uses **zero-based indexing**, just like Python lists.

### 5.2 Two-Dimensional Indexing

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

print(matrix[0, 1])
print(matrix[2, 2])
```

Output:

```text
2
9
```

The syntax is:

```python
array[row, column]
```

### 5.3 Slicing

```python
arr = np.array([10, 20, 30, 40, 50])

print(arr[1:4])
```

Output:

```text
[20 30 40]
```

Slice a matrix:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

print(matrix[0:2, 1:3])
```

### 5.4 Reshaping

You can change the shape of an array using `.reshape()`.

```python
arr = np.arange(1, 7)

matrix = arr.reshape(2, 3)

print(matrix)
```

Output:

```text
[[1 2 3]
 [4 5 6]]
```

The total number of elements must remain unchanged.

For example:

```python
6 elements → 2 × 3
6 elements → 3 × 2
6 elements → 1 × 6
```

### 5.5 Flattening an Array

Convert a multidimensional array into one dimension:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

arr = matrix.flatten()

print(arr)
```

Output:

```text
[1 2 3 4 5 6]
```

---

## 6. Mathematical Operations and Broadcasting

NumPy allows mathematical operations to be performed directly on arrays.

### 6.1 Arithmetic Operations

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(a + b)
print(a - b)
print(a * b)
print(a / b)
```

Output:

```text
[5 7 9]
[-3 -3 -3]
[ 4 10 18]
[0.25 0.4  0.5 ]
```

### 6.2 Scalar Operations

A scalar can be applied to every element:

```python
arr = np.array([1, 2, 3, 4])

print(arr + 10)
print(arr * 2)
```

Output:

```text
[11 12 13 14]
[2 4 6 8]
```

### 6.3 Broadcasting

**Broadcasting** allows NumPy to perform operations between arrays with compatible shapes.

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

vector = np.array([10, 20, 30])

result = matrix + vector

print(result)
```

Output:

```text
[[11 22 33]
 [14 25 36]]
```

The vector is effectively applied to every row.

### 6.4 Comparison Operations

```python
arr = np.array([10, 20, 30, 40, 50])

print(arr > 25)
```

Output:

```text
[False False  True  True  True]
```

You can use the Boolean result to filter values:

```python
filtered = arr[arr > 25]

print(filtered)
```

Output:

```text
[30 40 50]
```

### 6.5 Aggregation

```python
arr = np.array([10, 20, 30, 40, 50])

print(np.sum(arr))
print(np.mean(arr))
print(np.min(arr))
print(np.max(arr))
print(np.std(arr))
```

For a matrix, you can calculate values by axis:

```python
matrix = np.array([
    [1, 2, 3],
    [4, 5, 6]
])

print(np.sum(matrix, axis=0))
print(np.sum(matrix, axis=1))
```

`axis=0` operates down the rows, producing one value for each column.

`axis=1` operates across the columns, producing one value for each row.

---

## 7. Commonly Used NumPy Functions

The following functions are especially useful in data science and AI.

| Function              | Purpose                                       |
| --------------------- | --------------------------------------------- |
| `np.array()`          | Create an array                               |
| `np.zeros()`          | Create an array filled with zeros             |
| `np.ones()`           | Create an array filled with ones              |
| `np.arange()`         | Create evenly spaced values using a step      |
| `np.linspace()`       | Create a fixed number of evenly spaced values |
| `np.reshape()`        | Change array shape                            |
| `np.concatenate()`    | Join arrays                                   |
| `np.vstack()`         | Stack arrays vertically                       |
| `np.hstack()`         | Stack arrays horizontally                     |
| `np.sort()`           | Sort values                                   |
| `np.unique()`         | Find unique values                            |
| `np.sum()`            | Calculate the sum                             |
| `np.mean()`           | Calculate the mean                            |
| `np.median()`         | Calculate the median                          |
| `np.std()`            | Calculate standard deviation                  |
| `np.var()`            | Calculate variance                            |
| `np.min()`            | Find minimum                                  |
| `np.max()`            | Find maximum                                  |
| `np.argmax()`         | Find index of maximum value                   |
| `np.argmin()`         | Find index of minimum value                   |
| `np.where()`          | Select values based on a condition            |
| `np.random.rand()`    | Generate random values                        |
| `np.random.randint()` | Generate random integers                      |
| `np.dot()`            | Calculate dot product                         |
| `np.transpose()`      | Transpose an array                            |

Example:

```python
import numpy as np

arr = np.array([5, 3, 8, 3, 1, 8])

print(np.unique(arr))
print(np.sort(arr))
print(np.argmax(arr))
```

Random numbers:

```python
np.random.seed(42)

numbers = np.random.randint(1, 101, size=10)

print(numbers)
```

The seed makes the generated sequence reproducible.

---

## 8. Exercises

The exercises below progress from basic array manipulation to operations commonly encountered in data science and machine learning.

### Exercise 1 — Create an Array

Create a NumPy array containing the numbers:

```text
10, 20, 30, 40, 50
```

Print the array.

---

### Exercise 2 — Array Properties

Create the following array:

```python
arr = np.array([
    [1, 2, 3],
    [4, 5, 6]
])
```

Print:

* Number of dimensions
* Shape
* Number of elements
* Data type

---

### Exercise 3 — Zeros and Ones

Create:

1. An array containing 10 zeros.
2. A `3 × 4` matrix containing ones.

Print both arrays.

---

### Exercise 4 — Generate a Sequence

Generate all even numbers from `2` to `20` using `np.arange()`.

Expected result:

```text
[ 2  4  6  8 10 12 14 16 18 20]
```

---

### Exercise 5 — Generate Evenly Spaced Values

Generate 11 evenly spaced numbers between `0` and `10` using `np.linspace()`.

Expected result:

```text
[ 0.  1.  2.  3.  4.  5.  6.  7.  8.  9. 10.]
```

---

### Exercise 6 — Indexing

Given:

```python
arr = np.array([5, 10, 15, 20, 25, 30])
```

Print:

* The first element
* The last element
* The third element
* The second-to-last element

---

### Exercise 7 — Slicing

Given:

```python
arr = np.arange(1, 11)
```

Use slicing to obtain:

```text
[3 4 5 6 7]
```

---

### Exercise 8 — Matrix Indexing

Given:

```python
matrix = np.array([
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
])
```

Extract:

* `20`
* `60`
* `70`
* `90`

Then extract the second row.

---

### Exercise 9 — Reshape an Array

Create an array containing numbers from `1` to `12`.

Reshape it into:

```text
3 × 4
```

Expected result:

```text
[[ 1  2  3  4]
 [ 5  6  7  8]
 [ 9 10 11 12]]
```

---

### Exercise 10 — Mathematical Operations

Given:

```python
arr = np.array([2, 4, 6, 8, 10])
```

Calculate:

* Square of every number
* Cube of every number
* Square root of every number
* Number multiplied by `5`

---

### Exercise 11 — Statistics

Given the following test scores:

```python
scores = np.array([75, 82, 91, 68, 88, 95, 73, 84])
```

Calculate:

* Mean
* Median
* Minimum
* Maximum
* Standard deviation
* Variance

---

### Exercise 12 — Filtering

Given:

```python
arr = np.array([12, 5, 18, 3, 25, 7, 30, 10])
```

Use Boolean indexing to find:

1. Numbers greater than `15`
2. Numbers less than `10`
3. Numbers between `10` and `25`

---

### Exercise 13 — Replace Values With `np.where()`

Given:

```python
scores = np.array([45, 72, 88, 39, 95, 60])
```

Use `np.where()` to replace:

* Scores greater than or equal to `50` → `"Pass"`
* Scores below `50` → `"Fail"`

---

### Exercise 14 — Row and Column Operations

Given:

```python
matrix = np.array([
    [10, 20, 30],
    [40, 50, 60],
    [70, 80, 90]
])
```

Calculate:

1. Sum of every column
2. Sum of every row
3. Mean of every column
4. Mean of every row

---

### Exercise 15 — Find Maximum and Minimum Indices

Given:

```python
scores = np.array([72, 85, 91, 68, 95, 77])
```

Use NumPy functions to find:

* The maximum score
* The index of the maximum score
* The minimum score
* The index of the minimum score

---

### Exercise 16 — Unique Values and Sorting

Given:

```python
arr = np.array([5, 3, 8, 3, 1, 5, 8, 2, 1, 9])
```

Find:

1. Unique values
2. Sorted values
3. Number of unique values

---

### Exercise 17 — Matrix Multiplication

Create the matrices:

```python
A = np.array([
    [1, 2],
    [3, 4]
])

B = np.array([
    [5, 6],
    [7, 8]
])
```

Calculate:

1. `A + B`
2. `A - B`
3. Element-wise multiplication `A * B`
4. Matrix multiplication `A @ B`

Explain the difference between `A * B` and `A @ B`.

---

### Exercise 18 — Random Dataset

Generate a NumPy array containing **100 random integers** between `1` and `100`.

Calculate:

* Mean
* Median
* Minimum
* Maximum
* Standard deviation

Then count how many values are greater than `50`.

---

### Exercise 19 — Normalize Data

Given:

```python
data = np.array([10, 20, 30, 40, 50])
```

Perform **Min-Max normalization** using:

```text
x_normalized = (x - min(x)) / (max(x) - min(x))
```

The resulting values should be between `0` and `1`.

---

### Exercise 20 — Mini Data-Science Task

Given:

```python
students = np.array([
    [80, 75, 90],
    [65, 70, 72],
    [95, 92, 88],
    [60, 68, 70],
    [85, 80, 84]
])
```

Each row represents a student and each column represents a subject.

Perform the following tasks:

1. Calculate the average score for each student.
2. Calculate the average score for each subject.
3. Find the student with the highest average.
4. Find the student with the lowest average.
5. Find the highest score in the entire dataset.
6. Find the lowest score in the entire dataset.
7. Count how many scores are greater than or equal to `80`.
8. Convert all scores to normalized values between `0` and `1`.

A possible solution should make extensive use of NumPy operations rather than Python `for` loops.

---

## Learning Path

A practical order for learning NumPy is:

```text
NumPy Basics
    ↓
Creating Arrays
    ↓
Array Properties
    ↓
Indexing & Slicing
    ↓
Reshaping
    ↓
Mathematical Operations
    ↓
Boolean Indexing
    ↓
Aggregation
    ↓
Broadcasting
    ↓
Linear Algebra
    ↓
Data Science / Machine Learning
```

After completing these exercises, the next useful step is to learn how **NumPy and Pandas work together**. NumPy is particularly important for understanding how numerical data is represented and manipulated underneath many data-science and machine-learning workflows.
