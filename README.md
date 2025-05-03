# Home Energy Usage Prediction

A machine learning project that explores household electricity usage and builds two models:
1. **Regression Model** to predict total power consumption using real-time features like voltage, current, and sub-metered appliance usage.
2. **Classification Model** to predict whether energy usage is unusually high based on the time of day.

---

## Project Overview

This project explores how household appliances and usage patterns drive electricity consumption. Using data from a real house in France, we analyze and model energy usage over time.

---

## Dataset

**Source**: [UCI Machine Learning Repository - Individual Household Electric Power Consumption](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)

- Measurements recorded every minute from December 2006 to November 2010
- 2+ million data points
- Features include:
  - `Global_active_power` (Target for regression)
  - `Voltage`, `Global_intensity`, `Sub_metering_1/2/3`
  - Timestamp features like `hour`, `day`, `weekday`, and `month`

---
## Preprocessing Steps

- Converted all numeric columns from string to float
- Extracted features from datetime (`hour`, `weekday`, etc.)
- Filtered for 2010 data in the regression task to reduce computational load
- Dropped or handled null values appropriately

---

## Models

### 1. Power Consumption Prediction (Regression)
- **Objective**: Predict `Global_active_power` in kW using real-time measurements
- **Model Used**: `RandomForestRegressor`
- **Features**: `Voltage`, `Global_intensity`, sub-metering, and time-based features

#### Evaluation
- **MSE**: ~0.0005
- **R² Score**: ~0.9994 → Predicts power usage with extremely high accuracy

---

### 2. High Usage Classifier (Classification)
- **Objective**: Predict whether power usage is unusually high using only time-based features
- **Model Used**: `RandomForestClassifier`
- **Features**: `hour`, `day`, `month`, `weekday`
- **Target**: Binary label indicating if `Global_active_power` > 75th percentile

#### Evaluation
| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| 0 (Normal) | 0.92 | 0.95 | 0.94 | 307,502 |
| 1 (High)   | 0.83 | 0.77 | 0.80 | 102,354 |
| **Accuracy** | **–** | **–** | **0.90** | 409,856 |

---
## Tools Used

- Python 
- Google Colab Notebook

---
## Blog Post

- This project is featured in a Medium article:  
👉 *[From Voltage to Insight: Predicting Power Use with Real Home Data](https://medium.com/@paboda-ratnayake/from-voltage-to-insight-966fc838a84b)*

---

