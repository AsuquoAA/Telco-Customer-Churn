# 📊 Telco Customer Churn Analysis & Dashboard

**Author:** Anthony Asuquo  
**Role:** Data Analyst  
**Date:** July 2025  

__Context__: Telco, a popular telecom company just started to experience customer churn, The Sales manager is deeply concerned as he is unsure of the cause as sales data include many variables. The goal is to identify the key drivers of this decline and recommend ways to averse it.

__Broad Problem__: What is the cause of the customer churn at Telco?

__Narrow Problem__: What factors are driving customer churn?

<u>Why this matters?</u>
1. Customer churn is critical as it leads to lost revenue and increase costs to get back those customers
2. Telco being a reputable company, customer churn could really affect it's image 
3. We need to look at the factors holistically make better decisions instead of looking for a short fix

---

## 🚀 Table of Contents

1. [Project Overview](##project-overview)  
2. [Business Context](##business-context)  
3. [Key Objectives](#key-objectives)  
4. [Dataset & Preparation](#dataset--preparation)  
5. [Exploratory Analysis & Modeling](#exploratory-analysis--modeling)  
6. [Interactive Dashboard](#interactive-dashboard)  
7. [Core Insights & Recommendations](#core-insights--recommendations)  
8. [Project Structure](#project-structure)  
9. [Getting Started](#getting-started)  
10. [Model Performance](#model-performance)  
11. [Next Steps](#next-steps)  
12. [Contact & License](#contact--license)  

---

## 📌 Project Overview

This end-to-end analytics project explores why customers leave a large telecommunications provider. It culminates in an interactive Power BI dashboard that equips stakeholders to spot high‑risk segments and take targeted retention actions.

---

## 🏢 Business Context

High churn rates directly impact revenue and growth. By understanding which customer groups are most at risk—and why—marketing and product teams can craft timely offers, optimize pricing, and improve service quality to boost retention.

---

## 🎯 Key Objectives

- **Quantify** overall and segment‐level churn rates  
- **Segment** customers by tenure, contract, and service type  
- **Analyze** patterns using statistical and ML methods  
- **Build** a churn prediction model (GLM)  
- **Deliver** a clean, interactive dashboard for non‑technical stakeholders  
- **Recommend** actionable strategies to reduce churn

---

## 📂 Dataset & Preparation

- **Source:** [Telco Customer Churn (7,043 records)](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **Key Fields:**  
  - `Churn` (Yes/No)  
  - `Tenure` (months)  
  - `ContractType` (Month‑to‑Month, One‑Year, Two‑Year)  
  - `InternetService` (DSL, Fiber Optic, None)  
  - `MonthlyCharges`
  - `TotalCharges`  
- **Cleaning Steps:**  
  1. Handled missing `TotalCharges` entries and converted to numeric  
  2. Standardized column names and data types  
  3. Created `TenureGroup` bins (0–12, 13–24, etc.)  
  4. Exported cleaned data for reporting and dashboard use

---

## 🔎 Exploratory Analysis & Modeling

- **Tools:** Python (Pandas, Matplotlib), scikit-learn etc.
- **Exploratory Analysis:**  
  - Visualized churn distribution across tenure groups, contract types, and services  
  - Explored relationship between monthly charges and churn using boxplots and summary statistics

- **Modeling:**  
  1. **Feature Engineering & Split**: Prepared features (`Tenure`, `ContractType`, `InternetService`, `MonthlyCharges`) and target (`Churn`), split data 80/20 train/test.  
  2. **GLM Training**: Built a logistic regression model to predict churn probability.  
  3. **Evaluation Metrics**: Calculated accuracy, precision, recall, F1-score, and AUC.  
     - Detailed metrics available in [`model/model_metrics.txt`](model/model_metrics.txt)  
  4. **Model Persistence**: Saved trained model as `model/glm_churn_model.pkl` for reproducibility and deployment

---

## 📊 Interactive Dashboard

![Dashboard Preview](https://github.com/AsuquoAA/Telco-Customer-Churn/blob/main/assets/Dashboard%20Image.png)  
📄 [Full Dashboard (PDF)](https://github.com/AsuquoAA/Telco-Customer-Churn/blob/main/dashboard/Telco%20Customer%20Churn.pdf)

**Dashboard Features:**
- **KPI Cards**: Overall churn rate, total customers, churned customers, average tenure, and average monthly charges  
- **Pie Chart**: Customer distribution by churn status  
- **Dynamic Driver Chart**: `Churn Rate by [Selected Driver]` (toggle between Contract, Internet Service, Tenure Group via “Select Churn Driver” slicer)  
- **Trend Analysis**: Churn rate over tenure groups and continuous tenure  
- **Interactive Filters**: Contract Type, Internet Service, Tenure Group  
- **Insights Panel**: Soft-cream background highlighting strategic recommendations

---

## 💡 Core Insights & Recommendations

| Insight                                                                 | Recommendation                                   |
|-------------------------------------------------------------------------|--------------------------------------------------|
| Month‑to‑Month contracts have >10× the churn rate of 2‑Year plans        | Incentivize 1–2 year commitments with discounts   |
| Customers with tenure <10 months exhibit the highest early churn risk    | Deploy retention offers at months 3 & 9           |
| Fiber‑optic users churn 2.85× more than DSL subscribers                  | Conduct satisfaction surveys & improve service    |
| Higher monthly charges slightly correlate with increased churn risk      | Bundle packages or loyalty rewards for high-bill |

---

## ⚙️ Getting Started

1. **Clone the repo**  
   ```bash
   git clone https://github.com/AsuquoAA/telco-churn-analysis.git
   cd Telco-churn-analysis
   ```

2. **Install dependencies (for analysis/modelling)**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn statsmodels ipython
   ```

3. Explore the analysis notebook
   - Open notebook/analysis.ipynb in Jupyter or VS Code
   - Review data cleaning, EDA, feature engineering, and model training steps

4. Inspect the cleaned data
   - data/modelling_data.csv contains the preprocessed dataset used for modelling

5. Check model performance
   - View metrics (accuracy, precision, recall, confusion matrix) in model/model_metrics.txt
   - See the saved logistic regression model at model/glm_churn_model.pkl

6. Browse the slide deck
   - Open slides/Reducing Customer Churn at Telco_ A Data-Driven Case Study.pdf (or .pptx) for descriptive analysis charts, insights, and hypotheses

7. View the dashboard
   - Interactive: Open dashboard/Telco Customer Churn.pbix in Power BI Desktop
   - Static: View dashboard/Telco Customer Churn.pdf for a full export

8. Read the full project report
   - Open report.pdf for a comprehensive write‑up of objectives, methodology, findings, and recommendations

 ---

 ## 🏆 Model Performance

> 📁 See full evaluation results in [`model/model_metrics.txt`](model/model_metrics.txt)

The model was trained using logistic regression (GLM). It performs reliably, balancing false positives and negatives. With an AUC of ~0.84, it captures churn risk patterns effectively for business use cases.

---

## 🔜 Next Steps

- Add a chart comparing **Avg. Monthly Charges by churn status**
- Publish the dashboard to **Power BI Service** for cloud access
- Enhance dashboard interactivity with **tooltip-based drilldowns**
- Refine model by adding features like `PaymentMethod`, `StreamingServices`
- Track stakeholder feedback for iterative improvements

---

## 📞 Contact & License

**Anthony Asuquo**  
📫 www.linkedin.com/in/anthony-asuquo-718200227

✉️ asuquoanthony2@gmail.com

---

**License:**  
This project is released under the [MIT License](https://opensource.org/licenses/MIT).
