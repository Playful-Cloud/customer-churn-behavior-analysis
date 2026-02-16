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

## Tools & Technologies Used

- Python 3.x  
- Pandas, NumPy, Matplotlib, Seaborn  
- Jupyter Notebooks  

---

## Repository Contents Overview

| Folder | Description |
|--------|-------------|
| docs/ | Documentation including data dictionaries, methodology notes. |
| data/ | All datasets, including raw and processed data. |
| notebooks/ | Notebooks for ingestion, cleaning, feature engineering, EDA, and analysis. |
| scripts/ | Python scripts for automation and transformations. |
| reports/ | Generated figures, PDFs, summaries, and analytics insights. |
| .gitignore | Untracked files excluded from Git. |
| README.md | This project documentation. |

---

## Project Structure

```text
customer-churn-behavior-analysis/
│
├── data/                  # Raw and processed data
├── notebooks/             # Jupyter notebooks with analysis
├── reports/
│   ├── figures/           # Analysis figures and charts
│   └── final_reports/     # PDF reports
├── README.md              # Project documentation
└── .gitignore             # Files/folders to exclude from Git