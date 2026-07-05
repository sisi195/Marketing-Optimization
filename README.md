# MarketMind: Predicting Ad Performance with Consumer Behavior Data

An end-to-end machine learning pipeline that analyzes how consumers engage with
online advertisements and predicts ad performance from user demographics and ad
attributes.

## Overview

This project builds a complete workflow for understanding and predicting digital
ad engagement. It covers data cleaning, exploratory data analysis with
interactive Plotly visualizations, and two supervised machine learning pipelines:
one to predict the number of ad clicks and one to classify users into high or low
engagement. The goal is to identify the drivers of ad performance and demonstrate
how predictive modeling can support digital marketing decisions.

## Dataset

- **Source:** Online Advertisement Click-Through Rates, Mendeley Data
- **DOI:** 10.17632/wrvjmdtjd9.1
- **Contributors:** Jagadish Tawade, Nitiraj Kulkarni

The dataset describes how users interact with online ads and includes:

- User demographics: age, gender, income, and location
- Ad characteristics: ad type, topic, and placement
- Engagement metrics: clicks per user, click-through rates, and conversion rates
- Temporal context: click dates, from which day and month features are derived

**Citation:** Tawade, Jagadish; Kulkarni, Nitiraj (2024). "Dataset: Online
Advertisement Click-Through Rates." Mendeley Data, V1. doi:10.17632/wrvjmdtjd9.1

## Data Cleaning and Preprocessing

Data was prepared using Power BI, Excel, and Python in Google Colab.

### Initial Cleaning (Power BI)

- Removed negative values from `Age` and `Income` to eliminate invalid entries
- Standardized missing data: numeric fields filled with the mean, categorical
  fields filled with the mode
- Checked for and removed duplicate records

### Formatting (Excel)

- Standardized numerical formatting for the `Income` column
- Converted `click_date` into datetime format for feature extraction

### Feature Engineering (Python)

- One-hot encoded categorical features such as `Gender` and `Ad_Type`
- Scaled income to improve regression performance
- Extracted `click_day` and `click_month` from `click_date`
- Created interaction terms (`income_x_clicks`, `ctr_x_conversion`)

Final dataset shape after removing leaky features: `(496, 17)`. Final shape after
one-hot encoding: `(496, 27)`.

## Exploratory Data Analysis

Interactive Plotly charts were used to examine the relationships between
demographics, ad attributes, and engagement.

- **Income vs. click behavior:** Higher-income users tend to click on more ads,
  with the strongest engagement among younger consumers (ages 18 to 35) in
  mid-range income brackets.
- **Feature correlations:** Click-through rates correlate with income and ad
  type; higher conversion rates align with higher clicks per user.
- **Click rates by income group:** Engagement peaks in mid-income groups
  ($25K to $40K) and declines slightly above $55K.
- **Click behavior by gender:** Female consumers show higher median click rates,
  while male consumers show greater variability.
- **Conversion rate over time:** Conversion rates fluctuate seasonally, with
  female consumers showing more stable conversion patterns.

## Machine Learning Pipelines

Two Random Forest pipelines were built and tuned with grid search.

### Regression: Predicting Ad Clicks

| Metric | Score |
|--------|-------|
| Mean Squared Error | 0.486 |
| R-squared | 0.7428 |
| Best cross-validated R-squared | 0.7455 |
| Best parameters | max_depth=15, min_samples_leaf=2, n_estimators=300 |

Income, age, and ad placement were the strongest predictors of ad clicks.

### Classification: High vs. Low Engagement

| Metric | Score |
|--------|-------|
| Accuracy | 0.84 |
| F1 Score | 0.50 |

**Classification report**

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0 (Low clicks) | 0.84 | 0.99 | 0.90 | 77 |
| 1 (High clicks) | 0.89 | 0.35 | 0.50 | 23 |

**Confusion matrix**

```
[[76  1]
 [15  8]]
```

The classifier identifies low-engagement users reliably but underpredicts
high-engagement cases due to class imbalance.

## Key Findings

- Income, gender, and ad placement have the strongest effect on engagement.
- The regression model predicts ad clicks with solid accuracy.
- The classification model is limited by class imbalance in high-engagement cases.

## Future Work

- Expand feature engineering to include ad interaction history.
- Apply boosting and bagging methods and class-imbalance handling to improve
  classification.
- Integrate external datasets for a broader view of consumer behavior.

## Repository Contents

- `marketmind.ipynb` — full analysis, visualizations, and modeling notebook
- `README.md` — project documentation

## How to Run

1. Clone the repository.
2. Open `marketmind.ipynb` in Jupyter or Google Colab.
3. Run the cells in order. Install any missing dependencies with `pip install`
   (pandas, numpy, scikit-learn, plotly, matplotlib, seaborn).
