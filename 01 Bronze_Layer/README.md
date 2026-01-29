# 🥉 Bronze Layer — Raw Data Ingestion

### 📌Purpose of the Bronze Layer

The Bronze layer is responsible for ingesting raw data exactly as received from the source system and storing it in a reliable, queryable format.
This layer does not perform cleaning, transformation, or feature engineering.
Its only objective is to ensure that raw data is:

Safely ingested
Traceable
Reproducible
Available for downstream processing
In real-world data platforms, the Bronze layer acts as the system of record.

### 🧱 Bronze Layer Design Principles

This notebook strictly follows these principles:

No data modification
Raw data is stored exactly as it appears in the source file.

Schema preservation
All columns and data types are retained.

Immutability
Bronze tables are not overwritten casually. Any changes upstream require re-ingestion.

Auditability
Bronze data allows verification of downstream transformations.

### 🔧 What This Notebook Does
1️⃣ Load Raw Data from Databricks Volume

Reads the raw CSV file stored in Databricks Volumes

Uses Spark to load data efficiently

2️⃣ Apply Initial Schema

Ensures consistent column interpretation

Prevents silent data type issues later in the pipeline

### 3️⃣ Basic Validation

Row count checks
Schema inspection
Column presence verification
No data is filtered, cleaned, or modified at this stage.

### 🧪 Data Validation Performed

The following checks are intentionally lightweight:
Record count verification
Column list confirmation
Schema inspection using printSchema()
These checks ensure:
Data ingestion succeeded
No data loss occurred during loading

### 💾 Storage Format

Format: Delta Lake
Catalog: Unity Catalog
Layer: Bronze

Using Delta Lake at the Bronze stage provides:

Reliable storage
ACID compliance
Compatibility with downstream Spark processing

### 📤 Output

The output of this notebook is a Bronze Delta table containing:
Raw hospital encounter records
Original column names and values
No transformations applied
This table serves as the foundation for the Silver layer.

### 🚫 What Is NOT Done in Bronze Layer

To maintain architectural discipline, the following are intentionally excluded:

Missing value handling
Data cleaning
Feature engineering
Target variable creation
Business logic

All such operations are deferred to the Silver layer.

### ✅ Why This Layer Matters

A well-designed Bronze layer:
Prevents accidental data corruption
Enables reproducibility
Supports debugging and audits
Mirrors enterprise data lake practices
Without a proper Bronze layer, downstream analytics and machine learning become unreliable.

### 🧠 Key Takeaway

The Bronze layer is about trust and traceability, not intelligence.
This notebook establishes a clean and reliable starting point for all downstream healthcare analytics and machine learning workflows.
