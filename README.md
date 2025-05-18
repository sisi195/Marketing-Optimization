# MarketMind: Predicting Ad Performance with Consumer Behavior Data

## Overview

In this project, I built an end-to-end pipeline to analyze and predict consumer engagement with online advertisements. By cleaning a rich dataset, performing exploratory data analysis (EDA) with interactive Plotly charts, and developing machine learning pipelines, I explored the complex relationships between user demographics, ad attributes, and engagement metrics (clicks and conversion rates). This analysis not only unveiled insights into the drivers of ad performance but also set the stage for predictive modeling to optimize digital marketing strategies.

## Dataset

**Dataset:** [Online Advertisement Click-Through Rates](https://data.mendeley.com/datasets/wrvjmdtjd9/1)  
**Published:** 22 April 2024  
**Version:** 1  
**DOI:** [10.17632/wrvjmdtjd9.1](http://dx.doi.org/10.17632/wrvjmdtjd9.1)  
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

## Project Structure

- **Data Cleaning & Preprocessing:**  
  - Standardized column names and handled missing values.
  - Converted financial fields (e.g., `income`) and date fields (`click_date`) to proper formats.
  - Engineered additional features such as `click_day`, `click_month`, and interaction terms (e.g., `income_x_clicks`, `ctr_x_conversion`).

- **Exploratory Data Analysis (EDA):**  
  I used interactive Plotly charts to answer key questions:
  - _How does income affect click behavior?_ (Scatter Plot: Income vs. Clicks colored by Age)
  - _What are the relationships among the numerical features?_ (Correlation Heatmap)
  - _How do click rates vary across income groups?_ (Bar Chart using custom income bins: 10K–25K, 25K–40K, 40K–55K, 55K–70K, 70K–90K with a gradient from yellow to purple)
  - _Are there differences in click behavior between Female and Male consumers?_ (Box Plot: Clicks by Gender)
  - _How do conversion rates change over time by gender?_ (Conversion Map: Average Conversion Rate over Time by Gender)

- **Machine Learning Pipeline:**  
  Two predictive models were built:
  - **Regression Pipeline:**  
    - Predicting the continuous number of ad clicks using a Random Forest regressor.
    - Model performance was evaluated with Mean Squared Error (MSE) and R², and hyperparameter tuning was done via GridSearchCV.
  - **Classification Pipeline:**  
    - Classifying consumer engagement (high vs. low clicks) based on the median click count.
    - Evaluated using accuracy, F1 score, and a detailed classification report.

## Installation & Usage

1. **Clone the Repository:**
   ```bash
  git clone https://github.com/yourusername/MarketMind.git
   cd MarketMind
pip install -r requirements.txt

MIT License

Copyright (c) 2025 Sierra

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

Contributing
If you’d like to contribute improvements or report issues, feel free to open an issue or submit a pull request. Your feedback and contributions are welcome!

Acknowledgments
Dataset Contributors: Jagadish Tawade and Nitiraj Kulkarni for providing the comprehensive Online Advertisement Click-Through Rates dataset via Mendeley Data.

Inspiration: This project was developed to understand consumer behavior better and improve ad targeting strategies through data-driven insights.
