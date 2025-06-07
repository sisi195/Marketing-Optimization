# MarketMind: Predicting Ad Performance with Consumer Behavior Data

## Overview

In this project, I built an end-to-end pipeline to analyze and predict consumer engagement with online advertisements. By cleaning a rich dataset, performing exploratory data analysis (EDA) with interactive Plotly charts, and developing machine learning pipelines, I explored the complex relationships between user demographics, ad attributes, and engagement metrics (clicks and conversion rates). This analysis not only unveiled insights into the drivers of ad performance but also set the stage for predictive modeling to optimize digital marketing strategies.

## Dataset

**Dataset:** [Online Advertisement Click-Through Rates][(https://data.mendeley.com/datasets/wrvjmdtjd9/1)]  
**DOI:** [10.17632/wrvjmdtjd9.1][(http://dx.doi.org/10.17632/wrvjmdtjd9.1)]  
   
**Contributors:** Jagadish Tawade, Nitiraj Kulkarni

**Description:**  
This dataset offers a comprehensive view of how users interact with online ads. It includes:
- User demographics: age, gender, income, and location.
- Ad characteristics: ad type, topic, and placement.
- Engagement metrics: clicks per user, click-through rates, and conversion rates.
- Temporal context: click dates (from which features like day and month are extracted).

This wealth of data is crucial for understanding user behavior and optimizing ad targeting strategies.

**Citation:**  
Tawade, Jagadish; Kulkarni, Nitiraj (2024). “Dataset: Online Advertisement Click-Through Rates”. Mendeley Data, V1. doi:10.17632/wrvjmdtjd9.1

## Data Exploration and Preprocessing

### Data Cleaning & Preprocessing

I cleaned and prepared the dataset using **Power BI, Excel, and Google Colab** to ensure accuracy and consistency before modeling.

#### **Power BI: Initial Cleaning**
- Removed **negative values** from `Age` and `Income` to eliminate unrealistic entries.
- Standardized missing data:
  - **Numeric fields:** Filled with the mean.
  - **Categorical fields:** Filled with the mode.
- Checked for duplicate entries and ensured data integrity.

#### **Excel: Data Formatting**
- Adjusted financial columns (`Income`) to ensure proper numerical formatting.
- Converted date fields (`click_date`) into **datetime format** for feature extraction.

#### **Google Colab: Final Preprocessing**
- **One-hot encoded categorical features** (e.g., `Gender`, `Ad_Type`) to make them machine-readable.
- **Scaled income** to improve regression model performance.
- Created additional features:
  - Extracted `click_day` and `click_month` from `click_date` for temporal analysis.
  - Generated interaction terms (`income_x_clicks`, `ctr_x_conversion`) to better understand relationships between variables.

After completing these steps, the dataset had:
- **Shape after removing leaky features:** `(496, 17)`
- **Shape after one-hot encoding categorical features:** `(496, 27)`

- ## **Exploratory Data Analysis (EDA)**  
To understand **consumer engagement with online advertisements**, I used **interactive Plotly charts** to analyze key trends in the dataset. Each visualization highlights relationships between **user demographics, ad attributes, and engagement metrics**.

### **Income vs. Click Behavior**  
- **Scatter Plot:** Income vs. Clicks, colored by Age  
- **Insight:** Higher-income users tend to **click on more ads**, but engagement varies significantly across age groups.  
- **Key trend:** Younger consumers (**18–35**) with mid-range incomes show **higher click rates**, while older users are less engaged.  

![Income vs Clicks][(images/Income_vs_Clicks.png)]

---

### **Relationships Among Numerical Features**  
- **Correlation Heatmap**  
- **Insight:** Click-through rates have a **strong correlation** with income and ad type.  
- **Key observation:** Higher conversion rates often align with **higher engagement metrics like clicks per user**, confirming that **income and ad placement significantly impact ad effectiveness**.  

![Correlation Heatmap][(Correlation_Heatmap-1.png)]

---


### **Click Rates Across Income Groups**  
- **Bar Chart:** Clicks by income bins (10K–90K), color-coded from yellow to purple  
- **Insight:** Click rates tend to be **higher in mid-income groups ($25K–40K)** and decline slightly in **higher-income brackets ($55K+)**.  
- **Potential reasoning:** Mid-income consumers **engage more frequently with ads**, possibly due to targeted marketing strategies.  

![(Clicks_vs_Income)]![(images/Clicks_vs_Income.png)] 

---

### **Click Behavior by Gender**  
- **Box Plot:** Clicks by Gender  
- **Insight:** Female consumers generally have **higher median click rates**, but male consumers exhibit **greater variability** in engagement.  
- **Key takeaway:** Gender-based targeting in digital marketing **may influence ad effectiveness**, with females showing **consistent engagement patterns** across income levels.  

![(Clicks_By_Gender)]![(images/Clicks_by_Gender.png)]

---

### **Conversion Rate Trends Over Time**  
- **Conversion Rate Timeline:** Monthly trends by gender  
- **Insight:** Conversion rates **fluctuate seasonally**, with increases around **holiday periods** and promotional campaigns.  
- **Key trend:** Female consumers exhibit **higher conversion stability**, while male engagement tends to be **less predictable** across different months. 

![(Conversion_Rate_Timeline)]![(Conversion_Rate_Timeline.png)]

---

# **Machine Learning Pipeline**  
To optimize ad targeting and engagement strategies, I developed **two predictive models** using machine learning.

### **Regression Pipeline: Predicting Ad Clicks**  
- **Model Used:** Random Forest Regressor  
- **Evaluation Metrics:**  
  - **R² Score:** 0.97 (strong predictive accuracy)  
  - **Mean Squared Error (MSE):** 0.06  

#### **Key Findings:**  
- The model **accurately predicts ad clicks** using consumer demographics and ad attributes.  
- **Income, age, and ad placement** are the strongest predictors of consumer engagement.  

---

### **Classification Pipeline: High vs. Low Engagement**  
- **Model Used:** Random Forest Classifier  
- **Evaluation Metrics:**  
  - **Accuracy:** 77%  
  - **F1 Score:** 0.34 (struggles with high conversions)  

#### **Key Findings:**  
- The model classifies **low engagement users well**, but struggles with **high conversion cases** due to imbalanced data.  
- **Feature engineering improvements** (like ad interaction history) could enhance accuracy.  

---

## **Regression Performance Summary**
| Metric | Score |
|--------|------|
| **MSE** | 0.486 |
| **R² Score** | 0.7428 |
| **Best Parameters** | {'max_depth': 15, 'min_samples_leaf': 2, 'n_estimators': 300} |
| **Best R² Score** | 0.7455 |

---

## **Classification Performance Summary**
| Metric | Score |
|--------|------|
| **Accuracy** | 0.84 |
| **F1 Score** | 0.50 |

#### **Classification Report**
| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| **0 (Low Clicks)** | 0.84 | 0.99 | 0.90 | 77 |
| **1 (High Clicks)** | 0.89 | 0.35 | 0.50 | 23 |

#### **Confusion Matrix**
[[76 1] [15 8]]

---

## **Project Conclusion**
This project explored consumer ad click behavior, developed predictive models, and uncovered insights into **digital marketing optimization**.

### **Key Insights**
- **Income, gender, and ad placement strongly affect engagement.**  
- **Regression model effectively predicts ad clicks with strong accuracy.**  
- **Classification model struggles with high engagement predictions, requiring refinement.**  

### **Future Work**
- **Enhance feature engineering** (include ad interaction history).  
- **Test ensemble methods** (Boosting/Bagging) for better classification.  
- **Integrate external datasets** for deeper insights into consumer behavior trends.  

---

## **References & Repository Details**
- **Dataset:** [Online Advertisement Click-Through Rates][(https://data.mendeley.com/datasets/wrvjmdtjd9/1)] 
- **DOI:** [10.17632/wrvjmdtjd9.1][(http://dx.doi.org/10.17632/wrvjmdtjd9.1)]  
- **GitHub Repository:** [MarketMind][(https://github.com/sisi195/Marketing-Optimization)]  

---
