### 🏙️ London Housing Price Model (2023–2024)

**A full end-to-end data science project on London’s housing market — from raw data to business insights.**

<img width="960" height="640" alt="image" src="https://github.com/user-attachments/assets/8b12692a-271c-41fe-a888-5b593c2ecaaf" />


London’s property market is famously unpredictable. Prices can jump dramatically within just a few streets, and traditional metrics like “number of bedrooms” often fail to explain why two similar homes sell for very different prices.

In this project, I set out to answer a practical business question:

> **What actually drives house prices in London today — and can we model it reliably at scale?**

To answer this, I built a complete data pipeline using **~200,000 real London property listings**, applied thoughtful **feature engineering**, and compared **OLS, Ridge, Lasso, and ElasticNet regression models** to balance interpretability, stability, and predictive power.

This repository showcases how I approach **real-world data problems**: cleaning messy datasets, engineering meaningful features, validating models properly, and translating results into **clear business insights**.

---

## 📊 Dataset Overview

- **Source:** Kaggle — *London House Price Data*  
- **Coverage:** ~418,000 records (1995–2024)  
- **Final modeling window:** **2023–2024 only**
- **Key attributes:**  
  - Location (postcode, latitude, longitude)  
  - Property characteristics (size, bedrooms, bathrooms, tenure, energy rating)  
  - Sale price estimates and historical transaction data  

### Why I Focused on 2023–2024

London prices from the 1990s or early 2000s no longer reflect today’s market reality. Including them would bias the model and weaken business relevance.

So I:
- Extracted the sale year
- Filtered the dataset down to **recent transactions only**
- Reduced noise while keeping **~197,000 high-quality records**

This ensures the model learns **modern buyer behavior**, not outdated price dynamics.

---

## 🧹 Data Cleaning & Preparation

Working with a large real-world dataset means dealing with missing, inconsistent, and irrelevant data.

### What I Did

- **Dropped irrelevant features** (e.g. rent estimates when predicting sale prices)
- **Handled missing values strategically**:
  - Numeric features → filled with medians
  - Categorical features → filled with mode
- **Removed overly sparse variables** (≈40% missing)
- Verified **no duplicate records**

📌 Result:  
A clean, modeling-ready dataset with **197,000+ rows and zero missing values**.

---

## 🔍 Exploratory Data Analysis (EDA)

EDA helped translate raw data into intuition.

### Key Observations

- **Most London homes sell between £0.4 and £0.9 million**
- A small number of **multi-million-pound properties** create strong right-skew
- Clear price tiering by **property type**
- Strong postcode-driven price clustering
<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/1f578841-0bbb-4540-a745-a9fa5e48d0ac" />
### Notable Insights

- Flats dominate the lower price bands
- Detached and semi-detached homes occupy premium tiers
- Central London outcodes (e.g. SW1X, W1K, W8) command **2–4× higher prices**

These insights directly informed later feature engineering and modeling choices.
<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/bf91496b-ec6b-4465-bafd-870f61c8d317" />
<img width="859" height="545" alt="image" src="https://github.com/user-attachments/assets/40b5b842-9d38-45d0-8712-37f59ca7f2b6" />




---

## 🧠 Feature Engineering

Instead of relying only on raw columns, I engineered features that reflect **how buyers think**.

### Key Engineered Features

- **beds_per_sqm**  
  Captures space efficiency — small, dense flats often trade at a premium.

- **baths_per_sqm**  
  Extra bathrooms in limited space often signal luxury.

- **area_sq (floorArea²)**  
  Allows the model to learn **diminishing returns** on very large homes.

- **dist_center_km**  
  Straight-line distance from Charing Cross — a strong proxy for the “Central London premium”.

- **Energy rating (ordinal encoding)**  
  Turns EPC ratings into an ordered efficiency signal.



📌 These features significantly improved model stability and interpretability.

---

## 🤖 Modeling Approach

I framed this as a **regression problem**, predicting **log(price)** to handle skew and outliers.

### Models Tested

- **OLS (Baseline)**
- **Ridge Regression (Regularized)**
- **Lasso Regression**
- **ElasticNet**

### Validation Strategy

- **5-fold cross-validation**
- **Hold-out test set**

**Metrics:**
- R² (explained variance)
- MAE (mean absolute error, in £)

---

## 📈 Model Performance 

| Model | Test R² | Test MAE (£) | Notes |
|------|--------|-------------|------|
| **OLS** | ~0.84 | ~£156k | Strong but multicollinearity present |
| **Ridge (Final)** | **0.83** | **£163k** | Best balance of accuracy & stability |
| Lasso | ~0.79 | £188k | Too aggressive, lost signal |
| ElasticNet | ~0.83 | £165k | Behaves like Ridge |

📌 **Ridge regression performed best overall**, maintaining high accuracy while handling correlated features gracefully.

---

## 📌 Business Insights 

This model isn’t just accurate — it tells a clear story:

- 📐 **Floor area is the strongest price driver**
- 🚿 **Bathrooms add value beyond size**
- 📍 **Every 1 km closer to Charing Cross ≈ ~5% higher price**
- 🏢 **Flats consistently underperform houses**
- 🏙️ **Prime postcodes can double prices**
- 📉 **Very large homes show diminishing returns**

  <img width="589" height="390" alt="image" src="https://github.com/user-attachments/assets/4df28de7-c2f3-475f-aca1-5becf7398739" />
  <img width="581" height="453" alt="image" src="https://github.com/user-attachments/assets/ddc67f8d-7ece-4e54-8296-289ad1e02228" />


These insights can directly inform:
- Pricing strategy
- Investment decisions
- Location-based forecasting
- Policy and urban planning analysis

---

## 🧪 Diagnostics & Model Reliability

I validated assumptions thoroughly:

- Residuals show **no systematic bias**
- Errors remain stable across price ranges
- Q–Q plots show near-normal residuals
- No signs of overfitting

<img width="1189" height="490" alt="image" src="https://github.com/user-attachments/assets/17887b66-96ee-4e30-a583-0a2b607974b5" />

This is a **production-ready modeling approach**, not just a notebook experiment.

---

## 🎯 Why This Project Matters

This project demonstrates my ability to:

- ✅ Work with **large, messy datasets**
- ✅ Engineer **domain-driven features**
- ✅ Apply **statistical rigor**
- ✅ Compare and justify **model choices**
- ✅ Translate results into **business insights**

If you’re looking for someone who can **bridge data science and decision-making**, this project reflects exactly how I work.

---

## ▶️ Reproduce or Extend

- Clone the repository
- Run the Jupyter notebook
- All charts, tables, and models are fully reproducible

Feel free to fork, explore, or build on it.

---

### 👋 About Me

I’m an MSc Data Science graduate with a strong interest in **applied machine learning, analytics, and real-world decision modeling**.  
I enjoy turning complex datasets into **clear, actionable insights**.

📬 *Happy to discuss this project or walk through the modeling decisions in an interview.*
