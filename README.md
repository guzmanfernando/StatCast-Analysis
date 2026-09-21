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
