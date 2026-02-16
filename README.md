# 📊 Student Performance Regression Model (Azure ML)

## 📌 Project Overview

This project focuses on building a regression model to predict a student's exam score based on behavioral, academic, and lifestyle variables. The model was developed and executed using **Azure Machine Learning**, including experiment tracking and metric logging.

**Complete implementation documentation:** 📄 Student Performance Model (PDF)

---

## 📂 Dataset

**Source:** [Kaggle - Student Performance Dataset](https://www.kaggle.com/datasets/amar5693/student-performance-dataset)

- **Records:** 5,000 synthetic student samples
- **Target variable:** `exam_score`

### Features

The dataset includes multiple behavioral, academic, and lifestyle indicators:

- Study hours
- Sleep hours
- Social media usage
- Gaming hours
- Mental health score
- Burnout level
- Productivity score
- Academic level
- Internet quality
- Other behavioral indicators

**Data Storage:** The dataset was uploaded into an Azure Blob container and registered as a Data Asset inside Azure ML.

---

## ⚙️ Methodology

### 1️⃣ Data Exploration

- ✅ Verified null values (none present)
- ✅ Checked data types
- ✅ Visualized distribution using boxplot
- ✅ Detected and removed outliers using IQR method (1.5 × IQR)

**Outlier removal impact:**
- Original records: **5,000**
- After IQR cleaning: **4,991**

---

### 2️⃣ Preprocessing Pipeline

A structured **Scikit-Learn pipeline** was created:

- **Categorical encoding:** `OneHotEncoder`
- **Numerical scaling:** `StandardScaler`
- **Target scaling:** `TransformedTargetRegressor`
- **Model:** `LinearRegression`

**Training split:** 70/30 train-test split

---

### 3️⃣ Experiment Tracking

An Azure ML experiment (`StudentPerformanceModel`) was created to log:

- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)
- R² Score

**Additional artifacts logged:**
- Real vs Predicted scatter plot
- Residual distribution analysis

---

## 📈 Results

### Final Logged Metrics

| Metric | Value |
|--------|-------|
| Mean Absolute Error | 3.85 |
| Mean Squared Error | 23.70 |
| Root Mean Squared Error | 4.86 |
| R² Score | 0.8382 |

### Interpretation

- The model explains **~83.8%** of the variance in exam scores
- Average prediction error is approximately **±3.85 points**
- Residual distribution appears approximately centered around zero
- Real vs Predicted plot shows strong linear alignment

**Conclusion:** These results indicate a strong linear relationship between behavioral variables and exam performance.

---

## 📊 Visual Analysis

### Real vs Predicted Plot

- ✅ Predictions closely aligned with the ideal diagonal line
- ⚠️ Slight dispersion at lower score ranges
- ✅ No extreme heteroscedasticity patterns observed

### Residual Distribution

- Approximately normal error distribution

---

## 🧠 Conclusions

1. **Study behavior, productivity, mental health, and burnout are strong predictors** of exam performance
2. The **linear regression model performs well** on this dataset
3. **Removing outliers** slightly improved stability and generalization
4. The **pipeline design allows easy model replacement** (Ridge, Random Forest, etc.)
5. **Azure ML experiment tracking** provides reproducibility and traceability

This demonstrates an **end-to-end regression workflow** using Azure Machine Learning and Scikit-Learn best practices.

---

## 📄 Full Documentation

The complete step-by-step implementation (including Azure setup, pipeline construction, logging, and visualizations) is available in the attached PDF:

📎 **Student Performance Model**

> The PDF can be reviewed in detail for validation of methodology and reproducibility.

---

## 🔄 Reproducibility Notes

- All preprocessing steps are encapsulated in a Scikit-Learn pipeline
- Azure ML experiment logging ensures full traceability
- Data asset versioning allows consistent retraining
- Pipeline architecture supports easy experimentation with alternative models
