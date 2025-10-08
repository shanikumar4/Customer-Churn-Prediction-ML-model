# Customer Churn Prediction for a Telecommunications Company

This repository contains the code and findings for a machine learning project focused on predicting customer churn. The goal is to identify customers who are likely to stop using a telecom service, enabling the business to take proactive retention measures.

## 📄 Project Overview

Customer churn is a critical metric for subscription-based businesses. This project aims to build a binary classification model that predicts whether a customer will churn or not based on their account information and the services they use. The final model is interpreted to provide actionable business insights.

## 💾 Dataset

The project uses the **Telco Customer Churn** dataset, which is publicly available on Kaggle.
* **Link:** [https://www.kaggle.com/datasets/blastchar/telco-customer-churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

## 🛠️ Project Workflow

The project was structured into several key phases:

1.  **Data Cleaning and Preprocessing:**
    * Loaded the dataset and handled missing values (specifically in the `TotalCharges` column).
    * Corrected data types for analysis.

2.  **Feature Engineering:**
    * Converted categorical features into a numerical format using one-hot encoding.
    * Scaled all numerical features using `StandardScaler` to prepare the data for modeling and prevent issues like convergence warnings.

3.  **Model Building and Evaluation:**
    * Multiple models were tested, including Logistic Regression and Random Forest.
    * The class imbalance in the dataset (fewer churners than non-churners) was addressed using the `class_weight='balanced'` parameter.
    * The final champion model, a **Logistic Regression**, was selected based on its strong performance on the most critical business metric: **Recall**.

4.  **Model Interpretation:**
    * The final model was interpreted using the **SHAP (SHapley Additive exPlanations)** library to understand the key factors driving its predictions.

## 📈 Key Results and Findings

The final Logistic Regression model achieved an excellent **recall of 82%** for the 'Churn' class. This means it successfully identifies 82 out of every 100 customers who are actually at risk of leaving.

The SHAP analysis revealed the most significant factors influencing churn:

![SHAP Summary Plot](shap_summary_plot.png)

* **Contract Type:** Customers with **month-to-month contracts** are the most likely to churn.
* **Tenure:** **Newer customers** (low tenure) have a much higher probability of churning.
* **Lack of Add-on Services:** Customers without key services like **Tech Support** or **Online Security** are more likely to leave.

## 🚀 How to Run this Project

1.  Clone this repository to your local machine.
    ```bash
    git clone [your-repository-url]
    ```
2.  Install the required libraries.
    ```bash
    pip install pandas scikit-learn matplotlib seaborn jupyter shap imbalanced-learn
    ```
3.  Download the `Telco-Customer-Churn.csv` file from the Kaggle link above and place it in the project folder.
4.  Open and run the `churn_prediction.ipynb` Jupyter Notebook.

## 📁 Repository Structure

    ├── churn_prediction.ipynb    # The main Jupyter Notebook with all code and analysis
    ├── shap_summary_plot.png     # The output plot showing feature importance
    ├── Telco-Customer-Churn.csv  # The dataset file (to be added by the user)
    └── README.md                 # This file
