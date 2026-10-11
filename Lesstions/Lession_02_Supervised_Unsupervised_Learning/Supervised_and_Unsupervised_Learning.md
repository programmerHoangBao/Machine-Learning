# Supervised Learning and Unsupervised Learning

This document introduces two common groups of machine learning methods: **Supervised Learning** and **Unsupervised Learning**. It covers their definitions, how they work, commonly used algorithms, examples, evaluation methods, and a comparison table.

## 1. Overview of Machine Learning

**Machine Learning** is a branch of artificial intelligence in which computers learn patterns and rules from data in order to make predictions, classify items, or discover data structures.

Two basic groups of machine learning are:

- **Supervised Learning:** The training data contains labels or known target outcomes.
- **Unsupervised Learning:** The training data has no provided target labels; the model searches for hidden structures or patterns in the data.

---

## 2. Supervised Learning

### 2.1. Definition

**Supervised Learning** is a method of training a model using data for which the correct answers are already known. Each data sample usually contains:

- **Features (X):** Input information used to make a prediction.
- **Label/Target (y):** The correct result that the model needs to learn to predict.

The goal is to learn a mapping function from inputs to outputs:

\[
\hat{y} = f(X)
\]

Here, \(X\) is the input data, \(f\) is the trained model, and \(\hat{y}\) is the predicted result.

### 2.2. Examples

| Task | Features (X) | Label/Target (y) |
|---|---|---|
| House price prediction | Area, number of rooms, location | House price |
| Email spam detection | Email content, sender, keywords | Spam / Not Spam |
| Customer churn prediction | Usage frequency, duration of use, service history | Churn / No churn |
| Exam score prediction | Study time, number of sessions attended | Exam score |

### 2.3. Two Main Types of Problems

#### A. Classification

The model predicts a **label belonging to a predefined category or class**.

Examples:
- Classifying emails as `Spam` or `Not Spam`.
- Classifying images as `Cat`, `Dog`, or `Bird`.
- Predicting whether a customer is likely to stop using a service.

Common algorithms include:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- k-Nearest Neighbors (KNN)
- Naive Bayes
- Neural Networks

Common evaluation metrics include:

- **Accuracy:** The proportion of correctly predicted samples out of all samples.
- **Precision:** Of the samples predicted as positive, how many actually belong to the positive class.
- **Recall:** Of the samples that actually belong to the positive class, how many the model identifies.
- **F1-score:** The harmonic mean of Precision and Recall.
- **Confusion Matrix:** A table comparing actual labels with predicted labels.

Accuracy alone should not be relied on when the classes are imbalanced. Precision, Recall, and F1-score may provide more useful information.

#### B. Regression

The model predicts a **continuous numerical value**.

Examples:
- Predicting house prices.
- Predicting next month's revenue.
- Estimating tomorrow's temperature.

Common algorithms include:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- Support Vector Regression (SVR)
- Gradient Boosting Regressor
- Neural Networks

Common evaluation metrics include:

- **MAE (Mean Absolute Error):** The average absolute error.
- **MSE (Mean Squared Error):** The average squared error.
- **RMSE (Root Mean Squared Error):** The square root of MSE; it has the same unit as the target variable.
- **R² (Coefficient of Determination):** Indicates how much of the variation in the data the model explains compared with the usual reference baseline.

### 2.4. Basic Workflow

1. Collect labeled data.
2. Clean the data and handle missing values and outliers when necessary.
3. Select the features and identify the target.
4. Split the data into training and test sets; a validation set may also be included.
5. Preprocess the data and train the model on the training set.
6. Evaluate the model using metrics appropriate for the task.
7. Tune the model and its hyperparameters if necessary.
8. Use the model to make predictions on new data.

**Note:** Preprocessing steps such as scaling or feature selection should be learned from the training set and then applied to the validation/test sets to avoid data leakage.

### 2.5. Python Example: Classification

The following example uses the Iris dataset included in `scikit-learn` to classify flower species. The features are sepal and petal measurements; the labels are the flower species.

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, classification_report

# Load labeled data
iris = load_iris()
X, y = iris.data, iris.target

# Split the data: 80% train, 20% test
X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.2,
    random_state=42,
    stratify=y
)

