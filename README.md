# NYC Taxi Trip Duration Prediction (Orange + Python)

**Course:** SEP 6DA3 – Data Analytics and Big Data  
**Institution:** McMaster University  
**Semester:** Fall 2025  
**Team:** Group 6  
**Contributors:** Andi Dong, Zhiyu Hu, Foram Brahmbhatt, Jiarui Yang, Linghe Shen, Shiyu Chen  
**Instructor:** Prof. Pedro Tondo  

---

## 🧠 Project Overview
This project explores the **NYC Taxi Trip Duration dataset**, a large-scale real-world dataset containing millions of taxi rides with trip-level details such as pickup time, location, passenger count, and trip duration.  
The goal was to **build an end-to-end machine learning workflow** that demonstrates the process of data preprocessing, feature engineering, and predictive modeling using both **Orange** (visual interface) and **Python** (scripting environment).

Through this dual approach, we aimed to:
1. Understand the impact of **feature selection** and **data leakage** on model performance.  
2. Compare different **modeling techniques** (Linear Regression, Random Forest, LightGBM).  
3. Reflect on the complementary strengths of visual tools and programmatic approaches.

---

## 🧩 Workflow Summary

### 🟧 Orange (No-Code Workflow)
- Imported the dataset using **File** and **Select Columns** widgets.
- Assigned proper roles:
  - **Target:** `trip_duration`
  - **Ignored:** `dropoff_datetime`, `dropoff_longitude`, `dropoff_latitude` (to avoid data leakage)
  - **Features:** `vendor_id`, `pickup_datetime`, `passenger_count`, `store_and_fwd_flag`
- Visualized key patterns:
  - Trip durations are **right-skewed** (most < 2000 sec ≈ 30 min).
  - Demand peaks at **8–9 AM** and **5–7 PM** (rush hours).
- Evaluated models:
  - **Linear Regression:** unrealistically high R² (1.0) due to data leakage.
  - **Random Forest:** more reasonable R² ≈ 0.09 after fixing leakage.

### 🐍 Python (Code-Based Workflow)
- Cleaned and engineered data in **Pandas**:
  - Created new features: `pickup_hour`, `pickup_dayofweek`, `pickup_month`, `distance_km`, and `speed_kmph`.
  - Removed leakage columns (`dropoff_datetime`, coordinates).
- Trained and evaluated models using **Scikit-learn** and **LightGBM**:
  - Train/test split adjusted from **70/30 → 80/20**.
  - Tuned Random Forest (`n_estimators=200`, `max_depth=20`).
  - Added **LightGBM** baseline model for better performance.

| Model | MAE (sec) | RMSE (sec) | R² |
|--------|------------|------------|----|
| Linear Regression (Orange) | — | — | 1.00 *(leakage)* |
| Random Forest (Orange) | — | — | 0.09 |
| LightGBM (Python) | 31.11 | 747.41 | — |

---

## 📊 Key Insights
- **Data leakage** can drastically inflate model performance and must be prevented.  
- **Feature engineering** (e.g., distance & speed) has greater impact than switching algorithms.  
- Combining **visual analysis (Orange)** with **coding flexibility (Python)** improves both understanding and performance.  
- **LightGBM** demonstrated superior accuracy and interpretability with feature importance analysis.

---

## 💡 Reflection
This lab taught our team the importance of **critical thinking in data analytics** — identifying leakage, validating models properly, and balancing automation with code control.  
By working collaboratively, we not only corrected flawed results but also deepened our understanding of how feature design and evaluation shape real-world predictive modeling.

---

## 🧰 Technologies Used
- **Orange 3.36+**
- **Python 3.11**
- **Pandas**, **NumPy**, **Matplotlib**, **Seaborn**
- **Scikit-learn**
- **LightGBM**

---

## 📁 Repository Structure
