# 🏦 bank-marketing-prediction

## 📌 Project Overview

This project uses machine learning to predict whether a bank customer will subscribe to a term deposit based on customer information and previous marketing campaign data.

The goal is to explore the dataset, prepare the data, train different classification models, and evaluate their performance.

## 📊 Dataset

- Source: "Bank Marketing Dataset – Kaggle" (https://www.kaggle.com/datasets/janiobachmann/bank-marketing-dataset)
- File: "bank.csv"
- Rows: 11,162
- Columns: 17
- Target variable: "deposit"
  - "yes": Customer subscribed to a term deposit.
  - "no": Customer did not subscribe.

The dataset is not included in this repository. Download it from Kaggle and place "bank.csv" inside the "data/" directory.

## 🔄 Project Workflow

1. Load and inspect the dataset.
2. Perform exploratory data analysis (EDA).
3. Check missing values, duplicate records, and unusual values.
4. Analyze customer characteristics and subscription patterns.
5. Prepare the data for machine learning.
6. Encode categorical variables.
7. Split the data into training and testing sets.
8. Train and evaluate classification models.
9. Compare model performance.
10. Tune the Random Forest model using GridSearchCV.
11. Analyze feature importance using two methods.

## 🧹 Data Preparation

- Checked for missing values and duplicate records.
- Converted the target variable into binary values.
- Applied one-hot encoding to categorical features.
- Used stratified train-test splitting (80% training, 20% testing).
- Excluded "duration" from the model features because call duration is only known after a marketing call. Including it would introduce information leakage for a prediction made before contacting the customer.

## 👾 Machine Learning Models

The following models were trained and evaluated:

- Logistic Regression
- Scaled Logistic Regression
- Decision Tree
- Random Forest

### 📈 Model Comparison

|Model| Accuracy| Precision| Recall| F1-score|
|---|---:|---:|---:|---:|
|Random Forest| 72.68%| 78.00%| 59.00%| 67.20%|
|Logistic Regression| 69.95%| 74.00%| 56.30%| 64.00%|
|Scaled Logistic Regression| 69.50%| 73.20%| 56.10%| 63.60%|
|Decision Tree| 68.43%| 71.30%| 55.90%| 62.60%|

Random Forest achieved the best F1-score among the initial models.

## ⚙️ Hyperparameter Tuning

GridSearchCV with 5-fold cross-validation was used to tune the Random Forest model.

Best parameters:

- **max_depth** : None
- **min_samples_split** : 10
- **n_estimators** : 200

Best cross-validation F1-score: 69.52%

### 🏆 Tuned Random Forest Performance

|Metric| Score|
|---|---:|
|Accuracy| 72.95%|
|Precision (Deposit = Yes)| 76.00%|
|Recall (Deposit = Yes)| 62.00%|
|F1-score (Deposit = Yes)| 69.00%|

The tuned model achieved a modest improvement in accuracy, recall, and F1-score compared with the baseline Random Forest model. Precision decreased slightly, showing a trade-off between precision and recall.

## 🔍 Feature Importance

Two approaches were used to investigate the contribution of features:

- Random Forest Feature Importance: Measures how features contribute to impurity reduction across the trees.
- Permutation Importance: Measures how model performance changes when individual features are shuffled.

Permutation Importance identified "contact_unknown" as the most influential feature for the model's F1-score on the test set.

Feature importance indicates predictive usefulness, not causation.

## 🛠️ Technologies Used

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Jupyter Notebook**
- **Git and GitHub**

## 📂 Repository Structure
```
bank-marketing-prediction/
│
├── notebooks/
│   └── bank_marketing_analysis.ipynb
│
├── data/
│   └── bank.csv     # Download separately; not tracked by Git
│
├── .gitignore
├── README.md
└── requirements.txt
```
## 🚀 How to Run

1. **Clone the repository:**
```
git clone https://github.com/mobo2r-ali/bank-marketing-prediction.git
```
2. **Navigate to the project directory:**
```
cd bank-marketing-prediction
```
3. **Install the required libraries:**
```
pip install -r requirements.txt
```
4. **Download "bank.csv" from the Kaggle dataset linked above.**

5. **Place the dataset in the "data/" directory.**

6. **Open the notebook:**
```
jupyter notebook
```
7. **Run ***notebooks/bank_marketing_analysis.ipynb*****

## 📝 Conclusion

This project demonstrates a complete beginner-level machine learning workflow, from exploratory data analysis and preprocessing to model training, evaluation, and hyperparameter tuning.

The tuned Random Forest model achieved an F1-score of approximately 69% for customers who subscribed to a term deposit.

The results provide a baseline for further experimentation with feature engineering, model selection, and classification thresholds.

## ⚠️ Limitations
- Model performance depends on the dataset and the selected features.
- The results do not establish causal relationships between customer characteristics and subscription decisions.
- Further validation on unseen data from other campaigns would be useful to assess generalization.