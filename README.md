# Car Price Predictor — Machine Learning Model for Used Vehicles

This repository contains a complete Machine Learning workflow for predicting the selling price of used vehicles.  
It is based on a dataset of more than **370,000 real car listings** collected through web scraping and later cleaned to **~270,000 high-quality samples**.  
The work includes data engineering, exploratory data analysis, model evaluation, and final deployment of the best-performing model.

The full methodology is detailed in the included PDF report  
**“Predicción de precio en venta de vehículos aplicando Machine Learning”** :contentReference[oaicite:1]{index=1}.

---

## 1. Project Overview

The goal is straightforward: **build a reliable model capable of estimating the market value of used cars** based on attributes such as:

- Brand & model  
- Mileage  
- Power (converted from PS to CV)  
- Age  
- Fuel type  
- Gearbox  
- Damage status  

This model aims to help buyers and sellers understand fair pricing for vehicles in the second-hand market.

---

## 2. Dataset

Source: Web-scraped listings from a public data repository (Data.world).  
The raw dataset initially contained **370k samples**, with text primarily in German.

### Data preprocessing steps (summarized from the report):
- Translation of categorical fields
- Outlier removal:
  - Prices limited to 300€–70,000€
  - Year of registration restricted to 1973–2019
  - Power limited to 50–400 CV
- Removal of >50k rows with missing values
- Creation of new features:
  - `Edad` (vehicle age)
- Conversion:
  - `PS → CV`
- Encoding categorical attributes (Label Encoding)

Final dataset size: **~270,000 samples**

Details and visuals are documented in the PDF report (pages 1–6). :contentReference[oaicite:2]{index=2}

---

## 3. Exploratory Data Analysis

The notebooks include visual analysis covering:

- Price distribution
- Mileage vs. price correlation
- Brand & model impact
- Power vs. price
- Gearbox and fuel type patterns
- Effect of damages

Examples of findings:
- Mileage and age reduce price in a predictable way.
- Brand/model strongly influence value (see figures 7 and 8 in the report). :contentReference[oaicite:3]{index=3}
- High-power cars show more variance in price.
- Automatic gearbox increases estimated value.
- Fuel type displayed weak impact due to dataset imbalance.

---

## 4. Model Development

Several models were compared:

### **Linear Models**
- Linear Regression  
- Ridge Regression  
- Lasso Regression  

These reached **R² ≈ 0.65** and showed clear limitations.

### **Non-Linear Models**
- Kernel Ridge Regression  
- Gradient Boosting Regressor  
- Random Forest Regressor  

Results from the report (pages 7–9):  
- Kernel Ridge: **R² = 0.84**  
- Gradient Boosting: **R² = 0.89**  
- **Random Forest: R² = 0.91, RMSE ≈ 2043€, Median AE ≈ 638€**

Based on accuracy and robustness, **Random Forest is the final chosen model**.

Figures 15 and 18 in the report highlight its predictive performance and feature importance.