# Pipeline: scale the data, then train Logistic Regression
model = make_pipeline(
    StandardScaler(),
    LogisticRegression(max_iter=1000)
)
model.fit(X_train, y_train)

# Make predictions and evaluate
predictions = model.predict(X_test)
print("Accuracy:", accuracy_score(y_test, predictions))
print(classification_report(y_test, predictions, target_names=iris.target_names))
```

Install the library if it is not already installed:

```bash
pip install scikit-learn
```

---

## 3. Unsupervised Learning

### 3.1. Definition

**Unsupervised Learning** is a method of training a model on data **without provided target labels**. The model discovers structures, groups, relationships, or useful representations in the data.

The data usually contains only features \(X\), without a target \(y\) for the model to learn to predict directly.

### 3.2. Examples

- Grouping customers according to purchasing behavior.
- Grouping articles with similar content.
- Detecting unusual transactions.
- Reducing data dimensionality for visualization or to support another model.
- Finding products that are frequently purchased together.

### 3.3. Main Types of Problems

#### A. Clustering

The goal is to group data points with similar characteristics into the same cluster. Cluster labels are not provided in advance; the algorithm creates groups according to its own criteria.

Example: grouping customers based on the number of purchases, amount spent, and frequency of visits.

Common algorithms include:

- **K-Means:** Divides data into \(k\) clusters based on distances to cluster centers; the number of clusters \(k\) must be chosen in advance.
- **DBSCAN:** Finds clusters based on density and can identify noise points; it is useful when clusters do not have simple spherical shapes.
- **Hierarchical Clustering:** Builds a hierarchical structure of clusters.
- **Gaussian Mixture Model (GMM):** Models data as a mixture of probability distributions.

Evaluation methods include:

- **Silhouette Score:** Considers how close a point is to its own cluster compared with other clusters; a higher value generally indicates better-separated clusters.
- **Davies–Bouldin Index:** A lower value generally indicates more compact and better-separated clusters.
- **Inertia (for K-Means):** The sum of squared distances from data points to their cluster centers. It usually decreases as the number of clusters increases, so it should not be used alone to choose \(k\).
- **Domain evaluation:** Check whether the clusters are meaningful and useful in practice.

Without ground-truth labels, evaluating clustering is often more difficult than evaluating classification.

#### B. Dimensionality Reduction

The goal is to represent data using fewer features while trying to preserve important information.

Applications:
- Visualizing high-dimensional data.
- Reducing noise or computational cost.
- Creating a more compact representation for subsequent analysis.

Common methods include:

- **PCA (Principal Component Analysis):** Finds linear components that retain as much variance as possible.
- **t-SNE:** Often used to visualize neighborhood structure in high-dimensional data.
- **UMAP:** A dimensionality-reduction method commonly used to visualize complex data.

Note: Coordinates produced by dimensionality reduction—especially by t-SNE and UMAP—should not automatically be interpreted as accurately representing distances or the global structure of the original data.

#### C. Association Rule Learning

The goal is to find items or events that frequently occur together.

Example: sales data shows that customers who buy bread often also buy milk. This is a statistical association in the data; it does not necessarily prove that buying one item causes the purchase of the other.

Common algorithms:

- Apriori
- FP-Growth

Key concepts:

- **Support:** The proportion of transactions that contain an itemset.
- **Confidence:** The proportion of transactions containing the left-hand side that also contain the right-hand side.
- **Lift:** Compares co-occurrence with the expected level if the two sides were independent; a lift greater than 1 indicates a positive association according to this measure.

#### D. Anomaly Detection

The goal is to find data points that differ significantly from most of the data. In practice, anomaly detection may be treated as an unsupervised, semi-supervised, or supervised problem, depending on how the data and model are constructed.

Common methods include:

- Isolation Forest
- Local Outlier Factor (LOF)
- One-Class SVM

Applications include detecting suspicious transactions, equipment faults, and unusual activity in a system.

### 3.4. Basic Workflow

1. Collect data without target labels.
2. Clean the data and handle missing values.
3. Select appropriate features; consider scaling when using distance-based algorithms.
4. Choose a method and train the model.
5. Analyze the results using appropriate metrics, visualizations, and domain knowledge.
6. Tune parameters and check whether the results are stable and meaningful.

### 3.5. Python Example: Clustering with K-Means

This example uses the Iris dataset but **deliberately does not use the flower-species labels** for training. K-Means creates three clusters based on the features; it is not given the correct flower species as answers.

```python
from sklearn.datasets import load_iris
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score

