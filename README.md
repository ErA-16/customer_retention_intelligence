# 🧠 Customer Retention Intelligence System

A full end-to-end machine learning system that goes beyond predicting churn —
it identifies **who** will leave, **why**, **when**, and **what action** will most likely stop them.

---

## 📌 Problem Statement

Most churn prediction projects stop at a binary prediction — will this customer leave or not?

This system takes it further by combining risk scoring, behavioral profiling, urgency estimation,
and a decision engine to recommend specific retention actions for each at-risk customer.

---

## 📦 Dataset

**E-Commerce Customer Churn Dataset**  
Source: Kaggle  
Size: 5,630 customers · 20 features  

Key features used:
- `Tenure` — how long the customer has been with the platform
- `Complain` — whether the customer raised a complaint
- `SatisfactionScore` — customer satisfaction rating
- `DaySinceLastOrder` — days since their last purchase
- `CashbackAmount` — cashback received
- `Churn` — target variable (1 = churned, 0 = stayed)

---

## 🏗️ System Architecture

```
Raw Data
   ↓
Phase 1 — Data Preparation
   ↓
Phase 2 — Risk Model       → Who will churn? (XGBoost → P(churn) score)
   ↓
Phase 3 — Behavior Profile → Why will they churn? (Frustrated / Inactive / Price-Sensitive)
   ↓
Phase 4 — Urgency          → When will they churn? (Immediate / Soon / Monitor)
   ↓
Phase 5 — Decision Engine  → What action to take? (Support Call / Discount / Re-engagement)
   ↓
Phase 6 — Simulation       → What actually works? (Simulated A/B retention outcomes)
```

---

## 🤖 Model

| Model | Accuracy | Churn Recall | Churn Precision |
|---|---|---|---|
| Logistic Regression | 79% | 0.82 | 0.44 |
| **XGBoost** | **98%** | **0.97** | **0.94** |

XGBoost selected as the final model.  
Class imbalance handled using `scale_pos_weight=5`.

---

## ⚡ Decision Logic

| Behavior | Urgency | Action |
|---|---|---|
| Frustrated | Immediate | Support Call Today |
| Frustrated | Soon | Apology Email + Support |
| Price Sensitive | Immediate | Discount Offer |
| Inactive | Immediate | Re-engagement Campaign |
| Inactive | Soon | Personalized Recommendation |
| Unknown | Any | General Retention Offer |

---

## 🧪 Simulation Results

| Action | Retention Rate |
|---|---|
| Support Call Today | ~81% |
| Personalized Recommendation | ~65% |
| Re-engagement Campaign | ~68% |
| Discount Offer | ~60% |
| General Retention Offer | ~15% |

**Key finding:** Direct human contact (support calls) outperforms generic offers significantly.

---

## 🚀 How to Run

1. Clone the repository
2. Install dependencies:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost joblib openpyxl
```
3. Place `E Commerce Dataset.xlsx` in the `data/` folder
4. Open and run `customer_retention_intelligence.ipynb`

---

## 📁 Project Structure

```
customer_retention_intelligence/
├── data/
│   └── E Commerce Dataset.xlsx
├── customer_retention_intelligence.ipynb
├── churn_model.pkl
└── README.md
```

---

## 🛠️ Tech Stack

- Python 3
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Matplotlib, Seaborn
- Joblib
