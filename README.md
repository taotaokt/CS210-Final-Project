# SQL-Driven Analysis of E-Commerce User Behavior for Purchase Prediction

## Team Project
This project was developed collaboratively as part of a data science course.

## My Contributions
- Built and optimized SQL queries for large-scale user behavior analysis  
- Implemented data preprocessing and ETL pipeline using Python and Pandas  
- Contributed to feature engineering and machine learning model development  


## Project Description

This project builds a **scalable SQL-based data warehouse** and an **end-to-end machine learning pipeline** to analyze user behavior logs from a multi-category e-commerce platform and predict purchase probability.

The system demonstrates a complete data science workflow, including data ingestion, storage, feature engineering, modeling, and evaluation.


## Tech Stack

- **SQL (MySQL)** – data warehousing, aggregation, indexing  
- **Python (Pandas)** – ETL pipeline and data processing  
- **Machine Learning** – Scikit-learn, XGBoost, LightGBM  
- **Visualization & Analysis** – Matplotlib  
- **Model Interpretability** – SHAP  


## Project Overview

- **Dataset:** Kaggle Multi-Category Store E-commerce Behavior Data (5M+ event logs)  
- **Goal:** Predict user purchase probability based on behavioral patterns  

- **Pipeline:**  
  Data ingestion → Cleaning → SQL warehouse → Feature engineering → Modeling → Evaluation → Visualization  


## Data Warehouse Design

We use a **star schema** to efficiently store millions of events and support analytical SQL queries.

- **Fact Table:** user_behavior  
- **Dimension Tables:** users, products  

**Advantages:**
- Efficient aggregation compared to raw logs  
- Scalable for large datasets  
- Supports behavioral and conversion analysis  


## ETL Pipeline

Key features of the ETL system:

- Stream-based chunk loading (`chunksize=500,000`)  
- Data cleaning (timestamp correction, handling missing values)  
- Bulk ingestion using SQL (`LOAD DATA LOCAL INFILE`)  
- Optimized indexing strategy  
- Memory-efficient processing of large datasets  


## Machine Learning Models

Models evaluated:

- Logistic Regression (baseline)  
- Random Forest  
- XGBoost  
- LightGBM  
- Soft Voting Ensemble  

**Feature categories:**
- Session-based features  
- Action frequency  
- Category diversity  
- Price-related interactions  

**Evaluation metrics:**
- ROC / AUC  
- Precision-Recall Curve  
- Calibration Curve  
- Lift Analysis  


## Key Insights

- Behavioral features are more predictive than price-related features  
- Top-ranked users show significantly higher conversion rates  
- User activity peaks suggest optimal marketing timing  
- Category-level trends reveal business opportunities  


## How to Run

### **1. Set up MySQL**

```sql
source sql/create_tables.sql;
source sql/indexes.sql;
```

### **2. Configure Python environment**

```bash
pip install -r requirements.txt
```

### **3. Run ETL**

Open `ETL_Pipeline.ipynb` → run all cells.

### **4. Build features + train models**

Open `Modeling.ipynb`.

### **5. Generate visualizations**

Open `Visualization.ipynb`.
