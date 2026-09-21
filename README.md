# MarketMind: Predicting Ad Performance with Consumer Behavior Data

An end-to-end machine learning project that analyzes consumer engagement with online advertisements and predicts ad performance using demographic and advertising attributes.

## Overview

This project builds a complete workflow for understanding digital ad engagement. It includes:

- data cleaning and preprocessing,
- exploratory data analysis with interactive Plotly visualizations,
- feature engineering,
- a regression model to predict ad clicks,
- a classification model to distinguish high- and low-engagement users.

The goal is to identify the main drivers of ad performance and show how predictive analytics can support digital marketing decisions.

## Dataset

- **Source:** Online Advertisement Click-Through Rates, Mendeley Data
- **DOI:** 10.17632/wrvjmdtjd9.1
- **Contributors:** Jagadish Tawade, Nitiraj Kulkarni

The dataset contains information about how users interact with online advertisements, including:

- user demographics: age, gender, income, and location,
- ad features: type, topic, and placement,
- engagement metrics: clicks, click-through rate, and conversion rate,
- temporal information: click dates, from which day and month features are derived.

**Citation:** Tawade, Jagadish; Kulkarni, Nitiraj (2024). "Dataset: Online Advertisement Click-Through Rates." Mendeley Data, V1. doi:10.17632/wrvjmdtjd9.1

## Data Cleaning and Preprocessing

The dataset was cleaned and prepared using Power BI, Excel, and Python in Google Colab.

### 1. Initial Cleaning (Power BI)

- Removed invalid negative values from `Age` and `Income`
- Standardized missing values by filling numeric columns with the mean and categorical columns with the mode
- Checked for and removed duplicate rows

### 2. Formatting (Excel)

- Standardized numeric formatting for the `Income` field
- Converted `click_date` into datetime format for feature extraction

### 3. Feature Engineering (Python)

- One-hot encoded categorical variables such as `Gender` and `Ad_Type`
- Scaled income values to improve regression model performance
- Extracted `click_day` and `click_month` from `click_date`
- Created interaction terms such as `income_x_clicks` and `ctr_x_conversion`

After preprocessing, the final dataset was reduced to 496 rows and 17 columns before encoding, and 496 rows and 27 columns after one-hot encoding.

## Exploratory Data Analysis

Interactive Plotly charts were used to investigate relationships among demographics, ad attributes, and user engagement.

Key insights included:

- **Income vs. Click Behavior:** Higher-income users tend to click on more ads, with stronger engagement among younger consumers aged 18 to 35 in mid-range income brackets.
- **Feature Correlations:** Click-through rate is strongly associated with income and ad type, while higher conversion rates align with greater clicks per user.
- **Click Trends by Income Group:** Engagement peaks in mid-income segments ($25K to $40K) and declines slightly above $55K.
- **Gender Patterns:** Female consumers show a higher median click rate, while male consumers exhibit more variability in engagement.
- **Temporal Trends:** Conversion rates fluctuate over time, with female consumers showing more stable patterns across months.

## Machine Learning Pipelines

Two Random Forest pipelines were developed and tuned using grid search.

### Regression Model: Predicting Ad Clicks

| Metric | Score |
|--------|-------|
| Mean Squared Error | 0.486 |
| R-squared | 0.7428 |
| Best cross-validated R-squared | 0.7455 |
| Best parameters | max_depth=15, min_samples_leaf=2, n_estimators=300 |

The regression model performed well, with income, age, and ad placement identified as the strongest predictors of ad clicks.

### Classification Model: High vs. Low Engagement

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

```text
[[76  1]
 [15  8]]
```

The classifier was effective at identifying low-engagement users but struggled to predict high-engagement cases, likely due to class imbalance in the dataset.

## Key Findings

- Income, gender, and ad placement have the strongest overall effect on engagement.
- The regression model predicts ad clicks with solid accuracy.
- The classification model is limited by class imbalance in high-engagement cases.

## Future Work

- Add richer feature engineering, including ad interaction history
- Explore boosting and bagging methods to improve classification performance
- Use class-imbalance handling techniques such as resampling or weighted loss functions
- Integrate external datasets to gain deeper insight into consumer behavior trends

## Repository Contents

- `marketmind.ipynb` — full analysis, interactive visualizations, and modeling workflow
- `README.md` — project documentation

## How to Run

1. Clone the repository.
2. Open `marketmind.ipynb` in Jupyter Notebook or Google Colab.
3. Run the cells in order.
4. Install any missing dependencies using:

```bash
pip install pandas numpy scikit-learn plotly matplotlib seaborn
```

## Project Goal

This project demonstrates how consumer behavior data can be transformed into actionable insights for digital marketing optimization, helping to understand which users are most likely to engage with advertisements and which ad characteristics influence performance.

## License

This project is provided for educational and research purposes.
