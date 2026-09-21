# Pandas in Python

## Table of Contents

1. [What Is Pandas?](#1-what-is-pandas)
2. [What Is Pandas Used For?](#2-what-is-pandas-used-for)
3. [Series and DataFrame](#3-series-and-dataframe)
4. [How to Load and Inspect Data](#4-how-to-load-and-inspect-data)
5. [Selecting, Filtering, and Sorting](#5-selecting-filtering-and-sorting)
6. [Cleaning and Transforming Data](#6-cleaning-and-transforming-data)
7. [Grouping and Aggregation](#7-grouping-and-aggregation)
8. [Merging and Reshaping Data](#8-merging-and-reshaping-data)
9. [Exporting Data](#9-exporting-data)
10. [Exercises](#10-exercises)
11. [Conclusion](#conclusion)

## 1. What Is Pandas?

**pandas** is an open-source Python library for **data manipulation, data cleaning, and data analysis**.

It is especially useful for working with structured data such as:

* CSV files
* Excel files
* JSON data
* SQL query results
* Parquet files

Install pandas:

```bash
pip install pandas
```

Import it:

```python
import pandas as pd
```

---

## 2. What Is Pandas Used For?

Pandas is commonly used to:

* Load datasets
* Explore and inspect data
* Select and filter rows and columns
* Clean missing and duplicate data
* Transform data
* Group and aggregate data
* Merge multiple datasets
* Reshape data
* Export processed data

A typical workflow is:

```text
Load → Inspect → Clean → Transform → Analyze → Export
```

---

## 3. Series and DataFrame

Pandas has two fundamental data structures.

### Series

A `Series` is a one-dimensional labeled data structure.

```python
ages = pd.Series([20, 25, 30])

print(ages)
```

### DataFrame

A `DataFrame` is a two-dimensional table containing rows and columns.

```python
data = {
    "name": ["Alice", "Bob", "Charlie"],
    "age": [20, 25, 30],
    "score": [85, 90, 78]
}

df = pd.DataFrame(data)

print(df)
```

Output:

```text
      name  age  score
0    Alice   20     85
1      Bob   25     90
2  Charlie   30     78
```

---

## 4. How to Load and Inspect Data

### Read a CSV file

```python
df = pd.read_csv("data.csv")
```

### View data

```python
df.head()
df.tail()
```

### Check dimensions

```python
df.shape
```

### Check column names

```python
df.columns
```

### Check data types

```python
df.dtypes
```

### Get dataset information

```python
df.info()
```

### Get statistics

```python
df.describe()
```

These operations are usually the first steps when exploring a new dataset.

---

## 5. Selecting, Filtering, and Sorting

### Select a column

```python
df["name"]
```

### Select multiple columns

```python
df[["name", "score"]]
```

### Select rows with `iloc`

```python
df.iloc[0:3]
```

### Select rows with `loc`

```python
df.loc[df["score"] > 80]
```

### Filter with multiple conditions

```python
df[(df["age"] > 20) & (df["score"] > 80)]
```

### Sort data

```python
df.sort_values("score", ascending=False)
```

---

## 6. Cleaning and Transforming Data

### Check missing values

```python
df.isna().sum()
```

### Fill missing values

```python
df["age"] = df["age"].fillna(df["age"].median())
```

### Remove rows with missing values

```python
df = df.dropna()
```

### Remove duplicates

```python
df = df.drop_duplicates()
```

### Create a new column

```python
df["passed"] = df["score"] >= 50
```

### Rename a column

```python
df = df.rename(columns={"score": "exam_score"})
```

---

## 7. Grouping and Aggregation

`groupby()` is useful for analyzing data by categories.

Example:

```python
df.groupby("department")["salary"].mean()
```

Calculate multiple statistics:

```python
df.groupby("department")["salary"].agg(
    ["count", "mean", "min", "max"]
)
```

Count unique values:

```python
df["city"].value_counts()
```

Find unique values:

```python
df["city"].unique()
```

Count unique values:

```python
df["city"].nunique()
```

---

## 8. Merging and Reshaping Data

### Merge DataFrames

```python
result = pd.merge(
    employees,
    salaries,
    on="employee_id",
    how="inner"
)
```

Common join types:

```text
inner
left
right
outer
```

### Concatenate DataFrames

```python
result = pd.concat([df1, df2], ignore_index=True)
```

### Pivot table

```python
pivot = pd.pivot_table(
    df,
    values="salary",
    index="department",
    columns="gender",
    aggfunc="mean"
)
```

---

## 9. Exporting Data

After cleaning or analyzing data, you can save the result.

### CSV

```python
df.to_csv("output.csv", index=False)
```

### Excel

```python
df.to_excel("output.xlsx", index=False)
```

### JSON

```python
df.to_json("output.json")
```

### Parquet

```python
df.to_parquet("output.parquet")
```

---

## 10. Exercises

The exercises progress from **beginner to intermediate/advanced**.

### Exercise 1 — Create a DataFrame

Create a DataFrame containing:

```text
name, age, major, gpa
```

for five students.

Then display:

* The DataFrame
* Its shape
* Its column names

---

### Exercise 2 — Inspect a DataFrame

Given:

```python
df = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie", "David", "Emma"],
    "age": [20, 21, 22, 20, 21],
    "score": [85, 92, 78, 90, 88]
})
```

Use pandas to find:

* First 3 rows
* Last 2 rows
* Shape
* Data types
* Basic statistics

---

### Exercise 3 — Select Columns

Using the DataFrame above:

1. Select `name`.
2. Select `name` and `score`.
3. Select the first three rows.
4. Select rows using `iloc`.
5. Select rows using `loc`.

---

### Exercise 4 — Filter Data

Find students who:

1. Have a score greater than 85.
2. Have an age greater than or equal to 21.
3. Have a score between 80 and 90.
4. Are at least 21 years old and have a score above 85.

---

### Exercise 5 — Create New Columns

Given:

```python
df = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie", "David"],
    "math": [80, 90, 70, 85],
    "physics": [85, 88, 75, 90],
    "chemistry": [90, 92, 80, 87]
})
```

Create:

```text
total
average
passed
```

where:

```text
total = math + physics + chemistry
average = total / 3
passed = average >= 80
```

---

### Exercise 6 — Handle Missing Values

Given:

```python
df = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie", "David"],
    "age": [25, None, 30, None],
    "salary": [3000, 4000, None, 3500],
    "city": ["Hanoi", "HCMC", None, "Danang"]
})
```

Tasks:

1. Count missing values.
2. Fill missing ages with the median.
3. Fill missing salaries with the mean.
4. Fill missing cities with `"Unknown"`.
5. Verify that the missing values have been handled.

---

### Exercise 7 — Sort and Analyze

Given an employee DataFrame:

```python
df = pd.DataFrame({
    "name": ["Alice", "Bob", "Charlie", "David", "Emma"],
    "salary": [3000, 4200, 2800, 5000, 3500],
    "age": [25, 30, 28, 35, 27]
})
```

Tasks:

1. Sort by salary ascending.
2. Sort by salary descending.
3. Find the employee with the highest salary.
4. Find the average salary.
5. Find the median salary.

---

### Exercise 8 — GroupBy

Given:

```python
df = pd.DataFrame({
    "employee": ["A", "B", "C", "D", "E", "F"],
    "department": [
        "IT", "IT", "HR", "HR", "Finance", "Finance"
    ],
    "salary": [3000, 3500, 2800, 3200, 4000, 4500]
})
```

Calculate:

1. Average salary by department.
2. Maximum salary by department.
3. Minimum salary by department.
4. Employee count by department.
5. Total salary by department.

---

### Exercise 9 — Merge DataFrames

Given:

```python
employees = pd.DataFrame({
    "employee_id": [1, 2, 3, 4],
    "name": ["Alice", "Bob", "Charlie", "David"]
})

salary = pd.DataFrame({
    "employee_id": [1, 2, 3, 5],
    "salary": [3000, 3500, 4000, 4500]
})
```

Perform:

1. Inner join
2. Left join
3. Right join
4. Outer join

Then explain the difference between the results.

---

### Exercise 10 — String Processing

Given:

```python
df = pd.DataFrame({
    "name": [" Alice ", "BOB", " Charlie", "david ", " EMMA "],
    "email": [
        "alice@gmail.com",
        "bob@yahoo.com",
        "charlie@gmail.com",
        "david@gmail.com",
        "emma@yahoo.com"
    ]
})
```

Tasks:

1. Remove whitespace from names.
2. Convert names to lowercase.
3. Create uppercase names.
4. Extract the email domain.
5. Find users with Gmail addresses.

---

### Exercise 11 — Date Processing

Given:

```python
df = pd.DataFrame({
    "order_id": [1, 2, 3, 4, 5],
    "order_date": [
        "2026-01-15",
        "2026-02-20",
        "2026-03-10",
        "2026-03-25",
        "2026-04-05"
    ],
    "amount": [100, 250, 180, 300, 220]
})
```

Tasks:

1. Convert `order_date` to datetime.
2. Extract year, month, and day.
3. Find orders in March.
4. Calculate total sales.

---

### Exercise 12 — Value Counts

Given a DataFrame containing a `city` column:

```python
df["city"].value_counts()
```

Use pandas to determine:

1. The number of users per city.
2. The most common city.
3. The number of unique cities.
4. The percentage of users from each city.

---

### Exercise 13 — Multiple Aggregations

Using the employee dataset, create a summary containing:

```text
department
employee_count
average_salary
minimum_salary
maximum_salary
total_salary
```

Use `groupby()` and `agg()`.

---

### Exercise 14 — Remove Duplicates

Given:

```python
df = pd.DataFrame({
    "id": [1, 2, 3, 3, 4, 5, 5],
    "name": [
        "Alice", "Bob", "Charlie",
        "Charlie", "David", "Emma", "Emma"
    ]
})
```

Tasks:

1. Count duplicates.
2. Display duplicated rows.
3. Remove duplicates.
4. Reset the index.

---

### Exercise 15 — Advanced Filtering

Given columns:

```text
name
department
salary
age
```

Find employees who:

1. Work in IT.
2. Earn more than 4,000.
3. Are younger than 30.
4. Work in IT and earn more than 4,000.
5. Work in either IT or HR.

Try using:

```python
isin()
```

and:

```python
between()
```

---

### Exercise 16 — Concatenate DataFrames

Given two quarterly sales DataFrames:

```python
q1 = pd.DataFrame({
    "name": ["Alice", "Bob"],
    "sales": [1000, 1200]
})

q2 = pd.DataFrame({
    "name": ["Charlie", "David"],
    "sales": [900, 1500]
})
```

Tasks:

1. Concatenate them.
2. Reset the index.
3. Calculate total sales.
4. Find the highest-selling employee.

---

### Exercise 17 — Pivot Table

Given:

```python
df = pd.DataFrame({
    "department": ["IT", "IT", "HR", "HR", "Finance", "Finance"],
    "gender": ["Male", "Female", "Male", "Female", "Male", "Female"],
    "salary": [4000, 4200, 3000, 3200, 4500, 4300]
})
```

Create a pivot table showing:

```text
department × gender → average salary
```

---

### Exercise 18 — Data Cleaning Project

Clean the following types of problems in a customer dataset:

* Duplicate records
* Extra whitespace
* Inconsistent capitalization
* Missing names
* Missing ages
* Missing emails
* Inconsistent city names

Your final DataFrame should be clean and ready for analysis.

---

### Exercise 19 — Sales Analysis

Create a dataset containing:

```text
order_id
order_date
product
category
quantity
price
city
```

Create:

```python
df["revenue"] = df["quantity"] * df["price"]
```

Then calculate:

1. Total revenue.
2. Average revenue.
3. Total quantity sold.
4. Revenue by product.
5. Revenue by category.
6. Revenue by city.
7. Top 3 products by revenue.
8. Monthly revenue.

---

### Exercise 20 — Mini EDA Project

Choose a real dataset such as Titanic, Wine Quality, Netflix, or a dataset of your own.

Perform a complete EDA using pandas.

Your analysis should include:

```text
1. Load the dataset
2. Inspect the dataset
3. Analyze data types
4. Analyze missing values
5. Analyze duplicates
6. Analyze categorical variables
7. Analyze numerical variables
8. Perform groupby analysis
9. Create new features
10. Export the cleaned dataset
```

Try to answer at least **10 meaningful questions** about the dataset using pandas.

---

## Conclusion

The most important pandas concepts to master are:

```python
pd.DataFrame()
pd.read_csv()

df.head()
df.info()
df.describe()
df.shape

df["column"]
df.loc[]
df.iloc[]

df[condition]

df.isna()
df.fillna()
df.dropna()
df.drop_duplicates()

df.sort_values()

df.groupby()
df.agg()
df.value_counts()

pd.merge()
pd.concat()
pd.pivot_table()

df.to_csv()
```

A strong way to learn pandas is to practice these operations repeatedly on real datasets rather than memorizing every function.
