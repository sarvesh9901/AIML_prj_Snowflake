

# 📘 Customer Churn Prediction using Snowflake & Snowpark (End-to-End ML Project)

## 🚀 Overview

This project is an **end-to-end AI/ML Proof of Concept (POC)** developed entirely inside **Snowflake**, without using any local compute environments or external tools.

The objective is to demonstrate how Snowflake can be used for:

* Data ingestion
* Data engineering
* Machine learning model training
* Prediction storage
  — using **Snowpark Python** within Snowflake itself.

This project was created as part of the evaluation for an **AI/ML Engineer** role with a focus on **Snowflake + ML Operations**.

---

# 🎯 Problem Statement – Predict Customer Churn

Businesses face revenue loss when customers stop using their services.
The goal of this project is to **predict if a customer is likely to churn**, based on numeric, categorical, and behavioral features.

### ✔ Why it matters?

* Helps reduce churn
* Improves customer retention
* Enables personalized offers
* Supports better business decisions

---

# 🛠️ Solution Approach

This POC implements a complete ML lifecycle inside Snowflake:

### 🔹 1. Data Generation (Mockaroo)

Synthetic churn dataset generated with fields like age, income, spend, tenure, membership tier, etc.

### 🔹 2. Snowflake Setup

Created using SQL:

* Warehouse: `ML_WH`
* Database: `ML_PROJECT`
* Schema: `CHURN_POC`
* Table: `CUSTOMERS`

### 🔹 3. Data Loading

Mockaroo CSV was uploaded directly using **Snowsight → Load Data**.

### 🔹 4. ML Pipeline in Snowpark Python

A **Snowpark Python Worksheet** was used to perform:

* Load data from Snowflake table
* Convert to pandas for modeling
* Encode features (OneHotEncoding)
* Train a RandomForestClassifier
* Evaluate model accuracy
* Generate predictions
* Store results back into Snowflake

### 🔹 5. Prediction Storage

Predictions are saved into a Snowflake table:
`CUSTOMER_CHURN_PREDICTIONS`

---

# 📂 Files Included in This Repository

This repository contains:

### 📌 **1. SQL Scripts**

All SQL scripts used to create:

* Warehouse
* Database
* Schema
* Customer table

These are the exact scripts executed inside Snowflake.

---

### 📌 **2. Snowpark Python Notebook**

A notebook (exported from Snowflake) that contains:

* Data loading
* Model training
* Preprocessing
* Prediction generation
* Writing predictions back into Snowflake

This is the same code executed in the **Snowpark Python Worksheet**.

---

### 📌 **3. Sample Mockaroo Data**

* A sample CSV or schema file used to generate the customer dataset.
* Helps evaluators replicate or understand the dataset used.

---

# 📊 Dataset Description (Mockaroo)

| Column             | Description                        |
| ------------------ | ---------------------------------- |
| customer_id        | Unique ID                          |
| gender             | Male/Female                        |
| age                | 18–70                              |
| income             | Annual income                      |
| tenure_months      | Duration of customer relationship  |
| monthly_spend      | Monthly spending                   |
| num_tickets_raised | Support ticket count               |
| membership_tier    | Basic / Standard / Premium / Elite |
| churn              | 0 or 1 (target variable)           |

---

# 🧠 ML Model (Snowpark Python)

### ✔ Preprocessing

* OneHotEncoding for `gender` & `membership_tier`
* Numeric features used directly

### ✔ Model

**RandomForestClassifier**

* n_estimators=150
* max_depth=None
* random_state=42

### ✔ Output

Two columns generated:

* `predicted_churn`
* `predicted_churn_probability`

Stored in:
`CUSTOMER_CHURN_PREDICTIONS`

---

# 🧪 Results

### 🔸 Model Accuracy

~80–90% depending on dataset randomness.

### 🔸 Prediction Table Sample

| customer_id | predicted_churn | predicted_churn_probability |
| ----------- | --------------- | --------------------------- |
| 101         | 1               | 0.82                        |
| 102         | 0               | 0.10                        |
| ...         | ...             | ...                         |

---

# ▶️ How to Run This Project

### **Prerequisites**

* Snowflake free trial account
* Mockaroo dataset

### **Steps**

1. Run the SQL scripts from `sql_scripts/` folder
2. Upload the dataset using Snowflake **Load Data**
3. Open Snowpark Python Worksheet
4. Run the notebook provided in `python_notebook/`
5. Validate output in:

   ```
   ML_PROJECT.CHURN_POC.CUSTOMER_CHURN_PREDICTIONS
   ```

Everything runs fully inside Snowflake — **no local system required**.

---

# 📌 Key Highlights

✔ Fully Snowflake-native ML pipeline
✔ Snowpark Python for model training
✔ End-to-end data engineering + ML workflow
✔ Synthetic dataset creation with Mockaroo
✔ Clear predictions stored inside Snowflake
✔ No external compute or notebook used

---

# 🏁 Conclusion

This POC effectively demonstrates how Snowflake can be used as a complete machine learning platform including:

* Data ingestion
* Feature engineering
* ML model training
* Prediction storage

It showcases strong cloud-native AI/ML engineering skills aligned to the role requirements.

---

# 👨‍💻 Author

**Sarvesh**
AI/ML Engineer Candidate

