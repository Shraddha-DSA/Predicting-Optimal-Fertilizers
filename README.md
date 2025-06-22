# Predicting-Optimal-Fertilizers
# Fertilizer Prediction - Kaggle Playground Series S5E6

This repository contains my solution to the Kaggle [Playground Series - Season 5, Episode 6](https://www.kaggle.com/competitions/playground-series-s5e6) competition. The task is to **predict the optimal fertilizer** based on crop, soil, and weather conditions using **machine learning models**.

---

## 📌 Problem Statement

Given features like:

- **Temperature**
- **Humidity**
- **Moisture**
- **Soil Type**
- **Crop Type**
- **Nitrogen, Potassium, Phosphorous levels**

The goal is to predict the **top 3 fertilizers** suitable for each observation. The evaluation metric used is:

### ✅ MAP@3 (Mean Average Precision @ 3)

---

## 🔍 Dataset Overview

Each observation contains:

- **Categorical features**: `Soil Type`, `Crop Type`
- **Numerical features**: `Temperature`, `Humidity`, `Moisture`, `Nitrogen`, `Potassium`, `Phosphorous`
- **Target**: `Fertilizer Name`

---

## 🧠 Models Used

I explored the following models:

| Model            | Approach Highlights |
|------------------|---------------------|
| **Random Forest** | Handled mixed data types and overfitting using `max_depth`, `n_estimators` |
| **XGBoost**       | Fast and scalable gradient boosting using `predict_proba` for MAP@3 |
| **Decision Tree** | Simple and interpretable baseline |

---

## ⚙️ Preprocessing Steps

1. **One-Hot Encoding** of `Soil Type` and `Crop Type`
2. **Label Encoding** of the target variable `Fertilizer Name`
3. **Feature Engineering**:
   - Concatenated numerical + encoded categorical features
   - Reindexed test categorical features to match train columns
4. **Model Evaluation**:
   - Used `predict_proba()` to generate top-3 class predictions
   - Converted top-3 indices back to label names for submission

---

## 📊 Evaluation

- **Validation Strategy**: Used `train_test_split()` with `test_size=0.2`
- **Metric**: MAP@3
- **Best Validation Score**: ~0.4034 using RandomForest

---

## 🗂 File Structure

```bash
├── data/
│   ├── train.csv
│   ├── test.csv
├── notebooks/
│   ├── random_forest_solution.ipynb
│   ├── xgboost_solution.ipynb
│   ├── decision_tree_solution.ipynb
├── Optimal_Fertilizers_by_XGBoost.csv
├── README.md
