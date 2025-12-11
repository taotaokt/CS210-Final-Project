# **SQL-Driven Analysis of E-Commerce User Behavior for Purchase Prediction**

This project builds a **scalable, SQL-based data warehouse** and an **end-to-end machine learning pipeline** to analyze user behavior logs from a multi-category e-commerce platform and predict purchase probability.
Using a star-schema MySQL warehouse, engineered features, gradient-boosting models, and SHAP interpretability, the system demonstrates an enterprise-style workflow for data management and predictive analytics.

---

## **Project Overview**

* **Dataset:** Kaggle Multi-Category Store E-commerce Behavior Data (5M+ event logs)
* **Goal:** Predict user purchase probability based on behavioral patterns
* **Technologies:**

  * **MySQL** (star schema, SQL aggregation, index optimization)
  * **Python + Pandas** (ETL, chunked streaming)
  * **Scikit-learn, XGBoost, LightGBM** (ML models & evaluation)
  * **SHAP** (model interpretability)
* **Pipeline:** Data ingestion → Cleaning → SQL warehouse → Feature engineering → Modeling → Evaluation → Visualization

---

## **Data Warehouse Design**

We use a **star schema** to efficiently store millions of events and support analytical SQL queries.

**Fact Table:** user_behavior
**Dimension Tables:** users, products

Advantages:

* Better aggregation performance vs. flat logs
* Scalable to tens of millions of rows
* Enables conversion analysis, product interest tracking, session statistics

*(Insert your diagram here)*

```
figures/project_process.png
```

---

## **ETL Pipeline**

Key features of our ETL system:

* Stream-based chunk loading (`chunksize=500,000`)
* Real-time cleaning (timestamp fix, missing categories/brands → "unknown")
* Efficient bulk ingestion (`LOAD DATA LOCAL INFILE`)
* Deferred indexing for faster import
* Memory-efficient: handles multi-million row files on commodity hardware

---

## **Machine Learning Models**

We evaluate multiple models:

* Logistic Regression (baseline)
* Random Forest
* XGBoost
* LightGBM
* Soft-Voting Ensemble

**Feature categories:**

* Session features
* Action frequency
* Category diversity
* Price/interaction features

**Evaluation metrics:**

* ROC / AUC
* PR Curve / Average Precision
* Calibration curves
* Lift charts

---

## **Key Insights**

* Behavioral intensity (sessions, actions per session) is far more predictive than price signals.
* Top 10% model-ranked users show **6× higher** conversion rates.
* Activity peaks around **17:00**, suggesting optimal marketing windows.
* Smartphone category dominates platform revenue.

---

## **How to Run**

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
