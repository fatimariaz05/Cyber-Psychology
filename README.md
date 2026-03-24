# 🧠 Mental Health Prediction System

**Cyberpsychology — The Confluence of Technology in Mental Resilience**

A machine learning project that predicts an individual's mental health status based on their technology usage habits and lifestyle factors. Built as a semester project for the **Introduction to Data Science** course at the Department of Data Science, **National University of Computer and Emerging Sciences (FAST), Lahore**.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Pipeline](#project-pipeline)
- [Models Implemented](#models-implemented)
- [Results](#results)
- [Tech Stack](#tech-stack)
- [How to Run](#how-to-run)
- [Project Structure](#project-structure)
- [Team](#team)

---

## Overview

Mental health is a critical aspect of human well-being, yet early detection of mental health issues remains a challenge. This project leverages machine learning to predict a person's **Mental Health Status** (Poor / Fair / Good / Excellent) based on behavioral and lifestyle features — primarily centered around technology use patterns.

The dataset comprises **10,000 records** and covers attributes such as stress levels, sleep hours, screen time, gaming hours, and physical activity. Three ML models were trained and compared, with **XGBoost achieving the best accuracy of 95.4%** after feature selection.

---

## Dataset

**File:** `Mental_Health_tech_DataSet.csv`  
**Size:** 10,000 rows × 14 columns  
**Target Variable:** `Mental_Health_Status`

### Features

| Feature | Description | Encoding |
|---|---|---|
| `Age` | Age of the individual | Numeric |
| `Gender` | Gender of the individual | Label Encoded (0/1) |
| `Stress_Level` | Self-reported stress | Low=0, Medium=1, High=2 |
| `Sleep_Hours` | Average daily sleep duration | Numeric |
| `Screen_time_Working_Hours` | Daily screen time for work | Numeric |
| `Social_Media_Usage_Hours` | Daily social media usage | Numeric |
| `Gaming_Hours` | Daily time spent gaming | Numeric |
| `Physical_Activity_Hours` | Daily physical activity | Numeric |
| `Work_Environment_Impact` | Perceived work environment effect | Negative=0, Neutral=1, Positive=2 |
| `Mental_Health_Status` *(target)* | Overall mental health | Poor=0, Fair=1, Good=2, Excellent=3 |

> **No missing values** and **no duplicate records** were found in the dataset.

---

## Project Pipeline

```
Raw Dataset
    │
    ▼
Data Preprocessing
(null check, duplicate check, outlier analysis, encoding)
    │
    ▼
Exploratory Data Analysis
(univariate & bivariate analysis, heatmaps, boxplots, distribution plots)
    │
    ▼
Feature Selection
(model-driven importance — removed Gender & Work_Environment_Impact)
    │
    ▼
Model Training & Evaluation
(Logistic Regression, Random Forest, XGBoost)
    │
    ▼
Final Model: XGBoost (95.4% accuracy)
    │
    ▼
Single-Sample Prediction
```

---

## Models Implemented

### 1. Logistic Regression
- Baseline linear classification model
- Features standardized using `StandardScaler`
- Accuracy (before & after feature selection): **74.13%** — no change

### 2. Random Forest
- Ensemble of decision trees
- Accuracy before feature selection: **91.7%**
- Accuracy after feature selection: **92.2%** *(slight improvement)*

### 3. XGBoost *(Final Model)*
- Gradient boosted decision trees
- Accuracy before feature selection: **94.8%**
- Accuracy after feature selection: **95.4%** *(best performance)*

### Feature Selection

Feature importance was extracted from all three models. Both `Gender` and `Work_Environment_Impact` consistently ranked lowest across all models. Removing them improved XGBoost's accuracy, had a negligible effect on Random Forest, and made no difference to Logistic Regression — confirming their removal was justified.

**Final features used for training:**
`Screen_time_Working_Hours`, `Social_Media_Usage_Hours`, `Gaming_Hours`, `Age`, `Stress_Level`, `Sleep_Hours`, `Physical_Activity_Hours`

---

## Results

| Model | Before Feature Selection | After Feature Selection |
|---|---|---|
| Logistic Regression | 74.13% | 74.13% |
| Random Forest | 91.7% | 92.2% |
| **XGBoost** | 94.8% | **95.4%** ✅ |

XGBoost outperformed all other models in **precision**, **recall**, and **overall accuracy**, and was selected as the final model.

---

## Tech Stack

| Tool / Library | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data loading and manipulation |
| NumPy | Numerical computations |
| Matplotlib & Seaborn | Data visualization |
| Plotly Express | Interactive visualizations |
| Scikit-learn | Preprocessing, Logistic Regression, Random Forest, metrics |
| XGBoost | Final prediction model |
| SciPy | Statistical analysis |
| Jupyter Notebook | Development environment |

---

## How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn xgboost scipy
```

### Steps

1. Clone or download this repository.
2. Place the dataset file `Mental_Health_tech_DataSet.csv` in the same directory as the notebook (or update the file path in Cell 3).
3. Open the notebook:

```bash
jupyter notebook Final_Code.ipynb
```

4. Run all cells in order from top to bottom.

> **Note:** The dataset path in the notebook is currently set to a local Windows path. Update Cell 3 to point to wherever your CSV file is located:
> ```python
> df = pd.read_csv('Mental_Health_tech_DataSet.csv')
> ```

### Making a Prediction

The final cells of the notebook demonstrate a single-sample prediction. You can modify the values to test custom inputs:

```python
sample_data = {
    'Screen_time_Working_Hours': [12],
    'Social_Media_Usage_Hours': [4],
    'Gaming_Hours': [5],
    'Age': [20],
    'Stress_Level': [2],   # 0=Low, 1=Medium, 2=High
    'Sleep_Hours': [2],
    'Physical_Activity_Hours': [0]
}
```

---

## Project Structure

```
├── Final_Code.ipynb             # Main Jupyter Notebook (full pipeline)
├── Mental_Health_tech_DataSet.csv   # Dataset (not included in repo)
├── Cyberpsychology-Report.docx  # Final project report
└── README.md                    # This file
```

---


**Department of Data Science**  
National University of Computer and Emerging Sciences (FAST), Lahore  
**Course:** Introduction to Data Science
