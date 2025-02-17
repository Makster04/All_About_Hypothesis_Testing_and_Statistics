## Introduction to Machine Learning (ML)

Machine Learning (ML) is a branch of artificial intelligence (AI) that focuses on developing algorithms that enable computers to learn patterns from data and make decisions without explicit programming. ML can be broadly categorized into three main types:

### Supervised Learning

- The model learns from labeled data (input-output pairs).
- **Example:** Predicting house prices based on features like size, location, and number of rooms.
- **Common Algorithms:**
  - **Linear Regression**: Predicts continuous values.
  - **Logistic Regression**: Used for binary classification.
  - **Decision Trees**: A flowchart-like model for classification and regression.
  - **Random Forest:** An ensemble of decision trees for better performance.
  - **Support Vector Machines (SVM)**: Used for classification by finding the best hyperplane.
  - **Neural Networks**: Powers deep learning models.
  - **Gradient Boosting (XGBoost, LightGBM)** – Powerful for structured data classification/regression.

### Unsupervised Learning

- The model learns patterns and structures from unlabeled data.
- **Example:** Customer segmentation in marketing.
- **Common Algorithms:**
  - **K-Means Clustering:** Groups data into clusters without labels.
  - **Hierarchical Clustering:**  Groups data into nested clusters using similarity-based tree structures.
  - **Principal Component Analysis (PCA):**

### Reinforcement Learning (RL)

- The model learns by interacting with an environment and receiving rewards or penalties.
- **Example:** AlphaGo (a system that learns to play Go).
- **Common Algorithms:**
  - **Q-Learning**: Reinforcement learning algorithm using value iteration for optimal policy selection.
  - **Deep Q-Networks (DQN)**: Uses deep learning to approximate Q-values in reinforcement learning.
  - **Policy Gradient Methods**: Optimize policies directly using gradients in reinforcement learning.

## Key Terms in Machine Learning

- **Feature:** An independent variable used for predictions.
- **Label (Target):** The output variable in supervised learning.
- **Training Set:** The portion of data used to train the model.
- **Test Set:** The portion of data used to evaluate the model.
- **Overfitting:** When a model learns noise instead of patterns in the training data.
- **Underfitting:** When a model is too simple to capture underlying patterns in data.
- **Bias-Variance Tradeoff:** The balance between a model's complexity and its ability to generalize.

## Mathematical Equations in Machine Learning

### 1. Linear Regression Equation

Linear regression models the relationship between dependent and independent variables:

\[
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + ... + \beta_n x_n + \epsilon
\]

where:
- \( y \) = Predicted value
- \( x_i \) = Features
- \( \beta_i \) = Coefficients (weights)
- \( \epsilon \) = Error term

### 2. Logistic Regression (for Binary Classification)

\[
P(Y=1|X) = \frac{1}{1 + e^{-(\beta_0 + \beta_1 x_1 + \beta_2 x_2 + ... + \beta_n x_n)}}
\]

where \( P(Y=1|X) \) represents the probability of class 1.

### 3. Cost Function for Linear Regression (Mean Squared Error - MSE)

\[
J(\theta) = \frac{1}{2m} \sum_{i=1}^{m} (h_{\theta}(x^{(i)}) - y^{(i)})^2
\]

where:
- \( m \) = Number of training samples
- \( h_{\theta}(x) \) = Predicted value
- \( y \) = Actual value

### 4. Gradient Descent Update Rule

\[
\theta_j := \theta_j - \alpha \frac{\partial J(\theta)}{\partial \theta_j}
\]

where \( \alpha \) is the learning rate.

## Python Code for Machine Learning

### 1. Linear Regression using Scikit-Learn

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split

# Generate some sample data
np.random.seed(42)
X = np.random.rand(100, 1) * 10  # Feature
y = 2.5 * X + np.random.randn(100, 1) * 2  # Target with noise

# Split into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train Linear Regression model
model = LinearRegression()
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

# Plot results
plt.scatter(X_test, y_test, label="Actual data")
plt.plot(X_test, y_pred, color='red', label="Regression line")
plt.legend()
plt.show()
```

### 2. Logistic Regression for Classification

```python
from sklearn.datasets import load_iris
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

# Load dataset
iris = load_iris()
X, y = iris.data, iris.target

# Binary classification (select only two classes)
X, y = X[y != 2], y[y != 2]

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train Logistic Regression model
model = LogisticRegression()
model.fit(X_train, y_train)

# Predictions
y_pred = model.predict(X_test)

# Accuracy
accuracy = accuracy_score(y_test, y_pred)
print(f"Accuracy: {accuracy:.2f}")
```

### 3. K-Means Clustering

```python
from sklearn.cluster import KMeans
import seaborn as sns

# Generate sample data
np.random.seed(42)
X = np.random.rand(100, 2) * 10  # Random 2D data points

# Apply K-Means Clustering
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(X)
labels = kmeans.labels_

# Plot clusters
sns.scatterplot(x=X[:, 0], y=X[:, 1], hue=labels, palette="viridis", s=100)
plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1], color='red', marker='X', s=200)
plt.title("K-Means Clustering")
plt.show()
```

### 4. Neural Network with TensorFlow/Keras

```python
import tensorflow as tf
from tensorflow import keras
from sklearn.preprocessing import StandardScaler

# Generate synthetic data
np.random.seed(42)
X = np.random.rand(1000, 5)
y = (X.sum(axis=1) > 2.5).astype(int)  # Binary classification

# Standardize data
scaler = StandardScaler()
X = scaler.fit_transform(X)

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Build neural network
model = keras.Sequential([
    keras.layers.Dense(10, activation='relu', input_shape=(5,)),
    keras.layers.Dense(5, activation='relu'),
    keras.layers.Dense(1, activation='sigmoid')
])

# Compile and train the model
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])
model.fit(X_train, y_train, epochs=20, batch_size=10, verbose=1)

# Evaluate the model
loss, accuracy = model.evaluate(X_test, y_test)
print(f"Model Accuracy: {accuracy:.2f}")
```

## Conclusion

Machine Learning provides powerful tools for data analysis and prediction, with applications in healthcare, finance, robotics, and more. Understanding key terms, equations, and implementing models in Python can help in mastering ML concepts and applying them to real-world problems.
