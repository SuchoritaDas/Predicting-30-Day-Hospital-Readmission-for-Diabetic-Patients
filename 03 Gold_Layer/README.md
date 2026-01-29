# Gold Layer — Business-Ready & ML-Optimized Dataset

### 📌 Purpose of the Gold Layer

The Gold layer prepares a final, purpose-built dataset optimized for:

Machine learning
Interpretability
Business decision-making

This layer ensures that only meaningful, actionable features are exposed for modeling.

### 🧱 Role of Gold in the Architecture

The Gold layer represents the consumer-facing dataset.
It is designed for:
Data scientists
Analysts
ML pipelines
Reporting and insights

Gold does not perform data cleaning — it curates.

### 📂 Input Data

Source: Silver Delta table
Data State: Clean, standardized, validated
The Gold layer relies on the Silver layer’s guarantees.

### 🔧 What This Notebook Does
1️⃣ Feature Selection

Selects clinically and operationally meaningful features
Removes identifiers and low-value fields
Ensures features are interpretable and defensible

2️⃣ Target Alignment

Retains readmitted_30 as the prediction target
Ensures feature-target consistency

3️⃣ ML Readiness

Produces a dataset optimized for training
Keeps features in human-readable form
Avoids premature encoding or transformation

### 🧪 Validation Performed

Feature count verification
Column list inspection
Schema stability checks

These checks confirm that the dataset is model-ready and controlled.

### 💾 Storage Format

Format: Delta Lake
Catalog: Unity Catalog
Layer: Gold

The Gold table serves as the official input for ML training and evaluation.

### 📤 Output

The output is a Gold Delta table containing:
Selected business-relevant features
A clear target variable
Stable schema for modeling

### 🚫 What Is NOT Done in Gold Layer

To maintain clarity and discipline:

No feature encoding
No scaling
No ML training
No model-specific transformations


### ✅ Why This Layer Matters

A well-designed Gold layer:
Improves model explainability
Reduces noise and overfitting

Aligns ML outputs with business understanding

### 🧠 Key Takeaway

The Gold layer is where data becomes decision-ready.
