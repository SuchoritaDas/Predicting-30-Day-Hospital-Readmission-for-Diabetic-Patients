# 🤖 ML Training Layer — Readmission Risk Modeling & MLflow Tracking

### 📌 Purpose of the ML Training Layer

The ML Training layer is responsible for transforming curated Gold data into actionable predictive insights.
The goal of this notebook is not to build the most complex model, but to:
Produce a reliable and explainable baseline model
Ensure reproducibility and traceability using MLflow
Translate model outputs into real-world healthcare insights
In healthcare analytics, interpretability and trust are as important as predictive performance.

### 🧱 Role of ML Training in the Architecture

This layer sits after the Gold layer and consumes only business-approved, ML-ready features.

It ensures:

No leakage from raw or cleaned data
Clear separation between data preparation and modeling
Stable inputs for experimentation and evaluation

### 📂 Input Data

Source: Gold Delta table (gold_diabetes_ready)
Data State: Clean, curated, feature-controlled
Granularity: One row per hospital encounter

All features used in modeling are:

Clinically meaningful
Operationally relevant
Interpretable by non-technical stakeholders

### 🔧 What This Notebook Does

1️⃣ Data Loading & Sampling

Loads the Gold layer dataset from Unity Catalog
Applies sampling to support Databricks serverless constraints
Ensures representative class distribution
Sampling is a practical and common approach when building baseline models under resource constraints.

2️⃣ Feature–Target Separation

Defines:

Features (X): Patient demographics, clinical activity, and treatment indicators
Target (y): readmitted_30 (30-day readmission indicator)
This separation ensures clear modeling intent and prevents ambiguity.

3️⃣ Categorical Encoding

Applies label encoding to categorical features
Keeps transformations simple and explainable
Avoids premature complexity
Encoding is performed at the ML layer to preserve Gold data readability.

4️⃣ Train–Test Split

Splits data into training and testing sets
Uses stratification to maintain class balance
Prevents data leakage
This step ensures fair and reliable evaluation.

5️⃣ Feature Scaling

Applies standard scaling to numerical features
Ensures proper convergence of Logistic Regression
Improves coefficient stability
Feature scaling is critical for linear models in mixed-scale datasets.

6️⃣ Model Selection & Training

Model chosen: Logistic Regression

Rationale:

High interpretability
Transparent decision logic
Accepted in healthcare environments
Trained using scaled features

The emphasis is on clarity over complexity.

7️⃣ Model Evaluation

Evaluated using AUC (Area Under the ROC Curve)

AUC chosen due to:

Class imbalance
Focus on ranking high-risk patients

Evaluation focuses on model usefulness, not just accuracy.

8️⃣ Model Interpretation

Extracts and analyzes feature coefficients
Identifies top drivers of readmission risk
Translates statistical output into clinical insight
Examples of influential factors:

Prior inpatient visits
Emergency visit frequency
Length of hospital stay
Medication and treatment patterns

9️⃣ MLflow Experiment Tracking

Logs:

Model performance metrics
Model artifacts
Input schema examples

Enables:

Reproducibility
Comparison across runs
Model governance
MLflow integration ensures professional ML lifecycle management.

### 📤 Output

The outputs of this notebook include:
A trained Logistic Regression model
Evaluation metrics (AUC)
Feature importance insights
MLflow-tracked experiment runs

These outputs support both analysis and decision-making.

### 🚫 What Is NOT Done in ML Training Layer

To maintain clarity and discipline, the following are intentionally excluded:
Deep learning or black-box models
Automated hyperparameter tuning
Production deployment
Real-time inference pipelines
This notebook focuses on baseline modeling and insight generation.

### 🎯 Business & Healthcare Impact

The trained model enables hospitals to:
Identify high-risk diabetic patients before discharg
Allocate follow-up care efficiently
Improve patient outcomes
Reduce avoidable readmissions and costs
The emphasis is on actionable risk identification, not automation for its own sake.

### 🧠 Key Takeaway

The ML Training layer prioritizes explainability, reliability, and traceability, ensuring that machine learning supports healthcare decisions responsibly.
