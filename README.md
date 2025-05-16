# MarketMind: Machine Learning for Marketing Optimization

# Final Analysis and Conclusions  
**Sierra Gordon**  
*Date: 5/15/25*

---

## Abstract

In this analysis, I aimed to understand the factors driving consumer ad clicks and conversions. Using a rich dataset that includes consumer demographic, behavioral, and ad-related features, I developed predictive models to forecast ad clicks and classify conversion behavior. The regression approach proved highly effective—explaining nearly 97% of the variability in ad clicks—while the classification task highlighted challenges in accurately identifying high-conversion cases. This report details the entire pipeline, from data cleaning and exploratory visualizations to model building and evaluation, and concludes with insights and recommendations for future work.

---

## 1. Introduction

In today's digital marketing landscape, accurately predicting ad performance is critical. My research focused on these key questions:

1. **What factors influence consumer clicks and conversions?**
2. **Which factors drive conversions the most?**
3. **How do demographics affect ad performance?**
4. **Can we predict the number of ad clicks using consumer demographic, behavioral, and ad-related features?**

I set out to answer these questions by exploring the data in depth, creating insightful visualizations, and building both regression and classification models. 

---

## 2. Data Exploration and Preprocessing

### Data Loading & Cleaning
I began by loading the raw consumer data from a CSV file. To avoid including non-predictive or leaky features, I dropped variables such as `click_date`, `conversion_rate`, `ctr_x_conversion`, and `estimated_roi`. Missing values were handled by filling numeric features with their mean and categorical features with the mode. After these steps, the resulting data had:
- **Shape after dropping leaky features:** (496, 17)
- **Features shape after one-hot encoding:** (496, 27)

### Feature Engineering
A key step was to create an additional categorical variable for age by binning it into groups: 18–25, 25–35, 35–45, 45–55, and 55+. This not only helped with visualizing age-specific trends but also enriched the feature set for modeling.

---

## 3. Exploratory Data Analysis and Visualizations

### Age Binning and Distribution
I created the `age_binned` column using `pd.cut()` to group ages. This allowed me to observe the distribution of consumers across different age ranges.

**Figure 1: Age Distribution by Bins**  
*Interactive graph from Colab:*  
![Age Binned Distribution](path/to/age_binned_plot.png)  
*Hover over for additional details.*

### Conversion Rate by Age and Gender
Using interactive box plots, I visualized conversion rate distributions by age group and gender (female = pink, male = blue). These plots revealed differences in conversion spread across different demographic groups.

**Figure 2: Conversion Rate Distribution by Age Group and Gender**  
![Conversion Rate Box Plot](path/to/box_plot.png)

Additionally, a bar chart comparing average conversion rates by gender helped to clarify overall differences between males and females.

**Figure 3: Average Conversion Rate by Gender**  
![Conversion Rate Bar Chart](path/to/bar_chart.png)

### Correlation Heatmap
I generated a correlation heatmap for continuous variables (age, clicks, conversion rate, income_scaled) to examine inter-variable relationships. This visualization helped me assess potential multicollinearity and understand which features may be strongly associated.

**Figure 4: Correlation Heatmap**  
![Correlation Heatmap](path/to/heatmap.png)

---

## 4. Modeling and Evaluation

### Regression Analysis: Predicting Ad Clicks

#### Model Development
I built a Random Forest Regressor to predict the number of ad clicks. After a preliminary (baseline) model achieved a Test R² of around 0.75, I used GridSearchCV to fine-tune the model. With the best parameters (`{'max_depth': None, 'min_samples_leaf': 1, 'n_estimators': 300}`), the model's performance improved dramatically:
- **Test R² (Tuned Model):** ~0.97  
- **Test MSE:** ~0.06

#### Residual Analysis
To validate the regression model further, I examined the residuals (actual – predicted). The **Residuals vs. Predicted** plot shows that the errors are tightly clustered around zero, and the distribution of residuals (via a histogram with a KDE overlay) is near-normal.

**Figure 5: Residuals vs. Predicted Values**  
![Residuals vs. Predicted Plot](path/to/residuals_plot.png)

**Figure 6: Distribution of Residuals**  
![Residual Distribution Plot](path/to/residual_histogram.png)

*Interpretation:*  
These visualizations confirm that the regression model is performing very well, with minimal and randomly scattered errors.

---

### Classification Analysis: High vs. Low Conversions

#### Model Development
For classification, I converted the continuous click values into a binary target—classifying consumers into “high” or “low” conversion groups based on the median number of clicks. A Random Forest Classifier was then trained on this data. The classifier achieved:
- **Test Accuracy:** 77%
- **Test F1 Score:** ~0.34

The confusion matrix indicates that while the model correctly classifies negatives (low clicks), it struggles with the positive class (high clicks).

**Figure 7: Confusion Matrix**  
