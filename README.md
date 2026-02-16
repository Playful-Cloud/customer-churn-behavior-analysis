# Customer Churn Behavior Analysis

This repository contains the analysis of customer behavior and support interactions to understand the drivers of churn. The focus is **actionable insights** rather than predictive modeling.

---

## Introduction

Customer churn is a critical metric for subscription-based services. Understanding behavioral patterns that lead to churn allows businesses to design interventions that improve retention and reduce support costs.

---

## Problem Statement

The company seeks to identify which behaviors and interactions correlate with churn. Specific questions include:

- Which customers are at the highest risk of churn?  
- How do engagement and support usage interact to affect churn?  
- Which early indicators can be monitored for timely intervention?  

---

## Objectives

1. Analyze raw customer activity and support ticket data.  
2. Identify behavioral patterns and correlations that drive churn.  
3. Provide actionable insights and recommendations to reduce churn.  
4. Define metrics to monitor churn risk and customer engagement.

---

## Tools & Technologies Used

- Python 3.x  
- Pandas, NumPy, Matplotlib, Seaborn  
- Jupyter Notebooks  

---

## Dataset Handling

### Raw Data
Raw datasets include customer engagement logs, support tickets, and subscription details.

### Processed Data
Processed datasets standardize headers, remove duplicates, handle missing values, and include derived features such as engagement counts and support flags.

---

## Reproducibility

