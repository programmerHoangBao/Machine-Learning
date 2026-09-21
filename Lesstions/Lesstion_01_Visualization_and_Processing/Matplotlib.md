# Matplotlib in Python

## Table of Contents

- [Matplotlib in Python](#matplotlib-in-python)
  - [Table of Contents](#table-of-contents)
  - [1. What Is Matplotlib?](#1-what-is-matplotlib)
  - [2. What Is Matplotlib Used For?](#2-what-is-matplotlib-used-for)
    - [2.1 Exploring Data](#21-exploring-data)
    - [2.2 Comparing Categories](#22-comparing-categories)
    - [2.3 Understanding Distributions](#23-understanding-distributions)
    - [2.4 Analyzing Relationships](#24-analyzing-relationships)
    - [2.5 Presenting Results](#25-presenting-results)
  - [3. Installing and Using Matplotlib](#3-installing-and-using-matplotlib)
    - [3.1 Installation](#31-installation)
    - [3.2 Basic Import](#32-basic-import)
    - [3.3 Basic Plotting Structure](#33-basic-plotting-structure)
  - [4. Common Chart Types](#4-common-chart-types)
    - [4.1 Line Chart](#41-line-chart)
    - [4.2 Bar Chart](#42-bar-chart)
    - [4.3 Horizontal Bar Chart](#43-horizontal-bar-chart)
    - [4.4 Scatter Plot](#44-scatter-plot)
    - [4.5 Histogram](#45-histogram)
    - [4.6 Pie Chart](#46-pie-chart)
    - [4.7 Box Plot](#47-box-plot)
    - [4.8 Area Chart](#48-area-chart)
  - [5. Customizing Charts](#5-customizing-charts)
    - [5.1 Add a Title](#51-add-a-title)
    - [5.2 Add Axis Labels](#52-add-axis-labels)
    - [5.3 Add a Legend](#53-add-a-legend)
    - [5.4 Add a Grid](#54-add-a-grid)
    - [5.5 Set Axis Limits](#55-set-axis-limits)
    - [5.6 Customize Line Style](#56-customize-line-style)
    - [5.7 Rotate Tick Labels](#57-rotate-tick-labels)
    - [5.8 Add Text](#58-add-text)
  - [6. Figures, Axes, and Subplots](#6-figures-axes-and-subplots)
    - [6.1 Figure and Axes](#61-figure-and-axes)
    - [6.2 Multiple Subplots](#62-multiple-subplots)
    - [6.3 `tight_layout()`](#63-tight_layout)
    - [6.4 Save a Figure](#64-save-a-figure)
  - [7. Matplotlib With NumPy and Pandas](#7-matplotlib-with-numpy-and-pandas)
    - [7.1 Matplotlib + NumPy](#71-matplotlib--numpy)
    - [7.2 Matplotlib + Pandas](#72-matplotlib--pandas)
    - [7.3 Typical Data Visualization Workflow](#73-typical-data-visualization-workflow)
  - [8. Exercises](#8-exercises)
    - [Exercise 1 — Basic Line Chart](#exercise-1--basic-line-chart)
    - [Exercise 2 — Customize a Line Chart](#exercise-2--customize-a-line-chart)
    - [Exercise 3 — Multiple Lines](#exercise-3--multiple-lines)
    - [Exercise 4 — Bar Chart](#exercise-4--bar-chart)
    - [Exercise 5 — Horizontal Bar Chart](#exercise-5--horizontal-bar-chart)
    - [Exercise 6 — Scatter Plot](#exercise-6--scatter-plot)
    - [Exercise 7 — Histogram](#exercise-7--histogram)
    - [Exercise 8 — Pie Chart](#exercise-8--pie-chart)
    - [Exercise 9 — Box Plot](#exercise-9--box-plot)
    - [Exercise 10 — Multiple Subplots](#exercise-10--multiple-subplots)
    - [Exercise 11 — Sine and Cosine](#exercise-11--sine-and-cosine)
    - [Exercise 12 — Customize Axis Limits](#exercise-12--customize-axis-limits)
    - [Exercise 13 — Annotate a Maximum](#exercise-13--annotate-a-maximum)
    - [Exercise 14 — Monthly Revenue](#exercise-14--monthly-revenue)
    - [Exercise 15 — Compare Two Classes](#exercise-15--compare-two-classes)
    - [Exercise 16 — Random Data Visualization](#exercise-16--random-data-visualization)
    - [Exercise 17 — Correlation Visualization](#exercise-17--correlation-visualization)
    - [Exercise 18 — Create a Dashboard](#exercise-18--create-a-dashboard)
    - [Exercise 19 — Visualize a Pandas DataFrame](#exercise-19--visualize-a-pandas-dataframe)
    - [Exercise 20 — Mini Data Visualization Project](#exercise-20--mini-data-visualization-project)
    - [Suggested Project Structure](#suggested-project-structure)
  - [Learning Path](#learning-path)

---

## 1. What Is Matplotlib?

**Matplotlib** is a Python library for **data visualization**.

It can be used to create:

* Line charts
* Bar charts
* Histograms
* Scatter plots
* Pie charts
* Box plots
* Area charts
* Heatmaps
* Subplots
* Custom statistical visualizations

The main plotting module is commonly imported as:

```python
import matplotlib.pyplot as plt
```

The alias `plt` is the conventional way to access `matplotlib.pyplot`.

A simple example:

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.plot(x, y)
plt.show()
```

This creates a basic line chart.

---

## 2. What Is Matplotlib Used For?

Matplotlib is mainly used to **turn numerical or categorical data into visual information**.

### 2.1 Exploring Data

Visualization makes it easier to identify:

* Trends
* Patterns
* Outliers
* Distributions
* Relationships
* Differences between groups

For example, a line chart can show how sales change over time:

```python
import matplotlib.pyplot as plt

months = ["Jan", "Feb", "Mar", "Apr", "May"]
sales = [120, 150, 140, 180, 210]

plt.plot(months, sales)
plt.show()
```

### 2.2 Comparing Categories

Bar charts are useful for comparing different categories:

```python
products = ["A", "B", "C", "D"]
sales = [100, 150, 80, 120]

plt.bar(products, sales)
plt.show()
```

### 2.3 Understanding Distributions

Histograms help visualize how numerical values are distributed:

```python
import numpy as np
import matplotlib.pyplot as plt

data = np.random.normal(50, 10, 1000)

plt.hist(data, bins=20)
plt.show()
```

### 2.4 Analyzing Relationships

Scatter plots can show the relationship between two variables:

```python
height = [150, 155, 160, 165, 170, 175, 180]
weight = [50, 53, 57, 60, 65, 70, 75]

plt.scatter(height, weight)
plt.show()
```

### 2.5 Presenting Results

Matplotlib is also useful for:

* Data-analysis reports
* Machine-learning experiments
* Scientific papers
* Business dashboards
* Academic assignments
* Exploratory Data Analysis (EDA)

---

## 3. Installing and Using Matplotlib

### 3.1 Installation

Install Matplotlib using `pip`:

```bash
pip install matplotlib
```

If you are using a virtual environment, activate it first.

You can check the installation:

```python
import matplotlib

print(matplotlib.__version__)
```

### 3.2 Basic Import

The most common import is:

```python
import matplotlib.pyplot as plt
```

For numerical data, Matplotlib is often used together with NumPy:

```python
import numpy as np
import matplotlib.pyplot as plt
```

### 3.3 Basic Plotting Structure

A typical Matplotlib program looks like:

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [10, 20, 15, 25, 30]

plt.plot(x, y)

plt.xlabel("X")
plt.ylabel("Y")
plt.title("My Chart")

plt.show()
```

The general workflow is:

```text
Prepare data
    ↓
Create figure / axes
    ↓
Plot the data
    ↓
Add labels and title
    ↓
Customize the chart
    ↓
Display or save the figure
```

---

## 4. Common Chart Types

### 4.1 Line Chart

Use `plt.plot()` for continuous data or trends.

```python
x = [1, 2, 3, 4, 5]
y = [10, 15, 12, 20, 25]

plt.plot(x, y)
plt.show()
```

Add markers:

```python
plt.plot(x, y, marker="o")
plt.show()
```

### 4.2 Bar Chart

Use `plt.bar()` for categorical comparisons.

```python
categories = ["A", "B", "C", "D"]
values = [20, 35, 25, 40]

plt.bar(categories, values)
plt.show()
```

### 4.3 Horizontal Bar Chart

Use `plt.barh()`:

```python
categories = ["A", "B", "C", "D"]
values = [20, 35, 25, 40]

plt.barh(categories, values)
plt.show()
```

### 4.4 Scatter Plot

Use `plt.scatter()`:

```python
x = [1, 2, 3, 4, 5]
y = [2, 4, 3, 7, 8]

plt.scatter(x, y)
plt.show()
```

### 4.5 Histogram

Use `plt.hist()`:

```python
data = [10, 12, 12, 15, 18, 18, 20, 21, 22, 25]

plt.hist(data, bins=5)
plt.show()
```

A histogram groups numerical values into intervals called **bins**.

### 4.6 Pie Chart

Use `plt.pie()`:

```python
labels = ["Python", "Java", "C++", "JavaScript"]
values = [40, 25, 20, 15]

plt.pie(values, labels=labels)
plt.show()
```

### 4.7 Box Plot

Box plots are useful for understanding distributions and identifying potential outliers.

```python
scores = [55, 60, 62, 65, 68, 70, 72, 75, 78, 95]

plt.boxplot(scores)
plt.show()
```

### 4.8 Area Chart

An area chart can be created using `fill_between()`:

```python
x = [1, 2, 3, 4, 5]
y = [10, 20, 15, 30, 35]

plt.fill_between(x, y)
plt.show()
```

---

## 5. Customizing Charts

A major strength of Matplotlib is its ability to customize charts.

### 5.1 Add a Title

```python
plt.title("Monthly Sales")
```

### 5.2 Add Axis Labels

```python
plt.xlabel("Month")
plt.ylabel("Sales")
```

### 5.3 Add a Legend

When plotting multiple datasets:

```python
x = [1, 2, 3, 4, 5]

y1 = [10, 20, 15, 25, 30]
y2 = [5, 15, 20, 18, 35]

plt.plot(x, y1, label="Product A")
plt.plot(x, y2, label="Product B")

plt.legend()
plt.show()
```

### 5.4 Add a Grid

```python
plt.grid(True)
```

### 5.5 Set Axis Limits

```python
plt.xlim(0, 10)
plt.ylim(0, 50)
```

### 5.6 Customize Line Style

```python
plt.plot(
    x,
    y1,
    linestyle="--",
    marker="o",
    linewidth=2
)
```

Common line styles include:

```text
"-"   Solid
"--"  Dashed
":"   Dotted
"-."  Dash-dot
```

### 5.7 Rotate Tick Labels

```python
plt.xticks(rotation=45)
```

This is useful when category names are long.

### 5.8 Add Text

You can annotate specific points:

```python
plt.text(3, 15, "Important Point")
```

For more precise annotation:

```python
plt.annotate(
    "Maximum",
    xy=(5, 30),
    xytext=(4, 35),
    arrowprops={"arrowstyle": "->"}
)
```

---

## 6. Figures, Axes, and Subplots

For simple charts, `plt.plot()` is convenient. For more complex visualizations, Matplotlib's **object-oriented interface** is often easier to organize.

### 6.1 Figure and Axes

Create a figure and axes:

```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots()

x = [1, 2, 3, 4, 5]
y = [10, 20, 15, 25, 30]

ax.plot(x, y)

ax.set_title("Sales")
ax.set_xlabel("Month")
ax.set_ylabel("Revenue")

plt.show()
```

Here:

* `Figure` is the overall canvas.
* `Axes` represents an individual plotting area.

### 6.2 Multiple Subplots

Create multiple charts in one figure:

```python
import matplotlib.pyplot as plt

fig, axes = plt.subplots(2, 2)

axes[0, 0].plot([1, 2, 3], [2, 4, 6])
axes[0, 1].bar(["A", "B", "C"], [10, 20, 15])
axes[1, 0].scatter([1, 2, 3], [5, 3, 7])
axes[1, 1].hist([1, 2, 2, 3, 3, 3, 4])

plt.tight_layout()
plt.show()
```

The resulting figure contains four plotting areas.

### 6.3 `tight_layout()`

Use:

```python
plt.tight_layout()
```

to automatically adjust spacing between subplots and reduce overlapping labels.

### 6.4 Save a Figure

Save the chart to a file:

```python
plt.savefig("sales.png")
```

For example:

```python
fig, ax = plt.subplots()

ax.plot([1, 2, 3], [10, 20, 15])
ax.set_title("Sales")

fig.savefig("sales.png", dpi=300, bbox_inches="tight")
```

The figure can be saved in formats such as:

```text
PNG
JPG
SVG
PDF
```

---

## 7. Matplotlib With NumPy and Pandas

Matplotlib is frequently used together with **NumPy** and **Pandas**.

### 7.1 Matplotlib + NumPy

NumPy can generate numerical data while Matplotlib visualizes it.

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.plot(x, y)
plt.title("Sine Wave")
plt.xlabel("x")
plt.ylabel("sin(x)")
plt.grid(True)

plt.show()
```

### 7.2 Matplotlib + Pandas

Suppose you have a DataFrame:

```python
import pandas as pd
import matplotlib.pyplot as plt

data = {
    "Month": ["Jan", "Feb", "Mar", "Apr", "May"],
    "Sales": [120, 150, 140, 180, 210]
}

df = pd.DataFrame(data)
```

You can visualize it:

```python
plt.plot(df["Month"], df["Sales"], marker="o")

plt.title("Monthly Sales")
plt.xlabel("Month")
plt.ylabel("Sales")

plt.show()
```

### 7.3 Typical Data Visualization Workflow

A common workflow in data science is:

```text
Raw Data
   ↓
Pandas
   ↓
Data Cleaning
   ↓
NumPy
   ↓
Numerical Processing
   ↓
Matplotlib
   ↓
Visualization
   ↓
Analysis / Reporting
```

For example:

```python
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("sales.csv")

monthly_sales = df.groupby("month")["sales"].sum()

monthly_sales.plot(kind="line")

plt.title("Monthly Sales")
plt.xlabel("Month")
plt.ylabel("Sales")

plt.show()
```

---

## 8. Exercises

The exercises below progress from basic plotting to practical data-visualization tasks.

### Exercise 1 — Basic Line Chart

Create two lists:

```python
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
```

Create a line chart showing `y` as a function of `x`.

Add:

* Chart title
* X-axis label
* Y-axis label

---

### Exercise 2 — Customize a Line Chart

Using the data:

```python
x = [1, 2, 3, 4, 5]
y = [10, 15, 13, 20, 25]
```

Create a line chart with:

* Circular markers
* Dashed line
* Line width of `2`
* Grid
* Title
* Axis labels

---

### Exercise 3 — Multiple Lines

Create a chart comparing two products:

```python
months = ["Jan", "Feb", "Mar", "Apr", "May"]

product_a = [100, 120, 140, 160, 180]
product_b = [90, 130, 125, 170, 200]
```

Plot both products on the same chart.

Add:

* Legend
* Title
* Axis labels
* Grid

---

### Exercise 4 — Bar Chart

Create a bar chart using:

```python
products = ["Laptop", "Phone", "Tablet", "Monitor"]
sales = [120, 250, 100, 80]
```

Display the sales of each product.

---

### Exercise 5 — Horizontal Bar Chart

Using:

```python
languages = ["Python", "Java", "C++", "JavaScript"]
developers = [450, 300, 200, 350]
```

Create a horizontal bar chart.

Add a title and axis labels.

---

### Exercise 6 — Scatter Plot

Given:

```python
hours = [1, 2, 3, 4, 5, 6, 7, 8]
scores = [50, 55, 60, 65, 70, 75, 80, 90]
```

Create a scatter plot showing the relationship between study hours and exam scores.

Add:

* Title
* X-axis label
* Y-axis label
* Grid

---

### Exercise 7 — Histogram

Create a histogram from:

```python
scores = [
    55, 60, 62, 65, 67, 70, 72,
    72, 75, 78, 80, 82, 85, 88,
    90, 92, 95
]
```

Use different numbers of bins and observe how the visualization changes.

---

### Exercise 8 — Pie Chart

Create a pie chart showing programming-language preferences:

```python
languages = ["Python", "Java", "C++", "JavaScript"]
users = [40, 25, 15, 20]
```

Add:

* Labels
* Percentages
* Title

---

### Exercise 9 — Box Plot

Given:

```python
scores = [45, 50, 52, 55, 57, 60, 62, 65, 68, 70, 95]
```

Create a box plot.

Determine which value might be an outlier based on the visualization.

---

### Exercise 10 — Multiple Subplots

Create a `2 × 2` figure containing:

1. Line chart
2. Bar chart
3. Scatter plot
4. Histogram

Use `plt.subplots()`.

Give each subplot a title.

---

### Exercise 11 — Sine and Cosine

Use NumPy:

```python
import numpy as np

x = np.linspace(0, 2 * np.pi, 100)

sin_y = np.sin(x)
cos_y = np.cos(x)
```

Plot both functions on the same chart.

Add:

* Legend
* Title
* Axis labels
* Grid

---

### Exercise 12 — Customize Axis Limits

Create a line chart for:

```python
x = np.arange(0, 20)
y = x ** 2
```

Set:

```text
x-axis: 0 to 20
y-axis: 0 to 400
```

Add appropriate labels.

---

### Exercise 13 — Annotate a Maximum

Given:

```python
x = [1, 2, 3, 4, 5]
y = [10, 25, 18, 40, 30]
```

Create a line chart and annotate the point with the highest value.

The annotation should indicate:

```text
Maximum
```

and point to the corresponding data point.

---

### Exercise 14 — Monthly Revenue

Create a visualization using:

```python
months = [
    "Jan", "Feb", "Mar", "Apr",
    "May", "Jun", "Jul", "Aug"
]

revenue = [
    12000, 15000, 14000, 18000,
    21000, 19500, 23000, 25000
]
```

Create a professional-looking line chart containing:

* Title
* Axis labels
* Markers
* Grid
* Legend

---

### Exercise 15 — Compare Two Classes

Suppose two classes have the following scores:

```python
class_a = [70, 75, 80, 85, 90]
class_b = [65, 72, 78, 82, 88]
```

Create a visualization comparing the two classes.

Use a suitable chart type and explain why you selected it.

---

### Exercise 16 — Random Data Visualization

Use NumPy to generate:

```text
500 random values from a normal distribution
```

Then create a histogram.

Calculate and display:

* Mean
* Standard deviation

You may use `np.random.normal()`.

---

### Exercise 17 — Correlation Visualization

Generate two numerical datasets:

```python
x = np.arange(1, 101)
y = 2 * x + np.random.normal(0, 20, 100)
```

Create a scatter plot.

Add a line representing the general trend of the data.

---

### Exercise 18 — Create a Dashboard

Create a figure containing four visualizations for a fictional company:

```text
1. Monthly Revenue      → Line Chart
2. Product Sales        → Bar Chart
3. Customer Ages        → Histogram
4. Revenue vs Customers → Scatter Plot
```

Use `plt.subplots()`.

Make sure the four charts have:

* Appropriate titles
* Axis labels
* Good spacing
* Readable tick labels

---

### Exercise 19 — Visualize a Pandas DataFrame

Create the following DataFrame:

```python
import pandas as pd

data = {
    "Month": ["Jan", "Feb", "Mar", "Apr", "May", "Jun"],
    "Sales": [100, 130, 120, 160, 180, 200],
    "Expenses": [80, 90, 100, 110, 120, 125]
}

df = pd.DataFrame(data)
```

Create a chart comparing:

```text
Sales vs Expenses
```

Then answer:

1. Which month has the highest sales?
2. Which month has the highest difference between sales and expenses?
3. What is the average sales value?

---

### Exercise 20 — Mini Data Visualization Project

Create a fictional student dataset:

```python
students = [
    "Alice", "Bob", "Charlie",
    "David", "Emma", "Frank",
    "Grace", "Henry"
]

math = [85, 70, 92, 65, 88, 76, 95, 80]
english = [90, 75, 89, 70, 94, 78, 91, 82]
science = [88, 72, 95, 68, 90, 80, 93, 85]
```

Build a mini visualization report containing at least **4 charts**:

1. Bar chart showing each student's average score.
2. Line chart comparing Math, English, and Science.
3. Histogram showing the distribution of all scores.
4. Scatter plot showing the relationship between Math and Science.

Then calculate:

* Average score for each student
* Average score for each subject
* Highest individual score
* Lowest individual score
* Student with the highest average

Finally, save the visualization as an image:

```python
plt.savefig("student_analysis.png", dpi=300)
```

### Suggested Project Structure

```text
matplotlib-project/
│
├── data/
│   └── students.csv
│
├── notebooks/
│   └── analysis.ipynb
│
├── charts/
│   └── student_analysis.png
│
└── main.py
```

---

## Learning Path

A practical way to learn Matplotlib is:

```text
Matplotlib Basics
        ↓
Line Charts
        ↓
Bar Charts
        ↓
Scatter Plots
        ↓
Histograms
        ↓
Pie / Box Plots
        ↓
Chart Customization
        ↓
Subplots
        ↓
Figure & Axes API
        ↓
NumPy + Matplotlib
        ↓
Pandas + Matplotlib
        ↓
Exploratory Data Analysis
        ↓
Data Visualization Projects
```

The most important concepts to master first are:

```text
plt.plot()
plt.bar()
plt.scatter()
plt.hist()
plt.pie()
plt.boxplot()
plt.subplots()
plt.xlabel()
plt.ylabel()
plt.title()
plt.legend()
plt.grid()
plt.savefig()
```

Once these concepts are comfortable, Matplotlib can be used effectively for **Exploratory Data Analysis (EDA), machine-learning experiments, scientific computing, and data-analysis projects**.
