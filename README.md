# COPPA Risk Prediction - Data Analytics Competition FIND IT 2025 (UGM)

This repository contains the complete pipeline for building a machine learning model to predict COPPA (Children’s Online Privacy Protection Act) risk for mobile applications. The project was developed as a submission for the **Data Analytics Competition FIND IT 2025**, organized by **Universitas Gadjah Mada (UGM)**.

## 🧠 Background

With the growing digital exposure of children, mobile apps play an increasing role in education and entertainment. However, this also raises concerns about data privacy. Regulations like the **Children’s Online Privacy Protection Act (COPPA)** are designed to protect children under 13 from inappropriate data collection practices.

This competition challenges participants to develop a model to predict whether an app is at risk of violating COPPA regulations based on app characteristics such as download counts, developer attributes, and privacy policy features.

## 🎯 Problem Statement

**Task**: Binary classification  
**Target Variable**: `coppaRisk` (`True` = high risk, `False` = low risk)  
**Evaluation Metric**: AUC (Area Under the ROC Curve)

The goal is to build a model that can accurately classify whether an app poses a potential COPPA compliance risk.

## 📁 Dataset Description

Key features include:

| Column | Description |
|--------|-------------|
| `developerCountry` | Developer's country of origin |
| `countryCode` | App’s target region (e.g., GLOBAL, NA, APAC) |
| `userRatingCount` | Total number of ratings received |
| `primaryGenreName` | App genre (e.g., Games, Education) |
| `downloads` | Range of download counts |
| `deviceType` | Device types supported |
| `hasPrivacyLink` | Whether a privacy policy link is provided |
| `hasTermsOfServiceLink` | Whether a ToS link is provided |
| `hasTermsOfServiceLinkRating` | ToS quality rating (low/medium/high) |
| `isCorporateEmailScore` | Score for email professionalism |
| `adSpent` | Ad spending amount |
| `appAge` | Age of the app in days |
| `averageUserRating` | Average rating |
| `appContentBrandSafetyRating` | Content suitability rating |
| `appDescriptionBrandSafetyRating` | Description suitability rating |
| `mfaRating` | Advertising-focused app rating |
| `coppaRisk` | (Label) Whether the app is at risk of COPPA violation |

## ⚙️ Preprocessing Steps

- **Data Cleaning**:
  - Removed invalid or malformed download ranges.
  - Standardized inconsistent or obfuscated country names.
  - Replaced missing or unknown values with appropriate defaults (e.g., 0 or `'UNKNOWN'`).

- **Feature Engineering**:
  - Categorical features were label-encoded.
  - Grouped rare categories to reduce noise.

- **Handling Class Imbalance**:
  - Upsampled the minority class (`coppaRisk = True`) using `sklearn.utils.resample` for balanced training.

## 🤖 Modeling

- **Model Used**: [`XGBoost Classifier`](https://xgboost.readthedocs.io/)
- **Why XGBoost?**: It’s a powerful, scalable gradient boosting model known for handling imbalanced data, regularization, and high performance in classification tasks.

### Training & Evaluation:
- Data split using `train_test_split`
- Performance evaluated using:
  - **Confusion Matrix**
  - **Classification Report**
  - **ROC-AUC Score**

## 🧪 Prediction & Submission

The final model was used to generate predictions for the test set. Predictions are binary labels (`True`/`False`) indicating the app’s COPPA compliance risk.

## 📌 Conclusion

This project presents a complete machine learning pipeline — from preprocessing and feature engineering to model training with XGBoost — aimed at identifying mobile apps that might be at risk of violating COPPA. This contributes to safer digital environments for children by enabling proactive content moderation and app store policy enforcement.
