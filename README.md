# BI Abwab.ai TRX-200 – Financial Transaction Analysis Dashboard

## Overview

This repository contains a Power BI dashboard designed for the in-depth analysis of financial transaction data. The primary objectives are to visualize transaction flows, identify counterparty risks, and detect potential fraud patterns. The project is built from an annotated financial dataset (`Financial Annotation.xlsx`) and follows a systematic approach to data modeling and visualization as detailed in a companion guide.

The dashboard is divided into three main pages, each focusing on a different aspect of the transaction data.

---

## Transaction Overview

<img width="1000" height="650" alt="Transaction Overview 1" src="https://github.com/user-attachments/assets/938e9203-e667-4418-8f28-afa05f1e25be" />

### Key Visuals & Metrics

| Metric | Value |
|---|---|
| **Total Debit** | 1.60 Million SAR |
| **Net Flow** | 8.24 Million SAR |
| **Transaction Count** | 200 |
| **Avg Transaction Amount** | 57.17K SAR |

### Visual Elements

- **Transaction Type Distribution:** A bar chart displays the frequency of various transaction types, such as:
    - Internal Transfer (CIB) – **44 transactions**
    - Incoming Fast Transfer (RIYAD BANK) – **41 transactions**
    - Fast Outgoing Transfer (CIB via Alinma) – **33 transactions**
    - And various bill payments, payroll deductions, and rejected transfers.

- **Top Counterparties:** A list shows the sum of amounts for key counterparties like *Abdul Latif Jameel United Finance*, *Abdullah Abdulkarim Al Sudais CPA*, and *Advanced Finance and Maintenance Co*.

- **Directional Breakdown:** A pie chart visualizes the proportion of **Credit (34%)** vs. **Debit (66%)** transactions.

- **Monthly Trend:** A line chart tracks the **Sum of Amount** for Credit and Debit transactions from March to June 2023.

---

## Fraud & Risk Analysis

<img width="1000" height="650" alt="Fraud   Risk Analysis 2" src="https://github.com/user-attachments/assets/d15249ff-69af-4846-8691-d27db0d2f84f" />

### Key Visuals & Metrics

- **High-Risk Transactions Table:** A detailed table lists high-value or suspicious transactions, including:
    - **National Company for Building and Marketing** – Multiple large transfers (e.g., 800,000 SAR, 500,000 SAR) flagged with **High** or **Medium** FraudFlag and RiskScore of 5 or 3.
    - **Unknown Sender** – A rejected transfer of 31,653.70 SAR flagged **Medium**.
    - **Rejected Transfer (Returned)** – Multiple smaller returned transfers flagged **Medium**.
    - **Total high-risk amount tracked:** **2,425,056.00 SAR**

- **Balance By Month:** A bar chart showing the net change in balance (Delta) by month. March shows the highest positive Delta (8.3M SAR), while June shows the lowest (0.9M SAR).

- **Amount vs Balance by Risk Level:** This visual correlates the transaction amount with the assigned risk level (Low, Medium, High, Very High, Extremely High).

- **Risk Distribution Over Time:** A line chart tracks the count of High, Medium, and Low FraudFlag transactions from January to June 2023. February saw the highest number of flagged transactions (38).

---

## Counterparty & Cluster Deep Dive

<img width="1000" height="650" alt="Counterparty   Cluster Deep Dive 3" src="https://github.com/user-attachments/assets/6ac1f4e0-44e1-4b91-a67b-08213520cb99" />

### Visual Elements

- **Transaction Types by Volume:** A pie chart breaks down the percentage volume of different transaction types (e.g., largest slice at 16.5%, multiple slices between 1.5% and 7.5%).

- **Risk Distribution by Cluster:** A bar chart visualizes the average amount per cluster categorized by FraudFlag (High, Low, Medium). This helps identify which clusters are most associated with risky behavior.

- **Flow Analysis:** A Sankey or flow diagram illustrates the movement of funds between entities, tracing paths like `Expatriate Services Payment` to `Payroll Project` and various `Fast Outgoing Transfer` routes.

- **Counterparty Transaction Matrix:** A table provides a detailed debit vs. credit analysis for key counterparties.
    - **National Company for Building and Marketing** – **9,445,000.00 SAR** in both Debit and Credit, flagged **High Risk**.
    - Other counterparties like *Interhealth Medical Company*, *Saudi Vetonit*, and *Al Jazeera Paint Factory Company* show significant debit activity.

---

## Project File Structure

The project directory is organized as follows:

```text
BI-Abwab.ai-TRX-200/
│
├── data/
│   └── Financial Annotation.xlsx          # Raw annotated transaction data
│
├── dashboards/
│   ├── Transaction Overview 1.png         # Page 1 screenshot
│   ├── Fraud & Risk Analysis 2.png        # Page 2 screenshot
│   └── Counterparty & Cluster Deep Dive 3.png # Page 3 screenshot
│
├── docs/
│   └── build_guide.md                     # Step-by-step dashboard creation guide (from chat)
│
├── README.md                              # This file
└── .gitignore
