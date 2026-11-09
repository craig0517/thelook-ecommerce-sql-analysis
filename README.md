# TheLook E-Commerce Analytics | SQL & Python

An end-to-end e-commerce analytics portfolio project using **Google BigQuery SQL** and **Python**, based on the public, **synthetic** TheLook dataset.

## Project Overview

This project builds a reusable order-level analytical model and investigates:

- Monthly sales trends and January–September year-over-year performance
- Category sales contribution and **estimated** gross profitability
- One-time versus repeat purchasing customers
- First-observed purchase cohorts and monthly purchasing retention

The analysis uses a reporting cutoff of **September 30, 2026**. Monetary metrics refer to **fulfilled-status item value** (orders currently marked `Complete` or `Shipped`), not audited recognized revenue.

## Key Findings

| Area | Finding |
|---|---|
| Sales (Jan–Sep 2026 vs. 2025) | Fulfilled-status item value grew **73.43%**, with fulfilled orders up **73.56%**; AOV was approximately flat (**−0.07%**). |
| Category performance | **Outerwear & Coats** led with approximately **$672.9K** of fulfilled-status item value (**12.51%** of total) and **$373.6K** in estimated gross profit. |
| Customer segmentation | Repeat customers represented **22.98%** of purchasing customers and accounted for **40.38%** of fulfilled-status item value. |
| Cohort purchasing activity | For 2025 first-observed fulfilled-purchase cohorts (n = **11,383**), weighted activity was **1.47% at M+1**, **1.75% at M+3**, and **1.86% at M+6**. |

These are descriptive results from a synthetic dataset, not evidence of real-world buying behavior or causal effects.

## Tools & Techniques

- **BigQuery (GoogleSQL):** joins, CTEs, conditional aggregation, `CASE`, `DATE_DIFF`, window functions, safe division
- **Data modeling:** one-row-per-order fact model and customer/cohort aggregations
- **Data validation:** row-grain checks and reconciliation across order and customer totals
- **Python:** Pandas, Matplotlib, cohort pivot tables and visualizations

## Repository Contents

- `thelook_ecommerce_analysis.ipynb` — SQL queries, Python analysis, validation, visualizations, and written findings
- `README.md` — project overview and key results

## How to Explore

1. Open `thelook_ecommerce_analysis.ipynb` directly on GitHub to read the code and saved outputs.
2. To rerun the analysis, use a Python notebook environment with Google BigQuery access and the `bigquery-public-data.thelook_ecommerce` dataset.
3. Configure your own Google Cloud authentication and billing/project settings; never store credentials in the notebook or repository.

## Important Limitations

- **Synthetic data:** generated patterns may not describe real consumer behavior.
- **Revenue proxy:** fulfilled-status item value is not audited or necessarily recognized revenue.
- **Estimated gross profit:** product costs are not historical COGS and exclude other expenses.
- **Historical status:** current order status is observed at query time; it is not reconstructed at the cutoff date.
- **Cohorts:** first *observed* fulfilled purchase is not necessarily the actual customer acquisition date. Monthly purchasing activity is not continuous retention.

## Data Source

Google BigQuery public dataset: `bigquery-public-data.thelook_ecommerce`
