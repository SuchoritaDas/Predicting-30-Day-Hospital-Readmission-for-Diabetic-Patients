### 📌 Purpose of the Silver Layer

The Silver layer is responsible for transforming raw healthcare data into a clean, standardized, and analytics-ready dataset.
This layer applies business and data quality rules while still retaining detailed information required for modeling and analysis.
In real-world data platforms, the Silver layer is where data trust is enforced.

### 🧱 Role of Silver in the Architecture

The Silver layer acts as the bridge between raw ingestion (Bronze) and business consumption (Gold).

It ensures that:

Raw inconsistencies are resolved

Data types are standardized

Derived fields required for analysis are created

Downstream layers can rely on consistent semantics

### 📂 Input Data

Source: Bronze Delta table
Granularity: One row per hospital encounter
Data State: Raw, uncleaned, unvalidated
The Silver layer does not change the grain of the data — each record still represents one hospital visit.

### 🔧 What This Notebook Does

1️⃣ Data Quality Handling

Identifies missing and invalid values
Standardizes categorical values
Ensures numerical fields are consistent and usable

2️⃣ Target Variable Engineering

Creates a binary target variable: readmitted_30
1 → Patient readmitted within 30 days
0 → Patient not readmitted within 30 days
This transformation is critical for predictive modeling and evaluation.

3️⃣ Feature Standardization

Harmonizes demographic fields
Normalizes clinical activity counts
Prepares diagnosis and medication indicators for downstream use

4️⃣ Validation & Consistency Checks

Verifies target class distribution
Confirms column completeness
Ensures no accidental data loss

### 🧪 Data Validation Performed

The Silver layer performs meaningful validation, including:

Record count comparison with Bronze
Target variable distribution checks
Schema verification

These checks ensure that the dataset is analysis-safe before progressing.

### 💾 Storage Format

Format: Delta Lake
Catalog: Unity Catalog
Layer: Silver

The Silver Delta table represents the single trusted source for all analytics and modeling.

### 📤 Output

The output is a Silver Delta table that:
Contains cleaned and standardized data
Includes the engineered target variable
Retains all analytically relevant features
This table becomes the input for the Gold layer.

### 🚫 What Is NOT Done in Silver Layer

To maintain separation of concerns, the following are intentionally excluded:

Feature selection for modeling
Business prioritization of features
Encoding or scaling
Machine learning

### ✅ Why This Layer Matters

The Silver layer ensures that:
Models are trained on reliable data
Analytics are reproducible
Business logic is consistently applied

Without a strong Silver layer, Gold and ML outputs lose credibility.

### 🧠 Key Takeaway

The Silver layer is where data quality becomes enforceable and reliable.