### Data Access
- **data/**: Contains datasets (CSV, Excel).  
- **docs/**: Contains reference and documentation files.  

**Limitations:**  
These files are **not original to me** and cannot be distributed. They are provided **solely for certification purposes**.

**Contents may include:**
- Project specifications  
- Exam instructions  
- Data dictionaries  
- Supporting PDFs  

Project instruction materials and internal communication documents are excluded from public distribution and **not intended for sharing**.

---

## Project Approach

| Step | Description |
|------|-------------|
| 1. Data Ingestion | Load raw datasets, standardize headers, validate schema. |
| 2. Data Quality & Cleaning | Handle missing values, duplicates, and inconsistent date formats. |
| 3. Feature Engineering | Compute KPIs (CTR, CR, CPC, ROI) and campaign-level aggregates. |
| 4. Exploratory Data Analysis (EDA) | Visualize KPI distributions, identify outliers, correlations, and channel trends. |
| 5. Data Transformation & Modeling | ensures validated, production-grade data for reliable, interpretable, and scalable analytics. |
| 6. A/B Testing & Chi-Square Test | Statistical tests to validate relationships between engagement, support, and churn. |

---

## Data Transformation

Data transformation focuses on cleaning, aggregating, and feature engineering to create validated inputs for analysis:

- KPIs and derived metrics (event_count, support flags)  
- Customer segmentation for churn risk analysis  
- Aggregation by plan type, support usage, and engagement level  

---

## Repository Contents Overview

| Folder | Description |
|--------|-------------|
| [**Docs**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/tree/main/docs) | Documentation including data dictionaries, methodology notes. |
| [**Data**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/tree/main/data)| All datasets, including raw and processed data. |
| [**Notebooks**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/tree/main/notebooks) | Notebooks for ingestion, cleaning, feature engineering, EDA, and analysis. |
| [**Reports**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/tree/main/reports) | Generated figures, PDFs, summaries, and analytics insights. |
| [**.gitignore**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/blob/main/.gitignore) | Untracked files excluded from Git. |
| [**README.md**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/blob/main/README.md) | This project documentation. |

---

## Project Structure

```text
customer-churn-behavior-analysis/
├── data/                  # Raw and processed data
│
├── Docs/                  # Documentation, Instruction
│
├── notebooks/             # Jupyter notebooks with analysis
│   ├── 01_eda/           	# Exploratory Data Analysis
│   ├── 02_data_cleaning/ 	# Data Cleaning and Transformation
│   └── 03_analysis/     	# Data Analysis & Statistical Testing
│
├── reports/
│   ├── figures/           # Analysis figures and charts
│   └── final_reports/     # PDF reports
│
├── README.md              # Project documentation
│
└── .gitignore             # Files/folders to exclude from Git

```

---

### Jupyter Norebook:

| Notebook | Description |
|:--------|:-------------|
| [**01_eda/**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/blob/main/notebooks/01_eda.ipynb) |  Exploratory Data Analysis (EDA) covering initial data exploration, distributions, correlations, and outlier detection.. |
| [**02_data_cleaning/**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/blob/main/notebooks/02_data_cleaning.ipynb) |  Data Cleaning and Transformation: missing value handling, duplicates removal, standardization, feature derivation, and quality checks. |
| [**03_analysis/**](https://github.com/Playful-Cloud/customer-churn-behavior-analysis/blob/main/notebooks/03_analysis.ipynb) |  Data Analysis & Insights: segmentation, churn behavior patterns, statistical tests (Chi-Square), and visualization of key metrics.. |


---

## Analysis Results & Key Findings

### Churn Segmentation Table

| Low Engagement | High Support | Churn N | No Churn N | Total | Churn Rate (%) |
|----------------|--------------|---------|------------|-------|----------------|
| False          | False        | 5       | 71         | 76    | 6.6            |
| False          | True         | 2       | 56         | 58    | 3.4            |
| True           | False        | 58      | 102        | 160   | 36.2           |
| True           | True         | 49      | 57         | 106   | 46.2           |
| **All**        |              | 114     | 286        | 400   | 28.5           |

**Insights:**

- Churn is strongly associated with **low engagement**.  
- Support ticket volume alone shows weak separation, but combined with engagement, it becomes a **powerful risk signal**.  
- Customers with both low engagement and high support usage exhibit the **highest churn rate (~46%)**.  
- Early disengagement coupled with high support friction is the **highest-risk segment**.

---

### Chi-Square Test

```python
# Contingency table for chi-square test
chi_table = pd.crosstab(
    [final_df["low_engagement"], final_df["high_support"]],
    final_df["churn_status"]
)

chi2, p_value, dof, expected = chi2_contingency(chi_table)

print(f"Chi-square statistic: {chi2:.2f}")
print(f"P-value: {p_value:.4f}")

```

---

### Results:

- Chi-square statistic: 56.85
- P-value: 0.0000

### Interpretation:

- P-value < 0.05 confirms the relationship is statistically significant.
- The observed churn pattern is not random; it reflects a real behavioral relationship in the data.

---

### Key Findings

- Low engagement is the strongest behavioral indicator of churn.
- Support ticket volume alone has limited predictive power, but in combination with low engagement, churn risk is amplified.
- Customers with low engagement and high support usage show the highest churn (~46%).
- Prolonged support resolution times materially increase churn risk.

---

### Metric to Monitor

1. Early Engagement Rate (EER):
- % of new customers performing >1 activity event in initial usage period.
- Baseline from data: ≈75% of users have >1 event.
- Users with ≤1 event:
 - Churn: 36% (low engagement alone)
 - Churn: 46% (combined with high support)

2. Monitoring:
- Track weekly or monthly.
- Segment by plan type (Free vs Paid) and support interaction.
- Flag drops below baseline for early intervention.

---

### Recommendations

1. Prioritize Early Engagement Activation
- Onboarding nudges & guided actions in the first sessions.
- Encourage ≥2 meaningful actions (e.g., workout tracking or content interaction).
- Expected impact: Reduce early disengagement, lower churn.

2. Escalate Support Resolution for Low-Engagement Users
- Flag users with low engagement & high support usage.
- Prioritize faster resolution & first-contact problem solving.
- Expected impact: Reduce friction, prevent churn from unresolved frustration.


---

### Final Summary

- Customer churn is primarily driven by early disengagement.
- Users with ≤1 activity event have significantly higher churn, especially with frequent support interactions.
- Support resolution time exacerbates churn risk.
- Actionable metrics (Early Engagement Rate) and targeted interventions can help mitigate churn and improve retention.

---

### Final Report:

| File | Description |
|:--------|:-------------|
| [**Customer_Churn_Analysis/**](./Fit.lyCustomerChurnAnalysis.pdf) |  A comprehensive report summarizing the entire churn analysis project. Includes: customer segmentation, engagement and support behavior analysis, key metrics, Chi-Square statistical tests, visualizations, and actionable business recommendations. |

---






















