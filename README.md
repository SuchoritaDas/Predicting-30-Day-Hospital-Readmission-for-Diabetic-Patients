# Predicting-30-Day-Hospital-Readmission-for-Diabetic-Patients

End-to-End Database + AI Project on Databricks

Domain: Healthcare Analytics
Platform: Databricks Lakehouse
Project Type: Data Engineering + Machine Learning
Sponsored by: Databricks
Powered by: Codebasics × Indian Data Club

📌 Project Overview

Hospital readmission within 30 days is a critical indicator of healthcare quality, cost efficiency, and patient outcomes.
Diabetic patients experience significantly higher readmission rates due to chronic complexity, medication adjustments, and comorbidities.

This project presents a complete, production-style data and machine learning solution built on Databricks, designed to move from raw healthcare data to decision-ready insights using a structured Bronze → Silver → Gold architecture and an explainable ML model.

The focus is not only on prediction, but on:

Data reliability

Interpretability

Scalable architecture

Real-world healthcare impact

### 🎯 Problem Statement (STAR – Situation)

Hospitals are evaluated on 30-day readmission rates, which directly affect:

Quality-of-care metrics

Operational efficiency

Financial penalties and reimbursements

For diabetic patients, readmission rates are consistently higher than average, yet hospitals often lack:

A structured data pipeline to analyze historical admissions

A reliable way to identify high-risk patients before discharge

Explainable insights that clinicians and administrators can trust

Core Problem

How can hospitals use historical admission data to identify diabetic patients at high risk of 30-day readmission in a way that is scalable, interpretable, and actionable?

### 📊 Dataset Overview (STAR – Situation)

Dataset: Diabetes 130-US Hospitals Dataset (Kaggle)

Time Period: 1999–2008

Records: ~100,000 hospital encounters

Granularity: One row per hospital admission

Key Categories of Columns

The dataset contains 50+ columns, broadly grouped as:

Patient demographics:
age, gender, race, weight

Admission & discharge details:
admission_type_id, admission_source_id, discharge_disposition_id, time_in_hospital, payer_code, medical_specialty

Clinical activity counts:
num_lab_procedures, num_procedures, num_medications,
number_outpatient, number_emergency, number_inpatient

Diagnosis information:
diag_1, diag_2, diag_3, number_diagnoses

Lab results:
max_glu_serum, A1Cresult

Medication indicators:
Diabetes drugs (metformin, insulin, glipizide, etc.), combination therapies, and medication change flags

Target variable:
readmitted_30 → Whether the patient was readmitted within 30 days

This dataset reflects real hospital operations, making it suitable for healthcare risk modeling and decision support.

### 🧩 Task Definition (STAR – Task)

The task was to design and implement:

A robust data architecture to handle raw healthcare data

A clean and validated dataset suitable for analytics and ML

An explainable machine learning model to predict 30-day readmission risk

A solution that mirrors real enterprise data platform practices

Success was defined not by model complexity, but by:

Correct data handling

Clear reasoning

Actionable insights

### 🏗️ Solution Architecture (STAR – Action)

The project follows a Databricks Lakehouse architecture with strict separation of responsibilities.

Raw CSV (Kaggle)
   ↓
Bronze Layer  → Raw, immutable ingestion
   ↓
Silver Layer  → Cleaned, validated, standardized data
   ↓
Gold Layer    → Business-ready, ML-optimized dataset
   ↓
ML Training   → Explainable model + MLflow tracking

### 📂 Repository Structure

Each folder contains:

One Jupyter Notebook

One detailed README explaining that layer

├── bronze/
│   ├── BRONZE_LAYER.ipynb
│   └── README.md
│
├── silver/
│   ├── SILVER_LAYER.ipynb
│   └── README.md
│
├── gold/
│   ├── GOLD_LAYER.ipynb
│   └── README.md
│
├── ml_training/
│   ├── ML_Training.ipynb
│   └── README.md
│
└── README.md  ← (this file)

## 🔍 How the Project Was Implemented (STAR – Action)

### 📥 Data Ingestion & Environment Setup

The dataset was first downloaded as a CSV file from Kaggle and uploaded into the Databricks Free Edition workspace.

To maintain proper organization and data governance:

A dedicated catalog, schema, and volume were created for the project

The CSV file was uploaded using the Databricks Catalog interface

This allowed the data to be accessed directly within notebooks as a table source

This step reflects a real-world data ingestion approach, where raw files are landed into a controlled storage layer before further processing.

Once the data was available inside Databricks, the Bronze–Silver–Gold Medallion Architecture was implemented to structure the data pipeline.


### 🥉 Bronze Layer

Raw CSV data ingested into Databricks volumes

Schema preserved exactly as received

No transformations applied

Ensures traceability and auditability

### 🥈 Silver Layer

Missing and inconsistent values handled

Categorical and numerical fields standardized

Target variable readmitted_30 engineered

Data quality and class distribution validated

### 🥇 Gold Layer

Selection of clinically and operationally meaningful features

Removal of non-actionable or noisy columns

Creation of a stable, ML-ready dataset

### 🤖 ML Training

Logistic Regression chosen for interpretability

Categorical encoding and feature scaling applied

Train/test split with class stratification

Evaluation using AUC

Feature importance extracted for explanation

Experiments and models tracked using MLflow

