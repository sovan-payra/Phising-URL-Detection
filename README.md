# 🛡️ Phishing Website Detection Using Machine Learning

A machine learning project for detecting whether a website is **legitimate or malicious/phishing** based on URL and website-related features. 🔍🌐

The project performs **exploratory data analysis, feature selection, preprocessing, model training, model comparison, evaluation, and prediction of new URLs**.

---

## 📌 Project Overview

🎣 Phishing websites attempt to imitate legitimate websites to steal sensitive information such as:

* 🔑 Passwords
* 💳 Banking details
* 👤 Personal information
* 📧 Login credentials

This project uses **machine learning algorithms** to classify websites based on features associated with their URLs, domains, SSL status, web traffic, page rank, and other characteristics.

The goal is to build a model capable of identifying potentially malicious websites from their characteristics. 🛡️

---

## 📊 Dataset

The project uses the **Phishing Websites Dataset** from the UCI Machine Learning Repository.

### 📋 Dataset Characteristics

* 📄 **11,055 records**
* 📊 **32 columns**
* 🎯 Target column: `Result`
* 🔢 Features are primarily represented using numerical values such as `-1`, `0`, and `1`

### 🔎 Important Features

Some important features include:

* `having_IP_Address`
* `URL_Length`
* `Shortining_Service`
* `having_At_Symbol`
* `Prefix_Suffix`
* `having_Sub_Domain`
* `SSLfinal_State`
* `Domain_registeration_length`
* `HTTPS_token`
* `Request_URL`
* `URL_of_Anchor`
* `DNSRecord`
* `web_traffic`
* `Page_Rank`
* `Google_Index`
* `Statistical_report`

---

## 🔍 Exploratory Data Analysis

Before training the machine learning models, the dataset is analyzed using **Exploratory Data Analysis (EDA)**. 📈

The following steps are performed:

1. 📐 Checking the dataset shape
2. 📋 Inspecting column information
3. 🔎 Checking missing values
4. 📊 Generating descriptive statistics
5. 🔗 Calculating feature correlations
6. 🌡️ Visualizing the correlation matrix
7. 🔍 Identifying highly correlated features
8. 🧹 Identifying features with low correlation to the target

### 📐 Dataset Shape

The original dataset contains:

```text
11055 rows × 32 columns
```

✅ No missing values were found in the dataset.

---

## 🧹 Feature Selection

Feature selection is performed to remove weak or unnecessary features and improve the quality of the training data.

### 🔗 Correlation Analysis

A correlation matrix is generated to investigate relationships between features.

A strong correlation was found between:

```text
Favicon ↔ popUpWidnow
Correlation: 0.939633
```

### 🗑️ Removed Features

Several weak features were removed:

```python
features_to_drop = [
    'double_slash_redirecting',
    'Redirect',
    'Favicon',
    'popUpWidnow',
    'id',
    'RightClick',
    'Submitting_to_email',
    'Links_pointing_to_page',
    'port',
    'on_mouseover'
]
```

### 📉 Dataset After Feature Selection

Before:

```text
(11055, 32)
```

After:

```text
(11055, 22)
```

This reduces unnecessary information before model training. ⚡

---

## ⚙️ Data Preprocessing

The dataset is divided into **training and testing sets** using:

```python
train_test_split(
    X,
    y,
    test_size=0.3,
    random_state=42
)
```

### 📊 Data Split

* 🧠 **70%** for training
* 🧪 **30%** for testing

### 📏 Feature Scaling

Numeric features are standardized using:

```python
StandardScaler()
```

The expected feature names are also saved using Joblib:

```python
joblib.dump(feature_names, 'feature_names.pkl')
```

This helps maintain the correct feature structure when testing new URLs.

---

## 🤖 Machine Learning Models

Multiple machine learning algorithms are trained and compared:

* 🌳 **Decision Tree**
* 🌲 **Random Forest**
* 📈 **Logistic Regression**
* 📊 **Naive Bayes**
* 👥 **K-Nearest Neighbors (KNN)**
* 🎯 **Support Vector Machine (SVM)**
* 🧠 **Multi-Layer Perceptron (MLP)**

Testing multiple algorithms makes it possible to select the model with the best performance.

---

## 📈 Model Performance

