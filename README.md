# ✈️ Flight Price Prediction

A Machine Learning project that predicts **flight ticket prices** based on various flight-related features such as airline, source, destination, journey date, departure time, arrival time, duration, and number of stops.

## 📌 Project Overview

Flight prices depend on several factors, including:

* ✈️ Airline
* 📍 Source
* 🎯 Destination
* 📅 Date of Journey
* 🕐 Departure Time
* 🕐 Arrival Time
* 🔄 Total Stops
* ⏱️ Flight Duration

The goal of this project is to preprocess flight data, perform exploratory data analysis, transform categorical features into numerical values, and build a Machine Learning model capable of predicting flight prices.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Jupyter Notebook**

---

## 📂 Project Structure

```text
Flight-Price-Prediction/
│
├── data/
│   └── Data_Train.xlsx
│
├── notebooks/
│   └── Flight_Price_Prediction.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 📊 Dataset

The dataset contains information about different flights and their ticket prices.

Important columns include:

| Feature           | Description                           |
| ----------------- | ------------------------------------- |
| `Airline`         | Airline operating the flight          |
| `Date_of_Journey` | Date on which the journey takes place |
| `Source`          | Starting location                     |
| `Destination`     | Destination location                  |
| `Route`           | Flight route                          |
| `Dep_Time`        | Departure time                        |
| `Arrival_Time`    | Arrival time                          |
| `Duration`        | Total flight duration                 |
| `Total_Stops`     | Number of stops                       |
| `Additional_Info` | Additional flight information         |
| `Price`           | Flight ticket price — target variable |

---

## 🔄 Data Preprocessing

The project performs several preprocessing steps before training the Machine Learning model.

### 1. Handling Missing Values

Missing values are identified using:

```python
df.isnull().sum()
```

For example, the most frequent value of `Total_Stops` can be found using:

```python
df["Total_Stops"].mode()
```

---

### 2. Extracting Arrival Time

The arrival time is separated into hour and minute:

```python
df["Arrival_Time"] = df["Arrival_Time"].str.split(" ").str[0]

df["Arrival_Hour"] = df["Arrival_Time"].str.split(":").str[0]
df["Arrival_Minute"] = df["Arrival_Time"].str.split(":").str[1]
```

Similar preprocessing can be applied to departure time.

---

### 3. Removing Unnecessary Columns

Columns that are no longer required can be removed using:

```python
df.drop("Date_of_Journey", axis=1, inplace=True)
```

Here:

* `axis=1` means column
* `inplace=True` modifies the original DataFrame

---

### 4. One-Hot Encoding

Categorical features such as `Airline`, `Source`, and `Destination` are converted into numerical features.

```python
from sklearn.preprocessing import OneHotEncoder

encoder = OneHotEncoder()

encoded = encoder.fit_transform(
    df[["Airline", "Source", "Destination"]]
).toarray()
```

This converts categorical values into numerical `0` and `1` values.

---

## 🤖 Machine Learning

After preprocessing, the dataset is divided into:

```text
Training Data
      ↓
Machine Learning Model
      ↓
Predicted Flight Price
```

The target variable is:

```python
Price
```

The remaining relevant features are used as input variables.

---

## 📈 Model Evaluation

The trained model can be evaluated using regression metrics such as:

* Mean Absolute Error (MAE)
* Mean Squared Error (MSE)
* Root Mean Squared Error (RMSE)
* R² Score

Example:

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

mae = mean_absolute_error(y_test, y_pred)
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print("MAE:", mae)
print("MSE:", mse)
print("R2 Score:", r2)
```

---

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/Flight-Price-Prediction.git
```

### 2. Navigate to the project

```bash
cd Flight-Price-Prediction
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

On Linux/macOS:

```bash
source venv/bin/activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Start Jupyter Notebook

```bash
jupyter notebook
```

Open the project notebook and run the cells sequentially.

---

## 📦 Requirements

Example `requirements.txt`:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
openpyxl
jupyter
```

---

## 🎯 Project Goals

The main objectives of this project are:

* Understand and clean real-world flight data
* Handle missing values
* Perform feature engineering
* Encode categorical variables
* Prepare data for Machine Learning
* Train a regression model
* Evaluate model performance
* Predict flight ticket prices

---

## 🔮 Future Improvements

Possible improvements include:

* Add more Machine Learning models
* Perform hyperparameter tuning
* Improve feature engineering
* Compare multiple regression algorithms
* Build a Streamlit web application
* Deploy the prediction model
* Add an interactive flight price prediction interface

---

## 👨‍💻 Author

**Harsh Soni**

B.Tech Computer Science Engineering

---

## ⭐ If You Like This Project

If you found this project useful, consider giving the repository a ⭐ on GitHub.
