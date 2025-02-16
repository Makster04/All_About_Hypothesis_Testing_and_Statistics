# Key Concepts in Linear Regression

## 1. Types of Linear Regression
- **Simple Linear Regression**: Involves one independent variable and one dependent variable. It fits a straight line to the data.
- **Multiple Linear Regression**: Involves two or more independent variables.

---

## 2. Equation of Linear Regression
The linear regression model is represented by the equation:

$$\[
y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \dots + \beta_n x_n + \epsilon
\]$$

Where:
- $$**y**$$: Target (dependent) variable
- $$**xₑ**$$: Independent variables (features)
- $$**\(\beta_0\)**$$: Intercept
- $$**\(\beta_i\)**$$: Coefficients for each feature
- $$**\(\epsilon\)**$$: Error term (residual)

---

## 3. Objective
Minimize the sum of squared errors (SSE) between predicted and actual values:

\[
SSE = \sum (y_i - \hat{y}_i)^2
\]
The coefficients \(\beta_0, \beta_1, \dots, \beta_n\) are chosen to minimize this error.

---

## 4. Assumptions of Linear Regression
- Linear relationship between independent and dependent variables
- Homoscedasticity (constant variance of errors)
- Errors are normally distributed
- No multicollinearity (independent variables should not be highly correlated)

---

## 5. Evaluation Metrics
Common metrics for evaluating linear regression models:
- **Mean Absolute Error (MAE)**
- **Mean Squared Error (MSE)**
- **Root Mean Squared Error (RMSE)**
- **R² (Coefficient of Determination)**

---

## Python Implementation of Linear Regression

### Step 1: Import Libraries
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
```

### Step 2: Load and Prepare Data
```python
# Sample dataset
data = {
    "Experience": [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    "Salary": [30000, 32000, 34000, 36000, 40000, 43000, 46000, 50000, 52000, 55000]
}
df = pd.DataFrame(data)

# Split data into features and target
X = df[['Experience']]  # Feature (independent variable)
y = df['Salary']        # Target (dependent variable)

# Split into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

### Step 3: Fit the Linear Regression Model
```python
# Create and train the model
model = LinearRegression()
model.fit(X_train, y_train)
```

### Step 4: Make Predictions
```python
# Predict on the test set
y_pred = model.predict(X_test)

# Display results
print("Coefficients:", model.coef_)
print("Intercept:", model.intercept_)
```

### Step 5: Evaluate the Model
```python
# Calculate evaluation metrics
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"Mean Squared Error (MSE): {mse:.2f}")
print(f"R² Score: {r2:.2f}")
```

### Step 6: Visualize the Results
```python
plt.scatter(X, y, color='blue', label='Actual Data')
plt.plot(X, model.predict(X), color='red', label='Fitted Line')
plt.xlabel("Years of Experience")
plt.ylabel("Salary")
plt.title("Linear Regression - Salary Prediction")
plt.legend()
plt.show()
```

---

### Explanation of the Code:
1. **Data Preparation**: The dataset is converted into a pandas DataFrame. We separate the feature (X) and the target (y), then split the data into training and testing sets.
2. **Model Creation and Training**: We use `LinearRegression` from `sklearn` to create the model and fit it using the training data.
3. **Prediction**: We predict the target variable for the test set using the trained model.
4. **Evaluation**: Metrics such as MSE and R² are calculated to assess the performance of the model.
5. **Visualization**: The scatter plot shows the actual data, and the red line represents the fitted linear regression line.

---

## Advanced Concepts in Linear Regression
- **Regularization**: Techniques like Lasso (L1) and Ridge (L2) regression add penalties to the coefficients to prevent overfitting.
- **Polynomial Regression**: Extends linear regression by fitting a polynomial function to the data.
- **Feature Scaling and Engineering**: Important for improving the model’s performance.
- **Handling Multicollinearity**: Use techniques like Variance Inflation Factor (VIF) to detect and address multicollinearity.

# Key Concepts in Linear Regression

## Regularization (Ridge and Lasso Regression)

### Concept
Regularization helps reduce overfitting by adding a penalty term to the loss function. It controls the size of the coefficients:

- **Ridge Regression (L2 Regularization)**: Adds the sum of squared coefficients to the loss function.
  \[ \text{Loss} = \text{SSE} + \lambda \sum \beta_i^2 \]
  
- **Lasso Regression (L1 Regularization)**: Adds the sum of absolute values of coefficients to the loss function.
  \[ \text{Loss} = \text{SSE} + \lambda \sum |\beta_i| \]
  
  Lasso can shrink some coefficients to zero, effectively performing feature selection.

---

### Python Implementation
```python
from sklearn.linear_model import Ridge, Lasso
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score

# Using the same dataset as multiple linear regression
data = {
    "SquareFootage": [1000, 1200, 1500, 1800, 2000, 2300, 2500, 3000, 3500, 4000],
    "Bedrooms": [2, 3, 3, 4, 4, 4, 5, 5, 6, 6],
    "Age": [10, 15, 20, 25, 30, 35, 40, 45, 50, 60],
    "Price": [200000, 220000, 250000, 280000, 300000, 330000, 350000, 400000, 450000, 500000]
}
df = pd.DataFrame(data)

X = df[['SquareFootage', 'Bedrooms', 'Age']]
y = df['Price']

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Ridge Regression
ridge = Ridge(alpha=1.0)
ridge.fit(X_train, y_train)
ridge_pred = ridge.predict(X_test)

# Lasso Regression
lasso = Lasso(alpha=1.0)
lasso.fit(X_train, y_train)
lasso_pred = lasso.predict(X_test)

# Evaluation
print("Ridge Regression R² Score:", r2_score(y_test, ridge_pred))
print("Lasso Regression R² Score:", r2_score(y_test, lasso_pred))
```

---

### When to Use Each Method:
- **Multiple Linear Regression**: When the relationship between variables is linear.
- **Polynomial Regression**: When the data exhibits a clear non-linear relationship.
- **Regularization (Ridge/Lasso)**: When there’s a risk of overfitting or multicollinearity, especially with high-dimensional datasets.
