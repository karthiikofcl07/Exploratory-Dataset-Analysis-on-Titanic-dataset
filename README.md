# 🚢 Titanic Survival Analysis — Exploratory Data Analysis

<div align="center">

![Python](https://img.shields.io/badge/Python-3.13-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.x-11557c?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-0.x-4c8cbf?style=for-the-badge)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

**A rigorous, production-style Exploratory Data Analysis on the Kaggle Titanic dataset,**  
**uncovering survival patterns through data cleaning, statistical analysis, and visualization.**

[📊 View Notebook](#notebook) · [🔍 Key Findings](#key-findings) · [🛠 Tech Stack](#tech-stack) · [🚀 Quick Start](#quick-start)

</div>

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Dataset Description](#-dataset-description)
- [Project Structure](#-project-structure)
- [Methodology](#-methodology)
- [Key Findings](#-key-findings)
- [Visualizations](#-visualizations)
- [Tech Stack](#-tech-stack)
- [Quick Start](#-quick-start)
- [Results Summary](#-results-summary)
- [Future Scope](#-future-scope)
- [Author](#-author)

---

## 🧭 Project Overview

This project performs a comprehensive **Exploratory Data Analysis (EDA)** on the iconic [Titanic: Machine Learning from Disaster](https://www.kaggle.com/c/titanic) dataset from Kaggle. The goal is to extract meaningful patterns and insights about the factors that influenced passenger survival in the 1912 Titanic disaster.

This analysis demonstrates real-world data science skills including:
- **Data wrangling** and missing value treatment
- **Statistical analysis** and feature profiling
- **Hypothesis-driven visual exploration**
- **Correlation and multivariate analysis**

> 💡 This EDA serves as a strong foundation for downstream predictive modeling and machine learning pipelines.

---

## 💼 Business Problem

> *"Can we determine what socio-demographic factors most influenced a passenger's chance of survival aboard the Titanic?"*

Understanding survival determinants helps organizations model real-world risk scenarios and make data-driven decisions. This analysis answers:

- Did gender significantly impact survival odds?
- Did passenger class (socioeconomic status) play a role?
- How did fare price correlate with survival probability?
- What role did age and family size play?

---

## 📂 Dataset Description

**Source:** [Kaggle — Titanic: Machine Learning from Disaster](https://www.kaggle.com/c/titanic)  
**File used:** `train.csv`  
**Records:** 891 passengers × 12 features

| Feature | Type | Description |
|---|---|---|
| `PassengerId` | int | Unique identifier for each passenger |
| `Survived` | int (0/1) | Survival outcome — **Target Variable** |
| `Pclass` | int (1/2/3) | Ticket class (1 = 1st, 2 = 2nd, 3 = 3rd) |
| `Name` | string | Full name of the passenger |
| `Sex` | categorical | Gender of the passenger |
| `Age` | float | Age in years |
| `SibSp` | int | # of siblings/spouses aboard |
| `Parch` | int | # of parents/children aboard |
| `Ticket` | string | Ticket number |
| `Fare` | float | Passenger fare paid |
| `Cabin` | string | Cabin number (heavily missing) |
| `Embarked` | categorical | Port of embarkation (C / Q / S) |

---

## 🗂 Project Structure

```
titanic-eda/
│
├── 📓 eda.ipynb              # Main analysis notebook
├── 📄 train.csv              # Raw dataset (from Kaggle)
├── 📋 README.md              # Project documentation (this file)
│
└── 📊 outputs/               # Generated visualizations
    ├── survival_by_class.png
    └── correlation_heatmap.png
```

---

## 🔬 Methodology

The analysis follows a structured **5-phase EDA pipeline:**

```
┌─────────────────────────────────────────────────────────────┐
│  Phase 1 │  Data Loading & Initial Inspection               │
│          │  → Shape, dtypes, head/tail, basic stats         │
├─────────────────────────────────────────────────────────────┤
│  Phase 2 │  Missing Value Analysis                          │
│          │  → Identify, quantify, and visualize nulls       │
├─────────────────────────────────────────────────────────────┤
│  Phase 3 │  Data Cleaning & Imputation                      │
│          │  → Age (median), Embarked (mode), drop Cabin     │
├─────────────────────────────────────────────────────────────┤
│  Phase 4 │  Univariate & Bivariate Analysis                 │
│          │  → Survival rate by gender, class, fare, age     │
├─────────────────────────────────────────────────────────────┤
│  Phase 5 │  Correlation Analysis                            │
│          │  → Heatmap, numeric correlations with Survived   │
└─────────────────────────────────────────────────────────────┘
```

### 🧹 Data Cleaning Strategy

| Column | Missing Count | Strategy |
|---|---|---|
| `Age` | 177 (19.9%) | Imputed with **median age** |
| `Cabin` | 687 (77.1%) | **Dropped** — too sparse |
| `Embarked` | 2 (0.2%) | Imputed with **mode ('S')** |

---

## 🔍 Key Findings

### 1. 🚺 Gender Was the Strongest Survival Predictor

| Gender | Survival Rate |
|---|---|
| **Female** | **74.2%** |
| Male | 18.9% |

> Women had **~4× higher survival rate** than men, consistent with the "women and children first" evacuation protocol.

---

### 2. 🎟 Passenger Class Strongly Correlated With Survival

| Class | Survival Rate |
|---|---|
| **1st Class** | **~63%** |
| 2nd Class | ~47% |
| 3rd Class | ~24% |

> There is a **moderate negative correlation (−0.34)** between `Pclass` and `Survived`. Higher-class passengers had significantly better odds.

---

### 3. 💰 Fare Positively Correlated With Survival

- **Correlation:** `+0.26` between `Fare` and `Survived`
- Passengers paying higher fares (typically 1st class) were more likely to survive.
- Reflects the **socioeconomic advantage** in access to lifeboats.

---

### 4. 👶 Age Had Minimal Direct Impact

- Correlation of Age with Survived: **very weak**
- Age was not a strong standalone predictor in this dataset.

---

### 5. 👨‍👩‍👧 Family Variables Were Minimal Predictors

- `SibSp` and `Parch` showed **minimal independent influence** on survival.

---

## 📊 Visualizations

### Survival Rate by Passenger Class
> Bar chart showing clear decline in survival rates from 1st → 3rd class.

### Correlation Heatmap
> Coolwarm heatmap revealing relationships between all numeric features, highlighting `Pclass` and `Fare` as the most correlated variables with survival.

---

## 🛠 Tech Stack

| Tool | Purpose |
|---|---|
| **Python 3.13** | Core programming language |
| **Pandas** | Data manipulation and analysis |
| **NumPy** | Numerical operations |
| **Matplotlib** | Base plotting library |
| **Seaborn** | Statistical data visualization |
| **Jupyter Notebook** | Interactive analysis environment |

---

## 🚀 Quick Start

### Prerequisites

```bash
Python >= 3.8
pip or conda package manager
```

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/your-username/titanic-eda.git
cd titanic-eda

# 2. Create a virtual environment
python -m venv .venv
source .venv/bin/activate      # On Windows: .venv\Scripts\activate

# 3. Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# 4. Download the dataset from Kaggle
#    Place train.csv in the project root

# 5. Launch the notebook
jupyter notebook eda.ipynb
```

---

## 📈 Results Summary

| Analysis Area | Finding | Strength |
|---|---|---|
| Gender vs Survival | Female survival 4× higher | 🔴 Very Strong |
| Class vs Survival | 1st class survival ~2.6× 3rd class | 🔴 Strong |
| Fare vs Survival | Positive correlation (+0.26) | 🟡 Moderate |
| Age vs Survival | Negligible correlation | 🟢 Weak |
| Family Size vs Survival | Minimal impact | 🟢 Weak |

> **Overall survival rate in the dataset: ~38.4%**

---

## 🔮 Future Scope

- [ ] **Feature Engineering** — Extract title from Name, bin Age groups, create FamilySize feature
- [ ] **Advanced Visualization** — Survival by embarkation port, age distribution by class
- [ ] **Machine Learning** — Logistic Regression, Random Forest, XGBoost survival classifiers
- [ ] **Model Evaluation** — Cross-validation, ROC-AUC, precision-recall analysis
- [ ] **Hyperparameter Tuning** — Grid search / Bayesian optimization
- [ ] **Deployment** — Flask/FastAPI REST API for survival prediction

---

## 👤 Author

**Karthikeyan Thirunavukkarasu**  
*Data Science Intern @ Elevvo*

> 📅 Project Date: 10 February 2026

---

<div align="center">

**⭐ If this project helped you, please give it a star!**

</div>
