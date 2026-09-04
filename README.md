# Simple Linear Regression

## 📌 Project Overview

This project demonstrates **Simple Linear Regression** using Python and popular machine learning libraries.

Simple Linear Regression is a supervised machine learning algorithm used to model the relationship between **one independent variable (X)** and **one dependent variable (Y)**.

The model attempts to find the best-fitting straight line through the data.

### Mathematical Equation

$$
Y = b_0 + b_1X
$$

Where:

* **Y** → Dependent variable / Target
* **X** → Independent variable / Feature
* **b₀** → Intercept
* **b₁** → Coefficient / Slope

---

## 🎯 Objective

The main objectives of this project are:

* Understand the concept of Simple Linear Regression
* Separate independent and dependent variables
* Split the dataset into training and testing sets
* Standardize the features
* Train a Linear Regression model
* Perform predictions
* Evaluate model performance
* Understand OLS (Ordinary Least Squares) regression using `statsmodels`

---

## 🛠️ Technologies Used

* Python
* NumPy
* Pandas
* Matplotlib
* Scikit-learn
* Statsmodels
* Jupyter Notebook / VS Code

---

## 📂 Project Structure

```text
Simple-Linear-Regression/
│
├── Simple_Linear_Regression.ipynb
├── README.md
└── dataset/
    └── data.csv
```

---

## 🔄 Machine Learning Workflow

The project follows these steps:

```text
Dataset
   ↓
Data Preprocessing
   ↓
Independent & Dependent Variables
   ↓
Train-Test Split
   ↓
Feature Scaling
   ↓
Model Training
   ↓
Prediction
   ↓
Model Evaluation
   ↓
OLS Regression Analysis
```

---

## 1. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

For machine learning:

```python
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LinearRegression
```

For OLS regression:

```python
import statsmodels.api as sm
```

---

## 2. Independent and Dependent Variables

The dataset is divided into:

### Independent Variable (X)

The feature used to make predictions.

```python
X = df.iloc[:, :-1]
```

### Dependent Variable (y)

The target variable that we want to predict.

```python
y = df.iloc[:, -1]
```

---

## 3. Train-Test Split

The dataset is divided into training and testing data.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.25,
    random_state=32
)
```

Here:

* `X_train` → Training features
* `X_test` → Testing features
* `y_train` → Training target
* `y_test` → Testing target
* `test_size=0.25` → 25% data is used for testing
* `random_state=32` → Ensures reproducible splitting

---

## 4. Feature Scaling

Standardization is performed using `StandardScaler`.

```python
scaler = StandardScaler()

X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

Standardization converts values into a common scale using the **Z-score**:

$$
Z = \frac{X-\mu}{\sigma}
$$

Where:

* `μ` → Mean
* `σ` → Standard deviation

### Important

We use:

```python
scaler.fit_transform(X_train)
```

for training data because the scaler learns the mean and standard deviation from the training data.

For test data, we only use:

```python
scaler.transform(X_test)
```

This prevents information from the test dataset from leaking into the training process.

---

## 5. Linear Regression Model

Create the Linear Regression model:

```python
regressor = LinearRegression()

regressor.fit(X_train, y_train)
```

The model learns the relationship between `X_train` and `y_train`.

---

## 6. Prediction

Predictions can be made using:

```python
y_pred = regressor.predict(X_test)
```

`y_pred` contains the values predicted by the model.

---

## 7. Model Evaluation

The model can be evaluated using metrics such as:

### R² Score

```python
from sklearn.metrics import r2_score

r2 = r2_score(y_test, y_pred)

print("R2 Score:", r2)
```

R² indicates how well the independent variable explains the variation in the dependent variable.

A value closer to **1** generally indicates a better fit.

---

## 8. OLS Linear Regression

Ordinary Least Squares (OLS) is another approach for estimating a linear regression model.

Using `statsmodels`:

```python
import statsmodels.api as sm

X_train_sm = sm.add_constant(X_train)

model = sm.OLS(y_train, X_train_sm).fit()

print(model.summary())
```

### Why `add_constant()`?

`statsmodels` does not automatically add the intercept in the same way that `sklearn.LinearRegression` does.

Therefore:

```python
X_train_sm = sm.add_constant(X_train)
```

adds the intercept term.

---

## 📊 OLS Summary

The `model.summary()` output provides important statistical information such as:

* R-squared
* Adjusted R-squared
* Coefficients
* Standard Error
* t-statistic
* p-value
* Confidence intervals
* F-statistic

This makes `statsmodels` particularly useful when you want to understand the **statistical significance and relationship between variables**, rather than only making predictions.

---

## 📈 Regression Line

The goal of Simple Linear Regression is to find the best-fitting line:

$$
\hat{Y} = b_0 + b_1X
$$

The model minimizes the difference between actual values and predicted values.

These differences are called **residuals**:

$$
Residual = Y - \hat{Y}
$$

OLS finds the coefficients that minimize the **sum of squared residuals**.

---

## 📁 Key Libraries

| Library      | Purpose                      |
| ------------ | ---------------------------- |
| NumPy        | Numerical operations         |
| Pandas       | Data manipulation            |
| Matplotlib   | Data visualization           |
| Scikit-learn | Machine learning             |
| Statsmodels  | Statistical modeling and OLS |

---

## 🚀 How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
```

### 2. Navigate to the project

```bash
cd Simple-Linear-Regression
```

### 3. Install dependencies

```bash
pip install numpy pandas matplotlib scikit-learn statsmodels
```

### 4. Open the notebook

Open:

```text
Simple_Linear_Regression.ipynb
```

using **Jupyter Notebook** or **VS Code**.

---

## 📌 Conclusion

This project provides a basic implementation of **Simple Linear Regression** and demonstrates the complete machine learning workflow from data preprocessing to model evaluation.

It also introduces **OLS regression using Statsmodels**, which provides deeper statistical insights into the regression model.

---

## 👨‍💻 Author

**Harsh Soni**

B.Tech CSE | Machine Learning & Software Development
