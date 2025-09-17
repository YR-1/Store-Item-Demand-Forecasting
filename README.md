# Store-Item-Demand-Forecasting

## 📌 Objective
The goal of this project is to **forecast sales for the next 3 months** using historical transaction data.  
We apply a machine learning based time series forecasting approach, evaluate results with standard metrics, and document the methodology.

---

## 📂 Dataset
- **train.csv** – Historical sales data (date, store, item, sales).  
- **test.csv** – Test data (future dates, store, item).  
- **sample_submission.csv** – Example submission format.  

**Data fields**:
- `date` – Transaction date (continuous, no holidays/closures).  
- `store` – Store ID.  
- `item` – Item ID.  
- `sales` – Units sold (target variable).  

---

## 🛠️ Approach

1. **Data Preprocessing**
   - Converted `date` to datetime type and set it as index.
   - Created time based features: `dayofweek`, `month`, `year`, `lag features`, and `rolling means`.
   - Merged with store & item IDs to allow per (store, item) modeling.

2. **Modeling**
   - Baseline: Naive forecast (last known sales).  
   - Main model: **LightGBM Regressor** trained on engineered time series features.  
   - Iterative prediction for the test period to simulate true forecasting.

3. **Evaluation**
   - Metrics: **MAE, RMSE, MAPE** to capture absolute and relative errors.  
   - Split training/validation by time (not randomly) to avoid data leakage.  

4. **Forecasting**
   - Trained per store item group.
   - Generated predictions for the next 3 months.  
   - Saved results in the format: `id, sales`.  

---

## 📊 Results
- Models achieved reasonable accuracy on validation data.  
- Feature engineering (lags & rolling windows) improved predictive performance.  
- Final predictions are stored in `submission.csv`.  

---

## 🧰 Technologies and Tools
- **Python 3.9+**
- **Pandas** – Data manipulation  
- **NumPy** – Numerical computing  
- **Matplotlib** – Visualization  
- **scikit-learn** – Metrics, preprocessing, model training  
- **LightGBM** – Gradient boosting for forecasting  

---

## ▶️ How to Reproduce

### 1. Clone Repository
```bash
git clone https://github.com/YR-1/Store-Item-Demand-Forecasting.git

