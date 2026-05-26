# Fraud Pattern Recognition 

## Overview

With the rapid growth of digital payments, online banking, and e-commerce, financial transactions are increasingly conducted through electronic platforms. While these systems provide convenience and efficiency, they also introduce increased exposure to fraudulent activity. Fraud detection has therefore become a critical challenge for financial institutions, payment processors, and regulatory bodies.

Fraudulent transactions often follow complex and evolving patterns, making them difficult to detect using traditional rule-based systems. As fraud strategies continuously adapt, organizations must rely on data-driven approaches capable of identifying hidden anomalies within large volumes of transaction data.

The goal of this project is to analyze a digital transaction dataset and identify patterns associated with fraudulent activity using data analytics techniques.

---

## Project Structure

- `analysis.Rmd` — Main R Markdown analysis file (code + exploration)  
- `analysis.html` — Knitted HTML report for user friendly viewing  
- `findings.md` — Key insights and summarized results  
- `fraud_detection_dataset.csv` — Raw dataset used for analysis  
- `README.md` — Project documentation  

---

## Dataset

This project uses a kaggle based **51,000-record dataset**:  
`fraud_detection_dataset.csv`

The dataset contains **12 features**, including:

- Transaction_ID  
- Transaction_Amount  
- Time_of_Transaction  
- Device_Used  
- Location  
- Previous_Fraudulent_Transactions  
- Account_Age  
- Number_of_Transactions_Last_24H  
- Payment_Method  
- Fraudulent (target variable)

---
