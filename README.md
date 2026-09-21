# ⚾ MLB StatCast Analytics: Predicting Batted Ball Distance

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange.svg)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An end-to-end machine learning project utilizing MLB StatCast metrics to predict player-season average batted ball distance (`dist_avg`) using Multi-Linear Regression.

---

## 📌 Executive Summary

Quantifying how mechanical swing inputs translate into power output is vital for talent evaluation, scouting, and player development in modern Major League Baseball (MLB). 

Using aggregated StatCast data across **1,918 player-seasons** (filtered for $\text{BBE} > 100$), this project fits a Multi-Linear Regression model to evaluate the marginal impact of Exit Velocity, Launch Angle, Barrel %, and Hard-Hit % on average batted ball distance.

### Key Metrics & Results
* **$R^2$ Score:** `0.7892` (Exceeded target of $> 0.70$) — Explains ~79% of variance in seasonal average distance.
* **RMSE:** `9.53 feet` — Highlights remaining variance driven by non-linear aerodynamics and stadium environments.

---

## 📊 Feature Importance & Marginal Impact

```text
Linear Regression Feature Coefficients:
-------------------------------------------------------
ev_avg                          : +3.32 ft / mph
la_avg                          : +3.22 ft / degree
barrels_batted_balls_percentage : +1.12 ft / %
hard_hit_percentage             : -0.66 ft / %
-------------------------------------------------------
```
### Core Analytical Insights
1. **Exit Velocity vs. Launch Angle:** Holding other features constant, a $1\text{ mph}$ increase in average Exit Velocity increases distance by **$3.32\text{ ft}$**, while a $1^\circ$ increase in average Launch Angle adds **$3.22\text{ ft}$**.
2. **The Hard-Hit Paradox:** Controlling for `barrels_batted_balls_percentage`, raw `hard_hit_percentage` exhibits a negative coefficient ($-0.66\text{ ft}$). Hard contact hit at suboptimal launch angles (e.g., hard ground balls) suppresses total average distance.

---

## 🛠️ Project Architecture & Workflow

[Raw StatCast Data] ➔ [Data Filtering (BBE > 100)] ➔ [Mean Imputation] ➔ [80/20 Train-Test Split] ➔ [Scikit-Learn Regression] ➔ [Model Evaluation & XAI]

### Tech Stack
* **Language:** Python
* **Data Processing & EDA:** Pandas, NumPy, Seaborn, Matplotlib
* **Machine Learning:** Scikit-Learn (`LinearRegression`, `train_test_split`, `metrics`)

---

## 💡 Key Lessons Learned & Future Work

* Data Granularity Dictates Model Selection: An initial plan to use XGBoost to classify individual home runs was pivoted to Multi-Linear Regression upon recognizing that the dataset consisted of season-level averages rather than pitch-by-pitch event data.
* Future Work: Ingest pitch-level StatCast events (spray angle, pitch velocity, park factors) to build non-linear gradient-boosted classification models for discrete outcomes $(P(HR))$.