| 🤖 Model               | 🎯 Accuracy | 📊 F1 Score |
| ---------------------- | ----------: | ----------: |
| 🌳 Decision Tree       |      95.00% |      95.62% |
| 🌲 **Random Forest**   |  **96.11%** |  **96.61%** |
| 📈 Logistic Regression |      91.98% |      93.00% |
| 📊 Naive Bayes         |      58.22% |      42.06% |
| 👥 KNN                 |      92.92% |      93.81% |
| 🎯 SVM                 |      94.42% |      95.16% |
| 🧠 MLP                 |      95.57% |      96.12% |

---

## 🏆 Best Model

The models are compared primarily using their **F1 scores**.

The best-performing model is:

```text
🌲 Random Forest
Accuracy : 0.9611
F1 Score : 0.9661
```

🏆 Therefore, **Random Forest** is selected as the best-performing model for phishing website classification.

---

## 📉 Model Evaluation

Several evaluation techniques are used to analyze model performance.

### 📋 Classification Report

For every model, the project calculates:

* 🎯 Accuracy
* 🔬 Precision
* 🔄 Recall
* 📊 F1 Score

### 🧩 Confusion Matrix

Confusion matrices are generated for each trained model to visualize:

* ✅ True Positives
* ✅ True Negatives
* ❌ False Positives
* ❌ False Negatives

### 📊 Accuracy & Precision Comparison

A bar chart compares the **accuracy and precision** of the trained machine learning algorithms.

### 📈 ROC Curve & AUC

ROC curves are generated to compare the classification ability of different models.

The **Area Under the Curve (AUC)** is also calculated for supported classifiers.

---

## 🔗 URL Feature Extraction

The project includes an `extract_features()` function that converts a URL into features that can be passed to the trained machine learning model. 🔍

Some URL characteristics examined include:

```text
🌐 IP address usage
📏 URL length
🔗 URL shortening services
📧 @ symbol
↪️ Double-slash redirects
➖ Prefix/suffix characters
🌍 Subdomains
🔒 HTTPS usage
```

The generated features are arranged according to the feature names expected by the trained model.

---

## 🔮 Predicting New URLs

Users can enter a URL:

```text
Enter a URL to check if it's safe:
```

The URL is processed by the machine learning model and classified as:

### ✅ Safe

```text
Safe
```

or

### 🚨 Malicious

```text
Malicious
```

### 🧪 Example

```text
Enter a URL to check if it's safe: www.google.com

URL: www.google.com
Prediction: Safe
```

---

## 🛠️ Technologies Used

* 🐍 **Python**
* 📓 **Google Colab**
* 🧠 **Machine Learning**
* 📊 **Data Analysis**
* 📈 **Data Visualization**
* 🔐 **URL-based Phishing Detection**

---

## 📦 Libraries Used

The project uses several Python libraries for data analysis, visualization, preprocessing, machine learning, and model evaluation.

* 🐼 `pandas` - Data loading, manipulation, and analysis
* 🔢 `numpy` - Numerical operations
* 📊 `matplotlib` - Data visualization and graphs
* 🎨 `seaborn` - Heatmaps and confusion matrix visualization
* 🤖 `scikit-learn` - Machine learning algorithms, preprocessing, and evaluation
* 💾 `joblib` - Saving and loading model-related data
* 🚀 `xgboost` - Gradient boosting machine learning support
* 📁 `os` - File and directory operations
* ⏱️ `time` - Measuring model training time
* 🔎 `re` - URL pattern detection using regular expressions
* 🌐 `ipaddress` - IP address detection
* 🔗 `urllib.parse` - URL parsing

### 📚 Main Imports

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import joblib
import os
import time
import re
import ipaddress

from urllib.parse import urlparse
```

### 🤖 Scikit-learn Components

```python
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler, LabelEncoder

from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.naive_bayes import GaussianNB
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC
from sklearn.neural_network import MLPClassifier

from sklearn.metrics import (
    accuracy_score,
    precision_score,
    f1_score,
    classification_report,
    confusion_matrix,
    roc_curve,
    auc
)
```

---

## 📥 Installation

Install the required Python libraries using:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib xgboost
```

💡 Python standard-library modules such as `os`, `time`, `re`, `ipaddress`, and `urllib.parse` do not need to be installed separately.