iris = load_iris()
X = iris.data  # Use features only; do not use iris.target

# Scale the data once
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Train K-Means on the scaled data
model = KMeans(n_clusters=3, random_state=42, n_init=10)
cluster_labels = model.fit_predict(X_scaled)

print("Number of clusters created:", len(set(cluster_labels)))
print("Silhouette Score:", silhouette_score(X_scaled, cluster_labels))
```

In this example, `cluster_labels` are the cluster labels created by the algorithm. The numbers `0`, `1`, and `2` are cluster identifiers; they do not correspond to fixed flower-species names.

> Note: The example above illustrates a basic workflow. In a real project, if you need to evaluate the model on new data, fit the preprocessing step on the training set and then use that same fitted transformer to transform the validation/test sets to avoid data leakage.

---

## 4. Comparing Supervised and Unsupervised Learning

| Criterion | Supervised Learning | Unsupervised Learning |
|---|---|---|
| Training data | Has target labels `y` | No target labels `y` are provided |
| Goal | Learn to predict a label or value | Discover structures, groups, or relationships |
| Typical output | Predicted class or numerical value | Clusters, reduced-dimensional components, association rules, anomaly scores |
| Common tasks | Classification, Regression | Clustering, Dimensionality Reduction, Association Rules |
| Example | Predict whether an email is spam | Automatically group emails with similar content |
| Evaluation | Compare predictions with ground-truth labels using appropriate metrics | Use intrinsic metrics, visual inspection, and domain evaluation |
| Common challenges | Requires sufficiently good labeled data; risks include overfitting and data leakage | It is difficult to know whether results are correct without labels; results may be hard to interpret |
| Example algorithms | Logistic Regression, Random Forest, Linear Regression | K-Means, DBSCAN, PCA, Apriori |

### A Quick Way to Remember

- **Supervised:** Learn from examples with answers — “What result corresponds to this input?”
- **Unsupervised:** Learn from data without provided answers — “What groups or structures exist in this data?”

---

## 5. When Should You Use Each Method?

### Choose Supervised Learning when:

- You have historical data with reliable labels or outcomes.
- You have a clear prediction goal, such as price, score, likelihood of churn, or transaction type.
- You can measure prediction quality by comparing predictions with the actual answers.

### Choose Unsupervised Learning when:

- Labels are unavailable or labeling would take too much time or cost too much.
- You want to discover previously unknown groups in the data.
- You want to understand data structure, find relationships, or detect unusual cases.

The two methods are not mutually exclusive. For example, you can use clustering to discover customer groups first, then assign labels or build a supervised model to predict the group for new customers.

---

## 6. Related Concepts

- **Training set:** The dataset used to train a model.
- **Validation set:** The dataset used to select a model or tune hyperparameters.
- **Test set:** The dataset used for final evaluation on data that has not been used during model selection.
- **Feature engineering:** Creating or transforming features so that a model can learn more effectively.
- **Overfitting:** When a model fits the training data too closely and performs poorly on new data.
- **Underfitting:** When a model has not learned enough of the important patterns in the data.
- **Data leakage:** Information from outside the permitted scope (such as test data) enters the training or model-selection process, making evaluation results less objective.
- **Semi-supervised Learning:** Combining a small amount of labeled data with a larger amount of unlabeled data.
- **Reinforcement Learning:** An agent learns how to act by interacting with an environment and receiving reward/penalty signals; this is a learning paradigm different from the two groups above.

---

## 7. Conclusion

**Supervised Learning** is suitable when you need to predict a defined outcome and have labeled data for learning. **Unsupervised Learning** is useful when you want to discover structures or hidden patterns in unlabeled data.

When building a model, choose the algorithm, preprocessing approach, and evaluation metric according to the real-world objective. No single algorithm is always the best for every dataset.

## 8. References

- [Scikit-learn — Supervised learning](https://scikit-learn.org/stable/supervised_learning.html)
- [Scikit-learn — Unsupervised learning](https://scikit-learn.org/stable/unsupervised_learning.html)
- [Scikit-learn — Model evaluation](https://scikit-learn.org/stable/modules/model_evaluation.html)
