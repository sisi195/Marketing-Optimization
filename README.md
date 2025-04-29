# MarketMind: Machine Learning for Marketing Optimization

## Overview

MarketMind is a cutting‐edge project that leverages machine learning to optimize online ad targeting and enhance marketing strategies. By analyzing two primary datasets—the **Social Network Ads Dataset** and the **Consumer Behavior Dataset**—MarketMind uncovers trends in user behavior, refines ad targeting, and ultimately aims to boost engagement and conversion rates.

## Project Goals & Research Questions

### Social Network Ads Dataset
1. **What demographic factors influence purchasing decisions?**  
   - We analyze age, gender, and estimated salary to determine their impact on purchase outcomes.
2. **How does estimated salary correlate with product purchases?**  
   - We investigate whether higher salary ranges correspond with increased purchase likelihood.
3. **Can we predict purchases based on age and gender?**  
   - We build predictive models (e.g., Logistic Regression) using age, gender, and salary as features to forecast buying behavior.
4. **What trends can be identified to improve ad targeting strategies?**  
   - Exploratory analysis and clustering (K‑Means) are used to segment users and identify actionable insights for targeted ad campaigns.

### Consumer Behavior Dataset
1. **What factors influence user engagement and conversion rates?**  
   - We evaluate ad characteristics such as click-through rate (CTR), ad type, and placement to uncover key drivers of engagement.
2. **How do demographics correlate with ad performance?**  
   - We assess the relationship between user demographics and the effectiveness of different ad formats.
3. **Can predictive models enhance ad targeting strategies?**  
   - Using ensemble methods (Random Forest, Gradient Boosting) and addressing class imbalance with SMOTE, we build models to predict conversions and optimize campaign strategies.

## Data Analysis & Modeling Techniques

- **Exploratory Data Analysis (EDA):**  
  Tools used: Pandas, Matplotlib, Seaborn  
  - Visualizations include histograms, count plots, and scatter plots to understand distributions and trends.

- **Classification Models:**  
  Techniques: Logistic Regression (baseline), Random Forest, and Gradient Boosting  
  - These models predict purchase outcomes and ad conversions.

- **Data Balancing:**  
  Technique: SMOTE (Synthetic Minority Oversampling Technique)  
  - Applied to mitigate class imbalance issues in the Consumer Behavior data.

- **Clustering:**  
  Technique: K-Means  
  - Used to segment the Social Network Ads data based on demographics (e.g., age and estimated salary) for refined targeting.

## Google Colab Notebook Structure

The Colab notebook is organized into the following logical steps:
1. **Setup & Import Libraries:**  
   - Import all necessary libraries and configure the display settings (e.g., plotting styles).
2. **Data Loading & Overview:**  
   - Read in the Social Network Ads and Consumer Behavior datasets and inspect their structure.
3. **Exploratory Data Analysis (EDA):**  
   - Visualize distributions for key features and targets to gain insights into the data.
4. **Data Preparation for Modeling:**  
   - Define feature sets and target variables for classification and clustering.
5. **Model Training & Evaluation:**  
   - Build baseline Logistic Regression models, then enhance predictions using SMOTE with Random Forest and Gradient Boosting classifiers.
6. **Clustering with K-Means:**  
   - Apply K-Means clustering to the Social Network Ads data to discover user segments.
7. **Conclusion & Future Directions:**  
   - Summarize findings, answer the key research questions, and outline future work.

## How to Run the Notebook

1. **Clone the repository:**  
   ```bash
  git clone https://github.com/sisi195/MarketMind.git