---

## 🚀 How to Run

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/sovan-payra/phishing-url-detection.git
```

### 2️⃣ Open the Project Directory

```bash
cd phishing-url-detection
```

### 3️⃣ Install Dependencies

```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib xgboost
```

### 4️⃣ Open the Notebook

Open the project notebook using:

* 📓 Google Colab
* 🪐 Jupyter Notebook
* 💻 VS Code

### 5️⃣ Run the Notebook

Execute the notebook cells sequentially to:

1. 📥 Load the dataset
2. 🔍 Perform exploratory data analysis
3. 🧹 Perform feature selection
4. ⚙️ Preprocess the dataset
5. 🧠 Train machine learning models
6. 📊 Evaluate model performance
7. 🏆 Select the best model
8. 🔗 Enter and test new URLs

---

## ☁️ Running on Google Colab

If using Google Colab, mount Google Drive:

```python
from google.colab import drive

drive.mount('/content/drive')
```

Then load the dataset:

```python
USIIL = pd.read_csv(
    '/content/drive/MyDrive/Project/csv_result-Training Dataset.csv'
)
```

⚠️ Change the dataset path according to where you have stored the CSV file.

---

## 📂 Project Structure

```text
phishing-url-detection/
│
├── 📓 phishing_detection.ipynb
├── 📊 csv_result-Training Dataset.csv
├── 💾 feature_names.pkl
├── 📦 requirements.txt
└── 📖 README.md
```

---

## 🔄 Project Workflow

```text
📊 Dataset
    ↓
🔍 Exploratory Data Analysis
    ↓
🧹 Feature Selection
    ↓
⚙️ Data Preprocessing
    ↓
✂️ Train-Test Split
    ↓
📏 Feature Scaling
    ↓
🤖 Model Training
    ↓
📈 Model Evaluation
    ↓
🏆 Best Model Selection
    ↓
🔗 URL Feature Extraction
    ↓
🛡️ Safe / Malicious Prediction
```

---

## ⚠️ Limitations

The URL prediction component uses simplified feature extraction for some features.

Features that cannot be directly calculated from the URL are currently assigned default values.

Because of this, predictions for completely new URLs may not achieve the same accuracy as the test-set results.

For production use, the feature extraction process should reproduce all dataset features accurately instead of relying on default values.

⚠️ This project should therefore be considered an **educational machine learning implementation**, not a replacement for professional phishing detection or cybersecurity software.

---

## 🚀 Future Improvements

Possible improvements include:

* 🌐 Implement all URL and domain feature extraction methods
* 📅 Add WHOIS/domain-age analysis
* 🔒 Retrieve SSL certificate information
* 🧹 Improve feature engineering
* ⚙️ Add hyperparameter tuning
* 🔄 Use cross-validation
* 💾 Save the complete preprocessing pipeline
* 🚀 Add XGBoost to the final model comparison
* 🎨 Build a Streamlit interface
* 🌐 Build a Flask or FastAPI backend
* 🖥️ Create a browser-based phishing URL checker
* ☁️ Deploy the trained model as a web application
* 📊 Add an interactive analytics dashboard
* 🔌 Create a phishing-detection API

---

## 📚 Dataset Source

🏛️ **UCI Machine Learning Repository**

📊 **Dataset:** Phishing Websites

The dataset contains website characteristics that can be used to train machine learning models for phishing website classification.

---

## 🎯 Project Purpose

This project demonstrates how **machine learning can be applied to cybersecurity**, particularly phishing website detection. 🛡️

It provides practical experience with:

* 📊 Data analysis
* 🔍 Exploratory Data Analysis
* 🧹 Feature selection
* ⚙️ Data preprocessing
* 🤖 Machine learning classification
* 📈 Model evaluation
* 🔗 URL feature extraction
* 🛡️ Cybersecurity applications

---

## 📄 License

This project is intended for **educational and research purposes**. 🎓

Refer to the original dataset source for its applicable licensing and usage conditions.

---

## ⭐ Support

If you find this project useful:

⭐ **Star the repository**
🍴 **Fork the project**
🛠️ **Improve the model**
📢 **Share the project**

Happy coding! 🐍🤖🛡️
