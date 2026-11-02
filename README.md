# Air Quality Index (AQI) Estimation Using Machine Learning Techniques

A data analytics and machine-learning project that estimates the Air Quality Index (AQI) from pollutant measurements and city/date information using the India city-day air quality dataset.

> **Scope:** This project estimates AQI for held-out observations. It is *not* a future-AQI forecasting system.

---

## 📌 Project Objectives

- Explore air quality measurements, distributions, and missing-data patterns.
- Clean and prepare the dataset for supervised regression modeling.
- Train and compare four regression models: **Linear Regression**, **Random Forest**, **Gradient Boosting**, and **XGBoost**.
- Evaluate model performance using **MAE** (Mean Absolute Error), **RMSE** (Root Mean Squared Error), and **R² Score**.
- Visualize model performance, actual vs. predicted values, and residual error distributions.

---

## 📊 Dataset

- **Source:** [Kaggle India Air Quality Data Collection](https://www.kaggle.com/datasets/rohanrao/air-quality-data-in-india) (specifically `data/city_day.csv`).
- **Dimensions:** The raw dataset contains 29,531 rows and 16 columns. After removing rows without target AQI values, dropping the derived `AQI_Bucket` field, and excluding Xylene (due to ~61.32% missing values), the processed working dataset contains **24,850 rows and 14 columns**.
- **Imputation:** Remaining predictor missing values are handled via a preprocessing pipeline using training-set medians for numerical features and the mode for categorical (`City`) features.

---

## 📈 Model Performance Results

| Model | MAE | RMSE | R² Score |
| :--- | :--- | :--- | :--- |
| **Gradient Boosting** | 18.4283 | **31.4081** | **0.9087** |
| **Random Forest** | 17.7693 | 32.3495 | 0.9032 |
| **XGBoost** | **17.7473** | 35.0770 | 0.8862 |
| **Linear Regression** | 24.9152 | 37.3474 | 0.8709 |

* **Gradient Boosting** achieved the best overall balance with the lowest RMSE and highest R² score.
* **XGBoost** achieved the lowest Mean Absolute Error (MAE).

---

## 🗂️ Repository Structure

```text
AQI-Quality-Index-Estimation-Using-Machine-Learning-Techniques/
│
├── data/
│   └── city_day.csv                 # India city-day air quality dataset
├── figures/                         # Generated evaluation plots & charts
│   ├── figure_1_error_comparison.png
│   ├── figure_2_r2_comparison.png
│   ├── figure_3_actual_vs_predicted.png
│   ├── figure_4_residual_analysis.png
│   └── figure_5_aqi_time_series.png
├── results/                         # Exported metrics and summary text
│   ├── final_model_performance.csv
│   ├── model_performance_metrics.csv
│   └── experiment_summary.txt
├── src/
│   └── train_aqi_models.py          # Python training script
├── AQI_Prediction_ML.ipynb          # Comprehensive Jupyter Notebook workflow
├── Project_Report.pdf               # Detailed academic project report
├── requirements.txt                 # Project python dependencies
└── README.md                        # Project documentation
