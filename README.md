# MarketMind

<div align="center">
  <img src="https://img.shields.io/badge/ML-%20Random%20Forest-blueviolet" alt="Machine Learning" />
  <img src="https://img.shields.io/badge/Data-Analysis-orange" alt="Data Analysis" />
  <img src="https://img.shields.io/badge/Focus-Marketing%20Analytics-00BFA5" alt="Marketing Analytics" />
</div>

Predicting ad performance with consumer behavior data using machine learning and exploratory analysis.

## Overview

MarketMind is a data-driven machine learning project designed to understand how consumers engage with online advertisements and predict which ad characteristics and user attributes influence performance. The workflow combines data cleaning, feature engineering, exploratory data analysis, and predictive modeling to uncover patterns in digital marketing behavior.

The project includes:

- data preprocessing and feature engineering,
- interactive visual analysis with Plotly,
- a regression model to predict the number of ad clicks,
- a classification model to separate high- and low-engagement users,
- clear business insight generation for digital marketing strategy.

## Why This Project Matters

In digital advertising, understanding engagement is essential for improving targeting, campaign efficiency, and return on investment. This project demonstrates how data science can turn consumer behavior data into actionable insights and predictive models that support strategic marketing decisions.

## Dataset

- Source: Online Advertisement Click-Through Rates, Mendeley Data
- DOI: 10.17632/wrvjmdtjd9.1
- Contributors: Jagadish Tawade, Nitiraj Kulkarni

The dataset contains information on how users interact with online advertisements, including:

- user demographics: age, gender, income, and location,
- ad attributes: type, topic, and placement,
- engagement metrics: clicks, click-through rate, and conversion rate,
- temporal context: click dates used to derive day and month features.

**Citation:** Tawade, Jagadish; Kulkarni, Nitiraj (2024). "Dataset: Online Advertisement Click-Through Rates." Mendeley Data, V1. doi:10.17632/wrvjmdtjd9.1

## Data Cleaning and Preprocessing

The dataset was prepared using Power BI, Excel, and Python in Google Colab.

### Initial Cleaning (Power BI)

- Removed invalid negative values from `Age` and `Income`
- Filled missing numeric values with the mean and categorical values with the mode
- Checked for duplicate records and removed invalid entries

### Formatting (Excel)

- Standardized numeric formatting for the `Income` column
- Converted `click_date` into datetime format for feature extraction

### Feature Engineering (Python)

- One-hot encoded categorical variables such as `Gender` and `Ad_Type`
- Scaled income values to improve model training
- Extracted `click_day` and `click_month` from `click_date`
- Created interaction features such as `income_x_clicks` and `ctr_x_conversion`

After preprocessing, the data had a final shape of `(496, 17)` before encoding and `(496, 27)` after one-hot encoding.

## Exploratory Data Analysis

Interactive Plotly visualizations were used to explore relationships among user demographics, ad attributes, and engagement metrics.

Key findings included:

- **Income vs. click behavior:** Higher-income users tended to click more often, with strong engagement among younger consumers aged 18–35 in mid-range income brackets.
- **Feature correlations:** Click-through rate was associated with income and ad type, while higher conversion rates aligned with stronger user engagement.
- **Income-group trends:** Engagement peaked in the $25K–$40K range and declined slightly above $55K.
- **Gender patterns:** Female consumers showed a higher median click rate, while male consumers exhibited greater variability.
- **Temporal trends:** Conversion rates fluctuated seasonally, with relatively stable patterns among female users.

## Machine Learning Pipelines

Two Random Forest pipelines were developed and tuned using grid search.

### Regression Model: Predicting Ad Clicks

| Metric | Score |
|--------|-------|
| Mean Squared Error | 0.486 |
| R-squared | 0.7428 |
| Best cross-validated R-squared | 0.7455 |
| Best parameters | max_depth=15, min_samples_leaf=2, n_estimators=300 |

The regression model performed well, with income, age, and ad placement emerging as the most influential predictors of ad clicks.

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

The classification model was strong at identifying low-engagement users but struggled to detect high-engagement cases, most likely due to class imbalance in the dataset.

## Key Findings

- Income, gender, and ad placement had the strongest effect on engagement.
- The regression model accurately predicts ad clicks with solid performance.
- The classification model is promising but limited by imbalance in the high-engagement class.

## Future Work

- Improve feature engineering by incorporating ad interaction history
- Explore boosting and bagging methods to improve classification performance
- Apply class-imbalance strategies such as resampling or weighted loss functions
- Integrate external datasets for deeper insight into consumer behavior trends

## Repository Contents

- `marketmind.ipynb` — full analysis, interactive visualizations, and modeling workflow
- `README.md` — project documentation

## How to Run

1. Clone the repository.
2. Open `marketmind.ipynb` in Jupyter Notebook or Google Colab.
3. Run the cells in order.
4. Install the required dependencies:

```bash
pip install pandas numpy scikit-learn plotly matplotlib seaborn
```

## Project Goal

This project demonstrates how consumer behavior data can be translated into actionable insights for digital marketing optimization. By identifying the most influential drivers of engagement and building reliable prediction models, the work supports more informed ad targeting and campaign strategy.

## License

This project is intended for educational and research purposes.
