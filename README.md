Tienes razón, los bloques de código dentro del markdown rompen el formato. Aquí está todo en una sola pieza para copiar y pegar:

---

# 🏠 Airbnb Price Prediction — Multiple Linear Regression

[![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3+-orange?style=flat-square&logo=scikit-learn)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter)](https://jupyter.org)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

End-to-end data science project that predicts nightly Airbnb prices across 6 major U.S. cities using a **Multiple Linear Regression** model. Includes full EDA, statistical hypothesis testing, feature engineering, model evaluation, and business-oriented insights.

---

## 📊 Project Overview

| | |
|---|---|
| **Dataset** | 64,056 Airbnb listings — NYC, LA, SF, Chicago, Boston, DC |
| **Target variable** | log_price (log-transformed price per night) |
| **Model** | OLS Multiple Linear Regression |
| **R² (test set)** | 0.536 |
| **MAE** | $58.72 USD |
| **Features** | 15 variables (4 numeric + 11 encoded categorical) |

---

## 🔬 Methodology

### 1. Exploratory Data Analysis
- Descriptive statistics and null value diagnosis
- Distribution analysis with log-price transformation (skewness: 4.29 → 0.51)
- Price analysis by city, room type, and number of bedrooms
- Correlation heatmap and pairplot
- Geographic price distribution maps (NYC, LA, SF, Chicago)
- Feature importance ranking via Pearson correlation and eta²

### 2. Predictive Model

**Data preparation**
- IQR-based outlier removal for continuous variables; absolute bounds for discrete variables
- Median imputation for numerical nulls; coordinate-based row removal
- One-hot encoding for room_type, city, and cancellation_policy

**Hypothesis testing** *(before model training)*
- Welch t-test: Entire home/apt vs. Private room → t = 187.16, p ≈ 0.00 ✓
- One-way ANOVA: price differences across 6 cities → F = 572.07, p ≈ 0.00 ✓

**Feature selection**
- Excluded beds (multicollinearity with accommodates, r = 0.81)
- Excluded latitude/longitude (severe multicollinearity with city dummies, Condition No. > 85k)
- Excluded number_of_reviews (near-zero correlation, r = -0.03)
- VIF check: all selected features VIF < 5 ✓

**Model training**
- Train/test split: 80/20 (50,636 / 12,659 observations)
- OLS via statsmodels for statistical summary + scikit-learn for predictions
- No overfitting: R² train = 0.537, R² test = 0.536

---

## 📈 Key Results

| Metric | Value |
|---|---|
| R² (test) | 0.536 |
| MSE (log_price) | 0.2282 |
| RMSE (log_price) | 0.4777 |
| MAE (USD) | $58.72 |
| RMSE (USD) | $127.38 |

### Top predictors by coefficient magnitude

| Variable | Coefficient | Price impact |
|---|---|---|
| room_type: Shared room | −1.056 | −65.2% vs entire home |
| cancellation: super_strict_60 | +0.834 | +130.3% (luxury segment) |
| room_type: Private room | −0.613 | −45.8% vs entire home |
| city: SF | +0.290 | +33.6% vs Boston |
| city: Chicago | −0.310 | −26.7% vs Boston |
| accommodates | +0.075 | +7.8% per additional guest |

### Key business insights
- **The strongest numerical predictor is guest capacity** (accommodates, r = 0.57). Hosts maximizing property capacity can significantly increase revenue.
- **Room type is the most critical categorical driver** (eta² = 0.37). Offering the entire space vs. a private room increases estimated price by ~80%.
- **City-level market differences are statistically significant** (ANOVA F = 572.07). SF is the most expensive market; Chicago the most accessible.
- **Ratings have minimal price impact** (r = 0.09). The market does not consistently reward higher-rated listings with higher prices.

---

## 🛠 Tech Stack

pandas · numpy · matplotlib · seaborn · scikit-learn · statsmodels · scipy

---

## 🚀 Getting Started

Clone the repo, install dependencies with pip install pandas numpy matplotlib seaborn scikit-learn statsmodels scipy, download the dataset from Kaggle (link in References) and place it as Base_de_datos_Proyecto.csv in the root folder, then open the notebooks in order: EDA first, then the final project.

---

## 📁 Notebooks

| Notebook | Description |
|---|---|
| EDA_Proyecto.ipynb | Exploratory analysis: distributions, correlations, geographic maps, feature importance |
| Proyecto_Final_v6.ipynb | Full ML pipeline: cleaning, hypothesis testing, model training, evaluation, predictions |

---

## 🔮 Future Improvements

- Non-linear models: Random Forest / Gradient Boosting to capture interaction effects (expected R² > 0.75)
- NLP on amenities field: binary feature extraction (pool, parking, kitchen)
- Neighbourhood granularity: intra-city location features to capture neighborhood price gradients
- Ridge Regression: address residual multicollinearity (Condition No. = 6,760)

---

## 📚 References

- Tecmilenio. (2024). *Ciencia de datos* [Online course]. Universidad Tecmilenio. https://cursos.tecmilenio.mx/courses/234450
- Airbnb. (2017). *Airbnb listings data* [Dataset]. Kaggle. https://www.kaggle.com/datasets/stevezhenghp/airbnb-price-prediction

---

## 👤 Author

**Gerardo Olivares**
Software Engineering student @ Tecmilenio
[GitHub](https://github.com/gerardo-olivares)

*Built as the final project for the Data Science course at Universidad Tecmilenio.*
