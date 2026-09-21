# Seaborn in Python

# Table of Contents

- [Seaborn in Python](#seaborn-in-python)
- [Table of Contents](#table-of-contents)
  - [1. What Is Seaborn?](#1-what-is-seaborn)
  - [2. What Is Seaborn Used For?](#2-what-is-seaborn-used-for)
  - [3. Basic Seaborn Workflow](#3-basic-seaborn-workflow)
    - [Step 1 — Import libraries](#step-1--import-libraries)
    - [Step 2 — Load data](#step-2--load-data)
    - [Step 3 — Create a visualization](#step-3--create-a-visualization)
    - [Step 4 — Display the plot](#step-4--display-the-plot)
  - [4. Common Seaborn Plots](#4-common-seaborn-plots)
    - [4.1 Scatter Plot](#41-scatter-plot)
    - [4.2 Line Plot](#42-line-plot)
    - [4.3 Bar Plot](#43-bar-plot)
    - [4.4 Count Plot](#44-count-plot)
    - [4.5 Histogram](#45-histogram)
    - [4.6 KDE Plot](#46-kde-plot)
    - [4.7 Box Plot](#47-box-plot)
    - [4.8 Violin Plot](#48-violin-plot)
    - [4.9 Heatmap](#49-heatmap)
    - [4.10 Pair Plot](#410-pair-plot)
  - [5. Customizing Seaborn Visualizations](#5-customizing-seaborn-visualizations)
    - [Titles and Labels](#titles-and-labels)
    - [Figure Size](#figure-size)
    - [Rotating Labels](#rotating-labels)
    - [Seaborn Themes](#seaborn-themes)
    - [Color Palettes](#color-palettes)
  - [6. Statistical Visualization with Seaborn](#6-statistical-visualization-with-seaborn)
    - [Regression Plot](#regression-plot)
    - [Regression by Category](#regression-by-category)
    - [Distribution Comparison](#distribution-comparison)
    - [Box Plot for Group Comparison](#box-plot-for-group-comparison)
    - [Correlation Analysis](#correlation-analysis)
  - [7. Seaborn with Pandas](#7-seaborn-with-pandas)
  - [8. Exercises](#8-exercises)
    - [Exercise 1 — Basic Scatter Plot](#exercise-1--basic-scatter-plot)
    - [Exercise 2 — Line Plot](#exercise-2--line-plot)
    - [Exercise 3 — Bar Plot](#exercise-3--bar-plot)
    - [Exercise 4 — Count Plot](#exercise-4--count-plot)
    - [Exercise 5 — Histogram](#exercise-5--histogram)
    - [Exercise 6 — Box Plot](#exercise-6--box-plot)
    - [Exercise 7 — Violin Plot](#exercise-7--violin-plot)
    - [Exercise 8 — Scatter Plot with Hue](#exercise-8--scatter-plot-with-hue)
    - [Exercise 9 — Multiple Distributions](#exercise-9--multiple-distributions)
    - [Exercise 10 — Correlation Heatmap](#exercise-10--correlation-heatmap)
    - [Exercise 11 — Pair Plot](#exercise-11--pair-plot)
    - [Exercise 12 — Pair Plot with Categories](#exercise-12--pair-plot-with-categories)
    - [Exercise 13 — Regression Plot](#exercise-13--regression-plot)
    - [Exercise 14 — Category Comparison](#exercise-14--category-comparison)
    - [Exercise 15 — Faceted Visualization](#exercise-15--faceted-visualization)
    - [Exercise 16 — Customized Visualization](#exercise-16--customized-visualization)
    - [Exercise 17 — Sales Visualization Project](#exercise-17--sales-visualization-project)
    - [Exercise 18 — Titanic Visualization Project](#exercise-18--titanic-visualization-project)
    - [Exercise 19 — Complete EDA Visualization](#exercise-19--complete-eda-visualization)
    - [Exercise 20 — Final Seaborn Project](#exercise-20--final-seaborn-project)
  - [9. Seaborn Cheat Sheet](#9-seaborn-cheat-sheet)
  - [10. Conclusion](#10-conclusion)

## 1. What Is Seaborn?

**Seaborn** is a Python data visualization library built on top of **Matplotlib**. It provides a high-level interface for creating statistical graphics and makes it easier to produce clear and attractive visualizations from structured datasets.

Seaborn works especially well with **pandas DataFrames**.

Install Seaborn:

```bash
pip install seaborn
```

Import it:

```python
import seaborn as sns
import matplotlib.pyplot as plt
```

A common workflow is:

```text
Pandas → Prepare Data → Seaborn → Visualize → Analyze
```

---

## 2. What Is Seaborn Used For?

Seaborn is primarily used for **exploratory data analysis (EDA)** and **statistical data visualization**.

It is useful for visualizing:

* Distributions of numerical data
* Relationships between variables
* Differences between categories
* Correlations
* Trends over time
* Statistical summaries
* Multivariate relationships

For example, given a dataset containing:

```text
age
salary
department
experience
gender
```

Seaborn can help answer questions such as:

* How is salary distributed?
* Is salary related to experience?
* Which department has the highest salary?
* How does salary differ between genders?
* Are age and experience correlated?

---

## 3. Basic Seaborn Workflow

A basic Seaborn visualization usually follows these steps:

### Step 1 — Import libraries

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```

### Step 2 — Load data

```python
df = pd.read_csv("data.csv")
```

### Step 3 — Create a visualization

For example:

```python
sns.scatterplot(
    data=df,
    x="age",
    y="salary"
)
```

### Step 4 — Display the plot

```python
plt.show()
```

A complete example:

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv("employees.csv")

sns.scatterplot(
    data=df,
    x="experience",
    y="salary"
)

plt.title("Experience vs Salary")
plt.xlabel("Years of Experience")
plt.ylabel("Salary")
plt.show()
```

Seaborn functions generally follow this pattern:

```python
sns.plot_function(
    data=df,
    x="column1",
    y="column2",
    hue="category"
)
```

---

## 4. Common Seaborn Plots

### 4.1 Scatter Plot

Used to visualize the relationship between two numerical variables.

```python
sns.scatterplot(
    data=df,
    x="age",
    y="salary"
)
plt.show()
```

Add a categorical variable using `hue`:

```python
sns.scatterplot(
    data=df,
    x="age",
    y="salary",
    hue="department"
)
plt.show()
```

---

### 4.2 Line Plot

Useful for showing trends.

```python
sns.lineplot(
    data=df,
    x="month",
    y="sales"
)
plt.show()
```

Multiple groups:

```python
sns.lineplot(
    data=df,
    x="month",
    y="sales",
    hue="product"
)
plt.show()
```

---

### 4.3 Bar Plot

Useful for comparing categories.

```python
sns.barplot(
    data=df,
    x="department",
    y="salary"
)
plt.show()
```

Seaborn can calculate an aggregate statistic such as the mean when multiple observations belong to the same category.

---

### 4.4 Count Plot

Used to count observations in each category.

```python
sns.countplot(
    data=df,
    x="department"
)
plt.show()
```

With a second categorical variable:

```python
sns.countplot(
    data=df,
    x="department",
    hue="gender"
)
plt.show()
```

---

### 4.5 Histogram

Used to understand the distribution of numerical data.

```python
sns.histplot(
    data=df,
    x="salary"
)
plt.show()
```

Specify the number of bins:

```python
sns.histplot(
    data=df,
    x="salary",
    bins=20
)
plt.show()
```

---

### 4.6 KDE Plot

A KDE plot estimates the probability density of a numerical variable.

```python
sns.kdeplot(
    data=df,
    x="salary"
)
plt.show()
```

You can compare distributions:

```python
sns.kdeplot(
    data=df,
    x="salary",
    hue="department"
)
plt.show()
```

---

### 4.7 Box Plot

Useful for comparing distributions and identifying potential outliers.

```python
sns.boxplot(
    data=df,
    x="department",
    y="salary"
)
plt.show()
```

---

### 4.8 Violin Plot

Combines aspects of a box plot and a density plot.

```python
sns.violinplot(
    data=df,
    x="department",
    y="salary"
)
plt.show()
```

---

### 4.9 Heatmap

Useful for displaying matrices such as correlation matrices.

```python
correlation = df.corr(numeric_only=True)

sns.heatmap(
    correlation,
    annot=True
)

plt.show()
```

---

### 4.10 Pair Plot

Useful for exploring relationships among multiple numerical variables.

```python
sns.pairplot(df)
plt.show()
```

You can color points by a category:

```python
sns.pairplot(
    df,
    hue="species"
)
plt.show()
```

---

## 5. Customizing Seaborn Visualizations

Seaborn provides many options for controlling the appearance of plots.

### Titles and Labels

```python
sns.scatterplot(
    data=df,
    x="age",
    y="salary"
)

plt.title("Age vs Salary")
plt.xlabel("Age")
plt.ylabel("Salary")

plt.show()
```

### Figure Size

```python
plt.figure(figsize=(10, 6))

sns.boxplot(
    data=df,
    x="department",
    y="salary"
)

plt.show()
```

### Rotating Labels

```python
plt.xticks(rotation=45)
```

### Seaborn Themes

You can change the overall plotting style:

```python
sns.set_theme(style="whitegrid")
```

Common styles include:

```python
sns.set_theme(style="darkgrid")
sns.set_theme(style="whitegrid")
sns.set_theme(style="white")
sns.set_theme(style="ticks")
```

### Color Palettes

Seaborn provides built-in palettes:

```python
sns.set_palette("deep")
```

For a specific visualization:

```python
sns.barplot(
    data=df,
    x="department",
    y="salary",
    palette="Set2"
)
```

---

## 6. Statistical Visualization with Seaborn

One of Seaborn's major strengths is statistical visualization.

### Regression Plot

To visualize a relationship together with a regression trend:

```python
sns.regplot(
    data=df,
    x="experience",
    y="salary"
)

plt.show()
```

### Regression by Category

```python
sns.lmplot(
    data=df,
    x="experience",
    y="salary",
    hue="department"
)
```

### Distribution Comparison

```python
sns.histplot(
    data=df,
    x="salary",
    hue="gender",
    kde=True
)
```

### Box Plot for Group Comparison

```python
sns.boxplot(
    data=df,
    x="department",
    y="salary"
)
```

### Correlation Analysis

First calculate correlations:

```python
corr = df.corr(numeric_only=True)
```

Then visualize them:

```python
sns.heatmap(
    corr,
    annot=True,
    fmt=".2f"
)

plt.show()
```

Seaborn therefore works particularly well when visualization is part of an analytical workflow rather than simply producing presentation graphics.

---

## 7. Seaborn with Pandas

Seaborn and pandas are commonly used together.

For example:

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.DataFrame({
    "department": [
        "IT", "IT", "HR", "HR",
        "Finance", "Finance"
    ],
    "salary": [
        4000, 4500, 3000,
        3500, 5000, 5500
    ]
})
```

Calculate average salary:

```python
summary = (
    df.groupby("department")["salary"]
      .mean()
      .reset_index()
)
```

Visualize it:

```python
sns.barplot(
    data=summary,
    x="department",
    y="salary"
)

plt.title("Average Salary by Department")
plt.show()
```

A powerful workflow is therefore:

```text
Pandas
   ↓
Clean / Transform
   ↓
Group / Aggregate
   ↓
Seaborn
   ↓
Visualization
```

---

## 8. Exercises

The exercises progress from basic visualization to complete EDA tasks.

### Exercise 1 — Basic Scatter Plot

Create:

```python
df = pd.DataFrame({
    "age": [20, 22, 25, 28, 30, 32],
    "salary": [2000, 2200, 2500, 3000, 3500, 4000]
})
```

Tasks:

1. Create a scatter plot of `age` vs `salary`.
2. Add a title.
3. Add x-axis and y-axis labels.

---

### Exercise 2 — Line Plot

Create a dataset containing:

```text
month
sales
```

for 12 months.

Tasks:

1. Create a line plot.
2. Add markers to the line.
3. Add a title.
4. Add axis labels.

---

### Exercise 3 — Bar Plot

Given:

```python
df = pd.DataFrame({
    "department": ["IT", "HR", "Finance", "Marketing"],
    "employees": [50, 30, 20, 40]
})
```

Create a bar plot showing the number of employees in each department.

Add:

* Title
* Axis labels
* Rotated x-axis labels if necessary

---

### Exercise 4 — Count Plot

Given:

```python
df = pd.DataFrame({
    "city": [
        "HCMC", "Hanoi", "HCMC",
        "Danang", "Hanoi", "HCMC",
        "Hanoi", "Danang"
    ]
})
```

Tasks:

1. Create a count plot of cities.
2. Determine the most common city.
3. Add a title.

---

### Exercise 5 — Histogram

Generate or create a dataset containing the test scores of 100 students.

Tasks:

1. Create a histogram of scores.
2. Experiment with 5, 10, 20, and 30 bins.
3. Compare how the distribution changes.
4. Add a KDE curve.

Example:

```python
sns.histplot(
    data=df,
    x="score",
    bins=20,
    kde=True
)
```

---

### Exercise 6 — Box Plot

Create:

```python
df = pd.DataFrame({
    "department": [
        "IT", "IT", "IT",
        "HR", "HR", "HR",
        "Finance", "Finance", "Finance"
    ],
    "salary": [
        3500, 4000, 4500,
        2800, 3000, 3200,
        4500, 5000, 5500
    ]
})
```

Create a box plot showing salary distributions by department.

Identify potential differences between the groups.

---

### Exercise 7 — Violin Plot

Using the same employee dataset:

1. Create a violin plot.
2. Compare it with the box plot.
3. Explain what information is visible in the violin plot that is less obvious in the box plot.

---

### Exercise 8 — Scatter Plot with Hue

Create a dataset containing:

```text
age
salary
department
```

Create a scatter plot where:

* x = age
* y = salary
* color = department

Then describe the patterns visible in the plot.

---

### Exercise 9 — Multiple Distributions

Create a dataset containing salaries for employees in:

```text
IT
HR
Finance
Marketing
```

Use:

```python
sns.histplot(
    data=df,
    x="salary",
    hue="department",
    kde=True
)
```

Compare the salary distributions across departments.

---

### Exercise 10 — Correlation Heatmap

Create a DataFrame containing:

```text
age
experience
salary
working_hours
performance
```

Tasks:

1. Calculate the correlation matrix.
2. Create a heatmap.
3. Add correlation values using `annot=True`.
4. Identify strongly correlated variables.

---

### Exercise 11 — Pair Plot

Using a dataset with at least four numerical variables:

```python
sns.pairplot(df)
```

Tasks:

1. Create the pair plot.
2. Identify positive relationships.
3. Identify negative relationships.
4. Identify variables that appear weakly related.

---

### Exercise 12 — Pair Plot with Categories

Using the Iris dataset:

```python
iris = sns.load_dataset("iris")
```

Create:

```python
sns.pairplot(
    iris,
    hue="species"
)
```

Analyze how the species differ based on their numerical features.

---

### Exercise 13 — Regression Plot

Create a dataset containing:

```text
experience
salary
```

Tasks:

1. Create a scatter plot.
2. Create a regression plot using `regplot()`.
3. Describe the relationship between experience and salary.

Example:

```python
sns.regplot(
    data=df,
    x="experience",
    y="salary"
)
```

---

### Exercise 14 — Category Comparison

Given:

```python
df = pd.DataFrame({
    "department": [
        "IT", "IT", "IT",
        "HR", "HR", "HR",
        "Finance", "Finance", "Finance"
    ],
    "gender": [
        "Male", "Female", "Male",
        "Female", "Female", "Male",
        "Male", "Male", "Female"
    ],
    "salary": [
        4000, 4500, 4200,
        3000, 3200, 3100,
        5000, 5500, 4800
    ]
})
```

Create a visualization comparing salary across:

```text
department
gender
```

Try using:

```python
sns.boxplot()
```

and:

```python
sns.barplot()
```

Compare the two visualizations.

---

### Exercise 15 — Faceted Visualization

Create a dataset containing:

```text
month
sales
product
region
```

Use Seaborn's faceting capabilities to create separate plots for different regions.

For example, explore:

```python
sns.relplot(
    data=df,
    x="month",
    y="sales",
    col="region",
    hue="product",
    kind="line"
)
```

---

### Exercise 16 — Customized Visualization

Create a visualization of your choice and customize:

* Figure size
* Title
* Axis labels
* Tick rotation
* Grid
* Legend
* Theme
* Color palette

The goal is to make the visualization easy to read rather than simply using default settings.

---

### Exercise 17 — Sales Visualization Project

Create a sales DataFrame containing:

```text
date
product
category
quantity
price
region
```

Create:

1. A line plot of sales over time.
2. A bar plot of revenue by category.
3. A count plot of orders by region.
4. A box plot of revenue by category.
5. A heatmap of numerical correlations.

---

### Exercise 18 — Titanic Visualization Project

Load the Titanic dataset:

```python
titanic = sns.load_dataset("titanic")
```

Investigate:

1. Passenger survival counts.
2. Survival by gender.
3. Survival by passenger class.
4. Age distribution.
5. Fare distribution.
6. Age vs fare.
7. Survival vs age.
8. Survival vs gender and class.

Use at least **six different Seaborn plots**.

---

### Exercise 19 — Complete EDA Visualization

Choose a real dataset.

Perform a visualization-based EDA containing:

```text
1. Univariate analysis
2. Bivariate analysis
3. Multivariate analysis
4. Distribution analysis
5. Category comparison
6. Correlation analysis
```

Use at least:

```text
histplot
countplot
scatterplot
barplot
boxplot
heatmap
```

Write a short explanation below each visualization describing what the plot reveals.

---

### Exercise 20 — Final Seaborn Project

Choose a real dataset such as:

* Titanic
* Iris
* Wine Quality
* Netflix
* Customer churn
* Sales data
* Your own dataset

Perform a complete EDA using **Pandas + Seaborn**.

Your project should contain:

```text
Data Loading
     ↓
Data Cleaning
     ↓
Exploratory Analysis
     ↓
Statistical Summaries
     ↓
Visualization
     ↓
Insights
```

Create at least **10 meaningful visualizations**.

Your visualizations should include several different plot types, such as:

```python
sns.histplot()
sns.countplot()
sns.scatterplot()
sns.lineplot()
sns.barplot()
sns.boxplot()
sns.violinplot()
sns.kdeplot()
sns.heatmap()
sns.pairplot()
```

For every visualization, answer:

1. What does the plot show?
2. Which variables are being compared?
3. What pattern do you observe?
4. Are there unusual values or potential outliers?
5. What conclusion can reasonably be drawn from the visualization?

---

## 9. Seaborn Cheat Sheet

| Purpose                  | Function            |
| ------------------------ | ------------------- |
| Scatter plot             | `sns.scatterplot()` |
| Line plot                | `sns.lineplot()`    |
| Bar plot                 | `sns.barplot()`     |
| Count plot               | `sns.countplot()`   |
| Histogram                | `sns.histplot()`    |
| KDE                      | `sns.kdeplot()`     |
| Box plot                 | `sns.boxplot()`     |
| Violin plot              | `sns.violinplot()`  |
| Heatmap                  | `sns.heatmap()`     |
| Pair plot                | `sns.pairplot()`    |
| Regression plot          | `sns.regplot()`     |
| Regression by categories | `sns.lmplot()`      |
| Relational plots         | `sns.relplot()`     |
| Theme                    | `sns.set_theme()`   |
| Color palette            | `sns.set_palette()` |

A typical Seaborn call looks like:

```python
sns.scatterplot(
    data=df,
    x="feature_1",
    y="feature_2",
    hue="category"
)
```

---

## 10. Conclusion

Seaborn is particularly useful when you need to **understand data visually**.

The most important concepts to learn are:

```text
DataFrame
   ↓
Seaborn
   ↓
Distribution
   ↓
Relationship
   ↓
Comparison
   ↓
Correlation
   ↓
Insight
```

For practical data science, learn Seaborn together with **Pandas**:

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```

Use Pandas for **loading, cleaning, transforming, and aggregating data**, then use Seaborn to **visualize patterns and relationships** in that data.
