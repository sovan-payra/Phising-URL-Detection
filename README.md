# Phising-URL-Detection
# 🔐 Phishing URL Detection

This project aims to detect phishing websites using machine learning algorithms based on various URL features. It analyzes URLs to distinguish between legitimate and phishing sites, helping protect users from potential threats.

## 📁 Project Structure

- `Phising URL Detection.ipynb` - Main Jupyter Notebook containing:
  - Exploratory Data Analysis (EDA)
  - Feature engineering
  - Model training (Logistic Regression, Decision Tree, Random Forest, KNN, SVM, Naive Bayes, MLP)
  - Evaluation metrics and result visualization

## 📊 Dataset

The dataset includes various features extracted from URLs, such as:
- URL length
- Presence of HTTPS
- Use of special characters
- Number of dots
- Domain age, etc.

**Target Variable**:  
- `0`: Legitimate  
- `1`: Phishing

## ⚙️ Features

- URL feature extraction
- Multiple ML model training and comparison
- Confusion matrix, accuracy, precision, recall, F1-score
- Graphical visualization of results

## 📦 Libraries Used

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/sovan-payra/phishing-url-detection.git
   cd phishing-url-detection