### 📘 Key Terms & Concepts 

-- 1️⃣ Logistic Regression

What it is
Logistic Regression is a statistical model used for binary classification problems, where the outcome has two possible values.

In this project
It predicts whether a diabetic patient will be:

1 → Readmitted within 30 days

0 → Not readmitted within 30 days

🧠 Why Logistic Regression?

Transparent decision logic

Clinician-friendly interpretation

Suitable for healthcare risk scoring

Focuses on understanding risk drivers, not just prediction

In healthcare, explainability outweighs model complexity.

-- 2️⃣ Probability (Prediction Output)

What it means
Instead of just saying “Yes” or “No,” the model outputs a probability score between 0 and 1.

Example

0.82 → High risk of readmission

0.18 → Low risk of readmission

Why this matters
Hospitals can:

Set risk thresholds

Prioritize patients with the highest risk

-- 3️⃣ Features (X)

What features are
Features are the input variables used by the model to make predictions.

In this project, features include

Patient age and demographics

Length of hospital stay

Number of diagnoses

Emergency and inpatient visit history

Medication and treatment indicators

Simple explanation

Features describe the patient’s condition and hospital experience.

-- 4️⃣ Target Variable (y)

What it is
The target variable is what the model is trying to predict.

In this project

readmitted_30


1 → Patient was readmitted within 30 days

0 → Patient was not readmitted

-- 5️⃣ Coefficients (Feature Weights)

What coefficients mean
Coefficients indicate how strongly each feature influences the prediction.

Positive coefficient → increases readmission risk

Negative coefficient → decreases readmission risk

Example

number_inpatient with a high positive coefficient
→ Patients with prior hospitalizations are more likely to be readmitted

Why this is important
This makes the model explainable, which is critical in healthcare.

-- 6️⃣ Feature Scaling (StandardScaler)

What it is
Feature scaling adjusts numerical values so that all features are on a similar scale.

Why it’s needed
Some features have small ranges (e.g., days in hospital), others have large ranges (e.g., lab counts).
Without scaling, the model may behave incorrectly.

In simple words

Scaling ensures the model treats all features fairly.

-- 7️⃣ Train–Test Split

What it is
The dataset is split into:

Training set → used to train the model

Test set → used to evaluate performance

Why it’s important
Prevents the model from being evaluated on data it has already seen.

-- 8️⃣ Class Imbalance

What it means
In healthcare data, most patients are not readmitted, while fewer are.

This creates an imbalance:

Many 0s (not readmitted)

Fewer 1s (readmitted)

Why it matters
Accuracy alone can be misleading.
That’s why we use AUC, not just accuracy.

-- 9️⃣ AUC (Area Under the ROC Curve)

This is VERY IMPORTANT

What AUC measures
AUC measures how well the model can separate high-risk patients from low-risk patients.

AUC = 0.5 → Random guessing

AUC = 1.0 → Perfect separation

In healthcare
AUC answers this question:

Can the model correctly rank patients by risk?

Why AUC is preferred

Handles class imbalance well

Focuses on ranking, not just correctness

One-line explanation

AUC measures how well the model distinguishes between patients who will be readmitted and those who will not.

-- 🔟 ROC Curve (Brief)

What it is
The ROC curve shows the trade-off between:

True positive rate (catching real readmissions)

False positive rate (false alarms)

Why it matters
Hospitals can adjust thresholds depending on how cautious they want to be.

-- 1️⃣1️⃣ MLflow

What it is
MLflow is a tool for tracking machine learning experiments.

In this project
It tracks:

Model performance (AUC)

Model versions

Parameters and artifacts

Why it’s important

Reproducibility

Transparency

Professional ML lifecycle management

Simple explanation

MLflow helps keep a record of what models were trained and how well they performed.

-- 1️⃣2️⃣ Explainable ML (Why This Matters)

What it means
An explainable model allows humans to understand:

Which factors matter

How decisions are influenced

Why it’s critical in healthcare

Clinicians need trust

Decisions affect patient outcomes

Regulations require transparency


### 📈 Outcomes & Impact (STAR – Result)

-- Key Insights Identified

Prior inpatient visit history

Emergency visit frequency

Length of hospital stay

Number of diagnoses

Medication and treatment changes

-- Real-World Impact

This solution enables hospitals to:

Flag high-risk diabetic patients before discharge

Prioritize follow-up care and monitoring

Improve discharge planning

Reduce avoidable readmissions

Lower healthcare costs while improving outcomes

### 🧰 Tools & Technologies

Databricks Lakehouse

Delta Lake

PySpark

Python

Scikit-learn

MLflow

Unity Catalog

All tools were used in a production-aligned, disciplined manner.

### 🙏 Sponsors & Acknowledgements

Databricks — Platform sponsorship
Codebasics — Initiative and guidance
Indian Data Club — Community and support

This project was built as part of a hands-on Databricks challenge, emphasizing real-world workflows.

### 📌 Final Note

This repository represents a complete project submission, showcasing:

Structured data engineering

Thoughtful analytics

Responsible machine learning

Clear business and healthcare impact

The focus throughout was clarity, discipline, and real-world relevance.

### 🔗 Portfolio & Contact

Portfolio: [https://codebasics.io/portfolio/Suchorita-Das]
LinkedIn: [(https://www.linkedin.com/in/suchorita-das )]
