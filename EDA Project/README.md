# ✈️ Flight Price Prediction — Data Preprocessing & EDA

This project focuses on **Exploratory Data Analysis (EDA)** and **data preprocessing** of a flight price dataset using Python and Jupyter Notebook.

The main objective of this project is to understand the dataset, handle missing values, perform feature engineering, and convert categorical data into numerical data using **One-Hot Encoding** so that the dataset can later be used for Machine Learning models.

---

## 📌 Project Overview

Flight price datasets contain a mixture of numerical and categorical features such as airline, source, destination, journey date, departure time, arrival time, and number of stops.

Machine Learning algorithms generally require numerical input, so this project explores and preprocesses these features to prepare the data for future flight price prediction.

### Main tasks performed

* Data loading and inspection
* Exploratory Data Analysis (EDA)
* Identification of missing values
* Handling categorical features
* Feature extraction from date and time columns
* One-Hot Encoding
* Data preprocessing for Machine Learning

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** — Data manipulation and analysis
* **NumPy** — Numerical operations
* **Matplotlib** — Data visualization
* **Seaborn** — Data visualization
* **Scikit-learn** — Machine Learning preprocessing
* **Jupyter Notebook**
* **Visual Studio Code**

---

## 📂 Project Structure

```text
ONE_HEAT_ENCODING/
│
├── EDA_1.ipynb
├── flight_price.xlsx
└── README.md
```

### `EDA_1.ipynb`

The main Jupyter Notebook containing:

* Data exploration
* Data cleaning
* Missing-value analysis
* Feature engineering
* Categorical encoding
* Exploratory analysis

### `flight_price.xlsx`

The original flight price dataset used for analysis and preprocessing.

### `README.md`

Project documentation and setup instructions.

---

## 🔍 Exploratory Data Analysis

The notebook starts by loading the dataset and inspecting its structure.

Typical operations include:

```python
df.head()
```

```python
df.info()
```

```python
df.describe()
```

These operations help understand:

* Number of rows and columns
* Data types
* Numerical statistics
* Missing values
* Categorical features

---

## 🧹 Data Preprocessing

Several preprocessing techniques were explored in the project.

### Handling Missing Values

Missing values can be identified using:

```python
df.isnull().sum()
```

For example, the most common value of a categorical column can be found using:

```python
df["Total_Stops"].mode()
```

Missing values can then be handled using appropriate techniques such as `fillna()`.

---

## 🕐 Feature Engineering

Time-related columns can contain more information than just the original value.

For example, `Arrival_Time` can be separated into:

* Arrival Hour
* Arrival Minute

Example:

```python
df["Arrival_Time"] = df["Arrival_Time"].str.split(" ").str[0]

df["Arrival_Hour"] = df["Arrival_Time"].str.split(":").str[0]

df["Arrival_Minute"] = df["Arrival_Time"].str.split(":").str[1]
```

This converts a time such as:

```text
22:30
```

into:

```text
Arrival_Hour   → 22
Arrival_Minute → 30
```

---

## 🔢 One-Hot Encoding

Categorical columns such as:

* Airline
* Source
* Destination

cannot be directly used by many Machine Learning algorithms.

Therefore, **One-Hot Encoding** is used to convert categorical values into numerical features.

Example:

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder()

encoded = encoder.fit_transform(
    df[["Airline", "Source", "Destination"]]
).toarray()
```

For example, an airline column:

```text
Air India
IndiGo
Jet Airways
```

can be converted into numerical columns such as:

```text
Air India    IndiGo    Jet Airways
    1           0           0
    0           1           0
    0           0           1
```

This makes categorical information suitable for Machine Learning algorithms.

---

## 📊 Dataset Features

Some of the important features in the dataset include:

| Feature           | Description                   |
| ----------------- | ----------------------------- |
| `Airline`         | Airline operating the flight  |
| `Date_of_Journey` | Date of the journey           |
| `Source`          | Starting location             |
| `Destination`     | Destination location          |
| `Route`           | Flight route                  |
| `Dep_Time`        | Departure time                |
| `Arrival_Time`    | Arrival time                  |
| `Duration`        | Total flight duration         |
| `Total_Stops`     | Number of stops               |
| `Additional_Info` | Additional flight information |
| `Price`           | Flight ticket price           |

---

## 💻 How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/TechNinja-01/ONE_HEAT_ENCODING.git
```

### 2. Open the project in VS Code

Open the project folder in **Visual Studio Code**.

### 3. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

### 4. Open the notebook

Open:

```text
EDA_1.ipynb
```

in VS Code.

Make sure the **Jupyter extension** is installed in VS Code.

### 5. Select a Python kernel

In the notebook, select your Python environment/kernel and run the cells sequentially.

---

## 🎯 Learning Objectives

Through this project, the following concepts are practiced:

* Understanding Pandas DataFrames
* Reading Excel datasets
* Data inspection
* Missing-value detection
* Handling categorical data
* Feature engineering
* Working with date and time features
* One-Hot Encoding
* Basic EDA
* Preparing data for Machine Learning

---

## 🚀 Future Improvements

The project can be extended into a complete **Flight Price Prediction** Machine Learning project.

Possible next steps:

1. Complete data cleaning
2. Perform more detailed EDA
3. Convert all required features into numerical form
4. Split the dataset into training and testing sets
5. Train Machine Learning models
6. Compare model performance
7. Perform hyperparameter tuning
8. Evaluate predictions
9. Build a simple prediction application

---

## 👨‍💻 Author

**TechNinja-01**

GitHub:
https://github.com/TechNinja-01

---

## ⭐ Project Status

🚧 **Currently in development**

This repository currently focuses on **EDA and data preprocessing**, with One-Hot Encoding as one of the major preprocessing techniques explored.
