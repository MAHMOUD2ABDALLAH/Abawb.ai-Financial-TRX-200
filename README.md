# Financial Transaction Annotation — TRX-200 Case Study

## Overview

This repository contains a structured **financial transaction annotation case study** built in Microsoft Excel.  
The workbook (`Mahmoud Abdallah - Annotation -200 TRX.xlsx`) holds **200 real-world bank transactions** and demonstrates how to systematically label each transaction using a centralized classification scheme.

The goal is to produce a fully annotated dataset that can be used for:
- Financial auditing and reporting
- Accounting system training / rule‑engine development
- Machine‑learning model training for transaction categorisation
- Business intelligence dashboards

---

## Repository Contents

| File | Description |
|------|-------------|
| `Mahmoud Abdallah - Annotation -200 TRX.xlsx` | Main Excel workbook with three sheets |
| `README.md` | This file — project overview and annotation guide |

---

## Workbook Structure

The workbook contains three sheets:

### 1. `task` (Main Annotation Sheet)
**200 rows × 35 columns**  
Each row represents a single bank transaction.  
The first 21 columns contain raw transaction data.  
The remaining **14 columns** are the annotation target:

| # | Column | Purpose |
|---|--------|---------|
| V | `bank_system_classification` | High‑level banking channel (Transfer, SADAD, Payroll, Cash, etc.) |
| W | `bank_system_subclassification` | Sub‑type (Local Transfer, External FI, Same FI, Expat Fees, etc.) |
| X | `Bank System Confidence` | Confidence in bank‑system label (High / Medium / Low) |
| Y | `Bank System Reason` | Explanation for bank‑system classification |
| Z | `Entity` | Counterparty entity type (Shareholder, Supplier, Government, etc.) |
| AA | `Entity Nature of Business` | Industry / sector of the counterparty |
| AB | `scraped_description` | Manually scraped external data (blank by default) |
| AC | `relationship` | Relationship to the borrower (Supplier, Customer, Lender, etc.) |
| AD | `Relationship Confidence` | Confidence in relationship label (High / Medium / Low) |
| AE | `Relationship Reason` | Explanation for relationship label |
| AF | `Accounting_Classification` | Accounting category (Revenue, COGS, OPEX, ZATCA, Other Income) |
| AG | `Accounting_Subclassification` | Detailed account (Payroll, Electricity, Inventory Purchase, etc.) |
| AH | `Accounting Label Confidence` | Confidence in accounting label |
| AI | `Accounting Label Reason` | Explanation for accounting label |

### 2. `Centralized Labels`
A reference library of all valid labels used in the annotation.  
It acts as both a **data‑validation source** and a quick‑reference dictionary.  
Labels are organised into the same 14 categories plus a few extras (e.g., `bank_system_fi_classification`).

### 3. `Description Splitting`
A helper sheet that extracts and splits the `Transaction Type` / `Provider / Payer / Beneficiary` data from the raw bank statement format.  
Useful for understanding how the raw data was pre‑processed.

---

## Annotation Logic

The annotation uses **formula‑based rules** that examine:
- Transaction type (Fast Outgoing Transfer, Bill Payment, Payroll, etc.)
- Direction (Debit / Credit)
- Counterparty name (Provider / Payer / Beneficiary)
- Amount, fees, and bank routing information

**Key classification patterns:**

| Transaction Pattern | Classification |
|---------------------|----------------|
| `Fast Outgoing Transfer (CIB)` | Transfer → Local Transfer |
| `Incoming Fast Transfer (RIYAD BANK)` | Transfer → External FI |
| `Bill Payment 020` to ZATCA | SADAD → Government / Zakat |
| `Bill Payment 060` to GOSI | SADAD → Social Insurance |
| `Bill Payment 050` to Ministry | SADAD → Government Fees |
| `Payroll Deduction (BPM)` | Payroll → Payroll Expense |
| `Expatriate Services Payment` | SADAD → Expat Fees |
| `Internal Transfer (CIB)` | Transfer → Same FI |
| `Cash Deposit` | Cash → Deposit |
| `Rejected Fast Transfer` | Transfer → Failed |

**Confidence assignment rules:**
- **High**: Direct matches to shareholders, government entities, banks, same‑company transfers
- **Medium**: Name‑based matches to known suppliers, customers, service providers
- **Low**: Unknown counterparties or incomplete data

---

## KSA Government Entities Covered

The dataset includes transactions with several KSA government bodies:

| Government Entity | Label |
|-------------------|-------|
| General Authority of Zakat and Tax (ZATCA) | Tax Authority |
| General Organization for Social Insurance (GOSI) | Social Insurance Agency |
| Ministry of Human Resources and Social Development | Government / Regulatory Agency |
| Expatriate Services (Various IDs) | Government |

---

## How to Use

1. Open the `.xlsx` file in Microsoft Excel (formulas will **not** recalculate correctly in Google Sheets).
2. The `task` sheet columns V–AI are automatically populated via formulas.
3. To extend the annotation to new transactions:
   - Copy the formulas down from the last annotated row.
   - Review the six “Reason” columns (`Y`, `AE`, `AI`) and adjust any that need human input.
4. To modify the label library, add/edit entries in the `Centralized Labels` sheet.

---

## Data Source

The raw transactions are sourced from **Alinma Bank** corporate account statements for **RS Infratec Saudi Ltd.**, a construction and real‑estate contracting company in Saudi Arabia.

Transaction period: **January 2023 – June 2023**

---

## License

This project is intended for educational and internal use.  
For any commercial use, please contact the repository owner.

---

## Contact

**Mahmoud Abdallah**  
**Mahmoud_abdallah20@outlook.com**
