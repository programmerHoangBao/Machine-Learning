# Chart Types in Data Visualization

Data Visualization uses graphical representations to make data easier to understand, explore, and communicate.

Different chart types answer different analytical questions. Choosing the right chart depends primarily on:

* The type of data
* The analytical question
* The relationship we want to investigate
* The target audience

A useful principle is:

> **Choose the chart based on the question you want to answer, not based on the chart you want to draw.**

---

# Table of Contents

1. [Bar Chart](#1-bar-chart)
2. [Grouped Bar Chart](#2-grouped-bar-chart)
3. [Stacked Bar Chart](#3-stacked-bar-chart)
4. [Line Chart](#4-line-chart)
5. [Area Chart](#5-area-chart)
6. [Histogram](#6-histogram)
7. [Box Plot](#7-box-plot)
8. [Violin Plot](#8-violin-plot)
9. [Scatter Plot](#9-scatter-plot)
10. [Bubble Chart](#10-bubble-chart)
11. [Heatmap](#11-heatmap)
12. [Pie / Donut Chart](#12-pie--donut-chart)
13. [Count Plot](#13-count-plot)
14. [Pair Plot](#14-pair-plot)
15. [Area / Density Plot](#15-area--density-plot)
16. [Chart Selection Guide](#chart-selection-guide)
17. [Summary](#summary)

---

# 1. Bar Chart

## What is it?

A **Bar Chart** represents values for different categories using rectangular bars.

The length or height of each bar represents the magnitude of a value.

```text
Sales
  │
  │           █
  │           █
  │     █     █
  │     █     █       █
  │  █  █     █       █
  └────────────────────────
      A  B     C       D
```

## Best for

* Comparing categories
* Ranking values
* Showing frequencies
* Comparing aggregated metrics

## Example questions

* Which product has the highest sales?
* Which department has the most employees?
* Which country has the highest revenue?

## Typical data structure

```text
Category      Value
-------------------
Product A      120
Product B      200
Product C      150
Product D       80
```

## Python

```python
import matplotlib.pyplot as plt

plt.bar(df["category"], df["sales"])
plt.xlabel("Category")
plt.ylabel("Sales")
plt.title("Sales by Category")
plt.show()
```

## Important considerations

Bar charts are usually most effective when:

* Categories are clearly labeled
* The number of categories is manageable
* Bars are ordered when ranking is important

---

# 2. Grouped Bar Chart

## What is it?

A **Grouped Bar Chart** places multiple bars next to each other for each category.

It is useful for comparing multiple groups across the same categories.

```text
Sales
  │
  │       █ █
  │       █ █       █ █
  │   █ █ █ █   █ █ █ █
  └────────────────────────
      A       B       C
```

## Best for

Comparing:

* Multiple products
* Multiple regions
* Different years
* Different customer groups

## Example

```text
Category     2025     2026
---------------------------
Books         100      150
Electronics   200      220
Clothing      120      180
```

## Python

```python
import seaborn as sns

sns.barplot(
    data=df,
    x="category",
    y="sales",
    hue="year"
)
```

## Important considerations

Grouped bar charts become difficult to read when there are too many groups or categories.

---

# 3. Stacked Bar Chart

## What is it?

A **Stacked Bar Chart** divides each bar into multiple segments.

Each segment represents a component of the total.

```text
Revenue

A   █████████████
    ├───┤───────┤
    X     Y

B   █████████████████
    ├──────┤───────┤
     X       Y
```

## Best for

Understanding:

* Total values
* Composition
* Contribution of categories

## Example questions

* What contributes to total revenue?
* How is the customer base divided by segment?
* How does product composition change across regions?

## Typical data

```text
Region    Product_A    Product_B    Product_C
---------------------------------------------
North        100          50           30
South         80          70           20
West         120          60           40
```

## Important considerations

Stacked charts are good for showing total and composition, but comparing segments that do not share a common baseline can be difficult.

---

# 4. Line Chart

## What is it?

A **Line Chart** connects data points in sequence, usually across time.

```text
Sales
  │
  │              ●
  │          ●
  │       ●
  │    ●
  │ ●
  └──────────────────── Time
```

## Best for

* Time-series data
* Trends
* Continuous measurements
* Changes over time

## Example questions

* How did revenue change over time?
* Is the number of users increasing?
* What is the monthly trend in sales?

## Typical data

```text
Month     Sales
----------------
Jan       100
Feb       120
Mar       140
Apr       135
May       160
```

## Python

```python
import matplotlib.pyplot as plt

plt.plot(df["month"], df["sales"])
plt.xlabel("Month")
plt.ylabel("Sales")
plt.title("Monthly Sales")
plt.show()
```

## Important considerations

Line charts imply an ordered sequence. They are especially appropriate when the x-axis represents time or another naturally ordered continuous variable.

---

# 5. Area Chart

## What is it?

An **Area Chart** is similar to a line chart, but the area below the line is filled.

```text
Value
  │
  │        ●
  │      ●██
  │    ●████
  │  ●██████
  │●████████
  └──────────────── Time
```

## Best for

* Showing trends
* Emphasizing magnitude
* Showing cumulative behavior

## Example questions

* How has total traffic changed?
* How does the total number of users evolve over time?
* How much revenue was generated during a period?

## Important considerations

Area charts can make overlapping series difficult to read.

For multiple time-series categories, a stacked area chart can be useful when the goal is to show composition over time.

---

# 6. Histogram

## What is it?

A **Histogram** shows the distribution of a numerical variable by dividing values into intervals called **bins**.

```text
Frequency

  │       ███
  │      █████
  │    ████████
  │  ██████████
  │ ███████████
  └──────────────────
     10 20 30 40 50
```

## Best for

Understanding:

* Distribution
* Central tendency
* Spread
* Skewness
* Potential outliers
* Multiple modes

## Example questions

* What is the distribution of age?
* Are salaries normally distributed?
* How long do users spend on the platform?

## Python

```python
import seaborn as sns

sns.histplot(data=df, x="age", bins=20, kde=True)
```

## Important considerations

The choice of bin size can significantly affect the appearance of the distribution.

Too few bins:

```text
Too coarse → important patterns may disappear
```

Too many bins:

```text
Too fine → the distribution may look noisy
```

---

# 7. Box Plot

## What is it?

A **Box Plot** summarizes the distribution of numerical data using:

* Minimum
* First quartile (Q1)
* Median
* Third quartile (Q3)
* Maximum
* Potential outliers

```text
        ●
        │
        │
     ┌──┴──┐
     │     │
─────┤ ─── ├────
     │     │
     └─────┘
        │
```

The box represents the interquartile range:

```text
IQR = Q3 - Q1
```

## Best for

* Comparing distributions
* Detecting outliers
* Understanding spread
* Comparing groups

## Example questions

* Which department has higher salaries?
* Are there outliers in transaction amounts?
* Which customer group has the largest variation?

## Python

```python
import seaborn as sns

sns.boxplot(
    data=df,
    x="department",
    y="salary"
)
```

## Important considerations

Box plots summarize distributions efficiently, but they hide some details about distribution shape.

---

# 8. Violin Plot

## What is it?

A **Violin Plot** combines characteristics of a box plot with a kernel density estimate.

The width of the violin represents the estimated density of observations.

```text
Density

     ██
    ████
   ██████
  ████████
   ██████
    ████
     ██
```

## Best for

* Comparing distributions between groups
* Detecting multiple modes
* Seeing distribution shape

## Example questions

* How are salaries distributed across departments?
* Do two customer groups have different distributions?
* Are there multiple clusters in a variable?

## Python

```python
import seaborn as sns

sns.violinplot(
    data=df,
    x="department",
    y="salary"
)
```

## Box Plot vs Violin Plot

| Feature            | Box Plot         | Violin Plot   |
| ------------------ | ---------------- | ------------- |
| Median             | Yes              | Usually       |
| Quartiles          | Yes              | Usually       |
| Outliers           | Easy to identify | Less explicit |
| Distribution shape | Limited          | Detailed      |
| Density            | No               | Yes           |

---

# 9. Scatter Plot

## What is it?

A **Scatter Plot** displays individual observations as points according to two numerical variables.

```text
Y
│
│          ●
│       ●
│    ●
│  ●
│ ●
└──────────────── X
```

## Best for

Understanding:

* Relationships
* Correlation
* Clusters
* Outliers
* Non-linear patterns

## Example questions

* Is income related to age?
* Does experience correlate with salary?
* Is price related to demand?

## Python

```python
import seaborn as sns

sns.scatterplot(
    data=df,
    x="experience",
    y="salary"
)
```

## Important considerations

A scatter plot can reveal association, but:

> **Correlation does not imply causation.**

Additional statistical analysis may be required to understand the relationship.

---

# 10. Bubble Chart

## What is it?

A **Bubble Chart** extends a scatter plot by using the size of each point to represent a third numerical variable.

It can also use shape or color to represent additional dimensions.

```text
Y
│
│               ●●
│          ●
│    ●
│ ●●
└──────────────────── X
       Size → Z
```

## Example

```text
X = GDP
Y = Life Expectancy
Bubble Size = Population
```

## Best for

* Multivariate analysis
* Comparing entities using multiple variables
* Showing magnitude and relationship simultaneously

## Python

```python
import plotly.express as px

fig = px.scatter(
    df,
    x="gdp",
    y="life_expectancy",
    size="population"
)

fig.show()
```

## Important considerations

Large bubbles can visually dominate the chart, so size encoding should be used carefully.

---

# 11. Heatmap

## What is it?

A **Heatmap** represents numerical values using color intensity.

```text
        A    B    C    D
A      1.0  0.7  0.2  0.1
B      0.7  1.0  0.5  0.2
C      0.2  0.5  1.0  0.8
D      0.1  0.2  0.8  1.0
```

Conceptually:

```text
Low ─────────────── High
 ░   ▒   ▓   █
```

## Best for

* Correlation matrices
* Pattern detection
* Large tables of values
* Confusion matrices
* Feature relationships

## Example

```python
import seaborn as sns
import matplotlib.pyplot as plt

corr = df.select_dtypes("number").corr()

sns.heatmap(
    corr,
    annot=True,
    cmap="coolwarm"
)

plt.show()
```

## Example questions

* Which features are highly correlated?
* Which cells have the highest values?
* What errors are common in a classification model?

---

# 12. Pie / Donut Chart

## What is it?

A **Pie Chart** shows how a whole is divided into categories.

```text
       ______
    .-'      '-.
  .'    A       '.
 /               \
|      B          |
 \         C     /
  '.           .'
    '-._____.-'
```

## Best for

* Showing simple part-to-whole relationships
* A small number of categories

## Example

```text
Device

Mobile      60%
Desktop     30%
Tablet      10%
```

## Important considerations

Pie charts become difficult to interpret when there are many categories or when values are similar.

For precise comparisons, a bar chart is often easier to read.

## Python

```python
import matplotlib.pyplot as plt

plt.pie(
    df["value"],
    labels=df["category"],
    autopct="%1.1f%%"
)

plt.show()
```

---

# 13. Count Plot

## What is it?

A **Count Plot** displays how many observations belong to each category.

It is essentially a bar chart of category frequencies.

```text
Frequency

  │
  │ ███
  │ ███
  │ ███       ██
  │ ███   █   ██
  └────────────────
     A    B    C
```

## Best for

* Categorical EDA
* Class distribution
* Frequency analysis
* Checking imbalance

## Example questions

* How many samples belong to each class?
* How many users are in each country?
* Is the classification dataset imbalanced?

## Python

```python
import seaborn as sns

sns.countplot(
    data=df,
    x="target"
)
```

## Classification example

```text
Class 0   █████████████████████████
Class 1   ██████
```

This immediately indicates potential class imbalance.

---

# 14. Pair Plot

## What is it?

A **Pair Plot** shows relationships between multiple numerical variables simultaneously.

Conceptually:

```text
          Age    Income   Salary
Age       Hist   Scatter  Scatter
Income    Scatter Hist    Scatter
Salary    Scatter Scatter Hist
```

## Best for

* Initial EDA
* Multivariate analysis
* Finding correlations
* Identifying clusters
* Detecting possible relationships

## Python

```python
import seaborn as sns

sns.pairplot(
    df[["age", "income", "salary"]]
)
```

It can also be useful for understanding how feature distributions differ across classes.

```python
sns.pairplot(
    df,
    vars=["age", "income", "salary"],
    hue="target"
)
```

## Important considerations

Pair plots can become expensive and visually cluttered when the number of features or observations is large.

---

# 15. Density Plot

## What is it?

A **Density Plot**, often implemented using Kernel Density Estimation (KDE), represents a smoothed estimate of a numerical distribution.

```text
Density
  │
  │        ___
  │      /     \
  │    /         \
  │___/           \____
  └──────────────────── X
```

## Best for

* Comparing distributions
* Understanding distribution shape
* Detecting multiple modes
* Comparing groups

## Example questions

* Do two populations have similar distributions?
* Where are observations concentrated?
* Is the distribution bimodal?

## Python

```python
import seaborn as sns

sns.kdeplot(
    data=df,
    x="salary",
    fill=True
)
```

## Important considerations

KDE is an estimated distribution rather than the raw observations. The smoothing bandwidth affects the result.

---

# Chart Selection Guide

Choosing a chart can be simplified by first asking:

> **What do I want to understand?**

| Analytical Goal                    | Recommended Charts |
| ---------------------------------- | ------------------ |
| Compare categories                 | Bar Chart          |
| Compare multiple groups            | Grouped Bar Chart  |
| Show composition                   | Stacked Bar Chart  |
| Show trend over time               | Line Chart         |
| Show magnitude over time           | Area Chart         |
| Understand numerical distribution  | Histogram          |
| Detect outliers                    | Box Plot           |
| Compare distribution shapes        | Violin Plot        |
| Explore two numerical variables    | Scatter Plot       |
| Explore three numerical dimensions | Bubble Chart       |
| Explore correlations               | Heatmap            |
| Show simple part-to-whole          | Pie / Donut Chart  |
| Count categorical observations     | Count Plot         |
| Explore many variables             | Pair Plot          |
| Compare smoothed distributions     | Density Plot       |

---

# Choosing a Chart Based on Data Type

## Numerical + Numerical

Use:

```text
Scatter Plot
Bubble Chart
Heatmap
```

Example:

```text
Age ↔ Income
```

---

## Categorical + Numerical

Use:

```text
Bar Chart
Box Plot
Violin Plot
```

Example:

```text
Department ↔ Salary
```

---

## Categorical + Categorical

Use:

```text
Grouped Bar Chart
Stacked Bar Chart
Heatmap
```

Example:

```text
Gender ↔ Churn
```

---

## Numerical + Time

Use:

```text
Line Chart
Area Chart
```

Example:

```text
Date ↔ Revenue
```

---

## Single Numerical Variable

Use:

```text
Histogram
Box Plot
Density Plot
Violin Plot
```

---

## Single Categorical Variable

Use:

```text
Count Plot
Bar Chart
Pie / Donut Chart
```

---

# Data Visualization in EDA

In a typical machine learning project, these charts can be organized as an EDA workflow:

```text
                    Dataset
                       │
                       ▼
              Understand Schema
                       │
                       ▼
               Data Quality Check
                       │
          ┌────────────┴────────────┐
          │                         │
          ▼                         ▼
      Numerical                 Categorical
          │                         │
          ▼                         ▼
 Histogram / Boxplot           Count Plot / Bar
          │                         │
          └────────────┬────────────┘
                       ▼
                Relationship Analysis
                       │
             ┌─────────┼─────────┐
             ▼         ▼         ▼
         Scatter     Heatmap   Pair Plot
             │
             ▼
          Target Analysis
             │
             ▼
        Patterns & Insights
```

---

# Practical Example: Classification Dataset

Suppose we have:

```text
Age
Income
Gender
Tenure
MonthlyCharges
ContractType
Churn
```

A practical visualization strategy would be:

### Step 1 — Understand categorical variables

```text
Count Plot
    ↓
Gender
ContractType
Churn
```

### Step 2 — Understand numerical distributions

```text
Histogram
    ↓
Age
Income
MonthlyCharges
Tenure
```

### Step 3 — Detect outliers

```text
Box Plot
    ↓
Income
MonthlyCharges
Tenure
```

### Step 4 — Explore relationships

```text
Scatter Plot
    ↓
Age ↔ Income
Tenure ↔ MonthlyCharges
```

### Step 5 — Compare features against target

```text
Box Plot
    ↓
MonthlyCharges ↔ Churn

Bar Chart
    ↓
ContractType ↔ Churn
```

### Step 6 — Explore correlations

```text
Heatmap
    ↓
Numerical Features
```

This approach is generally more useful than producing every possible chart without an analytical question.

---

# Common Mistakes in Data Visualization

## 1. Choosing a chart without a question

Bad workflow:

```text
"I need a chart."
       ↓
"Let's draw a pie chart."
```

Better workflow:

```text
"What question am I trying to answer?"
       ↓
"What type of relationship does the data have?"
       ↓
"Which chart communicates that relationship clearly?"
```

---

## 2. Creating too many charts

More charts do not necessarily provide more insight.

A useful visualization should have a purpose.

---

## 3. Ignoring data quality

Before visualization, check:

```text
Missing Values
Duplicates
Invalid Values
Outliers
Incorrect Data Types
Inconsistent Categories
```

Otherwise, the chart may accurately visualize **bad data**.

---

## 4. Using misleading scales

The axis scale can strongly influence interpretation.

Always check:

* Axis limits
* Units
* Intervals
* Transformations
* Log scales

---

## 5. Using inappropriate chart types

For example:

```text
Time Series → Pie Chart
Distribution → Pie Chart
Correlation → Pie Chart
```

The chart should match the structure of the question.

---

# Recommended Python Visualization Stack

For a typical Data Science / AI project:

```text
Python
│
├── Pandas
│   └── Data manipulation
│
├── Matplotlib
│   └── Fundamental plotting
│
├── Seaborn
│   └── Statistical visualization / EDA
│
├── Plotly
│   └── Interactive visualization
│
└── Jupyter Notebook
    └── Exploration and experimentation
```

A common workflow is:

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

df = pd.read_csv("data.csv")
```

Then:

```text
Pandas
   ↓
Data Inspection
   ↓
Seaborn / Matplotlib
   ↓
EDA
   ↓
Plotly
   ↓
Interactive Analysis / Dashboard
```

---

# Summary

The 15 commonly used chart types covered in this README are:

```text
01. Bar Chart
02. Grouped Bar Chart
03. Stacked Bar Chart
04. Line Chart
05. Area Chart
06. Histogram
07. Box Plot
08. Violin Plot
09. Scatter Plot
10. Bubble Chart
11. Heatmap
12. Pie / Donut Chart
13. Count Plot
14. Pair Plot
15. Density Plot
```

The most important concept is not memorizing 15 chart types.

Instead, understand the relationship between:

```text
Data Type
    +
Analytical Question
    +
Visualization
    =
Insight
```

A strong Data Visualization workflow should help answer questions such as:

```text
What does the data look like?
        ↓
How is the data distributed?
        ↓
Are there outliers or anomalies?
        ↓
How are variables related?
        ↓
How do different groups differ?
        ↓
How does the data change over time?
        ↓
What patterns can we discover?
        ↓
What insights should we investigate further?
```

> **Good Data Visualization does not simply make data look attractive. It makes patterns, relationships, and problems easier to see and understand.**
