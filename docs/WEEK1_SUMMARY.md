# Week 1 – Data Cleaning and Preprocessing

**Project:** Invoice Payment Delay & Cash-Flow Intelligence Platform

**Organization:** Orvians Technologies

**Internship Duration:** 8 Weeks

**Week:** 1

**Status:** Completed

## 1. Objective

The primary objective of Week 1 was to understand the invoice dataset, identify data quality issues, perform data cleaning and preprocessing, and prepare a reliable dataset for further exploratory data analysis and machine learning.

The overall project focuses on predicting invoice payment delays, estimating expected settlement time, calculating customer payment risk scores, and forecasting cash collections over 30, 60, and 90 days.

## 2. Dataset Selection

Two candidate datasets were evaluated:

1. Customer Invoices Dataset.
2. Global B2B Invoice & Payments Dataset.

After comparing the available data, the Customer Invoices Dataset was selected as the primary dataset.

The Global B2B dataset showed inconsistencies between payment status, payment dates, and calculated payment delays. Therefore, the Customer Invoices Dataset was considered more suitable for the initial preprocessing stage.

## 3. Work Completed

### 3.1 Dataset Inspection

- Loaded the dataset using Pandas.
- Examined the dataset dimensions and column names.
- Inspected data types and missing values.
- Identified important invoice, customer, payment, and date-related columns.
- Prepared a data dictionary describing the dataset fields.

### 3.2 Data Cleaning

- Identified and removed 1,161 exact duplicate records.
- Removed the `area_business` column because it contained entirely missing values.
- Retained six records with missing `invoice_id` values because the records were otherwise valid.
- Identified missing payment dates in open invoices and retained those records.
- Converted date columns into appropriate datetime formats.
- Identified unusual date relationships and documented them for further review.
- Preserved valid early-payment records.

### 3.3 Target Variable Creation

The following project-specific variables were created:

| Variable | Description |
|---|---|
| `days_to_pay` | Difference between `clear_date` and `posting_date` |
| `delay` | Difference between `clear_date` and `due_in_date` |
| `paid_late` | 1 if delay is greater than zero; otherwise 0. Missing for open invoices |
| `open_paid_flag` | 1 for paid invoices and 0 for open invoices |

The `posting_date` was selected as the starting date for calculating `days_to_pay`.

## 4. Final Dataset Summary

| Metric | Value |
|---|---:|
| Original records | 50,000 |
| Duplicate records removed | 1,161 |
| Final records | 48,839 |
| Final columns | 25 |
| Paid invoices | 39,158 |
| Open invoices | 9,681 |
| Paid on time or early | 22,740 |
| Paid late | 16,418 |

The final dataset was validated to ensure that duplicate records were removed and the derived target variables were consistent with their source dates.

## 5. Challenges Encountered

### Challenge 1: Dataset Selection

The Global B2B dataset contained suspicious inconsistencies between payment status and payment dates.

**Solution:** Compared the candidate datasets and selected the Customer Invoices Dataset for the project.

### Challenge 2: Date Parsing

Some date columns were stored as numeric values in YYYYMMDD format. Initial parsing interpreted them incorrectly as timestamps near 1970.

**Solution:** Corrected the conversion by explicitly specifying the `%Y%m%d` date format.

### Challenge 3: Missing Values

Open invoices naturally contained missing payment dates.

**Solution:** Retained these records because they are important for future payment prediction. Payment-dependent target values remain missing for open invoices.

### Challenge 4: Date Inconsistencies

Some records contained unusual date relationships.

**Solution:** Identified and flagged these records for review instead of automatically deleting potentially useful information.

## 6. Key Learnings

- Learned to inspect and understand real-world datasets using Pandas.
- Improved understanding of missing-value handling and duplicate removal.
- Learned to process date columns stored in different formats.
- Understood how to derive payment-delay variables from invoice dates.
- Learned why open invoices must be retained for future prediction.
- Understood the importance of avoiding data leakage in machine learning.
- Gained practical experience with Jupyter Notebook, Git, and GitHub.

## 7. Deliverables

The following deliverables were completed:

1. Cleaned dataset – `customer_invoices_cleaned.csv`
2. Data dictionary – `data_dictionary.csv`
3. Cleaning log – `cleaning_log.csv`
4. Dataset comparison notebook – `00_compare_datasets.ipynb`
5. Data cleaning notebook – `01_cleaning.ipynb`

All the Week 1 project files were committed and pushed to the GitHub repository.

**GitHub Repository:**

https://github.com/Abhinav9895/invoice-cashflow-intelligence

## 8. Conclusion

Week 1 successfully established a cleaned, documented, and reproducible dataset for the Invoice Payment Delay & Cash-Flow Intelligence Platform.

The completed preprocessing workflow provides a foundation for the next stage of the project.

**Next Stage: Week 2 – Exploratory Data Analysis (EDA) and Data Visualization.**