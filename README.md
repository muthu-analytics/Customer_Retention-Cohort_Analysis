# Customer Retention & Cohort Analysis | Tableau

An interactive Tableau dashboard that shows whether customers of a UK online retailer come back after their first purchase, when they stop coming back, and which customer groups retain best.

![Customer Retention & Cohort Analysis Dashboard](dashboard.png)

---

## 📌 Problem Statement

| Problem | Description |
|---|---|
| **No visual view of customer retention** | Retention is shown only as numbers in a spreadsheet, making it hard to understand customer behavior over time. |
| **Cannot compare customer groups** | The business cannot easily compare whether customers who joined in different months are staying or leaving. |
| **No visibility of retention trends** | The business cannot see whether retention is improving or declining over time. |
| **Cannot identify when customers leave** | The business does not know at which month customers are most likely to stop buying. |

## 💡 Solution

A **cohort-based Tableau dashboard**. Each customer is assigned to a cohort based on the month of their first purchase, and each cohort is tracked month by month (Month 0, Month 1, Month 2, …) to measure how many customers return.

| Dashboard component | What it shows |
|---|---|
| **KPI strip** | Total customers, revenue, repeat rate, Month 1 retention, biggest drop-off stage |
| **Cohort retention heatmap** | Retention % for each monthly cohort from Month 0 to Month 6, colour-coded so patterns stand out |
| **Avg retention % by country** | Retention compared across the top 6 countries by customer count |
| **Retention trend by cohort** | Whether retention is improving, declining or stable across early, mid and recent cohorts |
| **Cohort details table** | Exact cohort size and retention figures |
| **Filters** | Country, Products, Month/Year of invoice |

---

## 📊 Key Metrics

| Total Customers | Revenue | Repeat Rate | Month 1 Retention | Biggest Drop-off |
|:---:|:---:|:---:|:---:|:---:|
| 5,878 | £17.37M | 72% | 23% | Month 1 |

## 🔍 Key Insights

1. Customer retention drops sharply from **100% to 23%** after the first month, so Month 1 is the biggest drop-off point.
2. **Spain** has the highest retention at **59%**.
3. **Portugal** follows with **49%** retention.
4. The **UK** has lower retention at **33%**, despite having the most customers.
5. December 2011 data is only available for 1–9 December, so the latest month's values are lower than the actual values.

> **Note:** Spain (41 customers) and Portugal (24 customers) have small customer bases, so their high retention should be treated as a lead to investigate rather than a firm conclusion.

## ✅ Recommendations

- **Focus on the first 30 days.** Retention drops most after the first purchase, so welcome emails or a first-repeat-purchase offer could have the biggest impact.
- **Learn from Spain and Portugal.** Investigate what drives their higher retention and test it in the UK market.
- **Run targeted campaigns.** Use the country and product filters to find weak spots instead of running one generic campaign.

---

## 🗂️ Dataset

- **Name:** Online Retail II
- **Source:** [Kaggle – Online Retail II (UCI)](https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci)
- **Original source:** [UCI Machine Learning Repository – Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii)
- **Period:** December 2009 – December 2011
- **Size:** 779,425 transaction records, 10 columns (cleaned)
- **File in this repo:** `online_retail_cleaned.zip` (unzip to get `online_retail_cleaned.csv`)

### Data dictionary

| Attribute | Description |
|---|---|
| `invoice` | Unique invoice/order number |
| `stock_code` | Product SKU/code |
| `description` | Product name |
| `quantity` | Number of units purchased |
| `invoice_date` | Date and time of purchase |
| `price` | Unit price of the item (£) |
| `customer_id` | Unique customer identifier |
| `country` | Customer's country |
| `total_price` | Total value of the transaction line (quantity × price) |
| `invoice_month` | Month of the invoice date |

> Dataset credit: Chen, D. (2019). *Online Retail II*. UCI Machine Learning Repository. Licensed under CC BY 4.0.

---## 🧹 Data Cleaning (Python – Pandas)

The raw dataset was cleaned in Python using Pandas before loading it into Tableau.

| Step | Action |
|---|---|
| 1 | Renamed columns to a consistent lowercase format (e.g. `Customer ID` → `customer_id`) |
| 2 | Removed rows with missing `customer_id`, since retention cannot be tracked without a customer |
| 3 | Removed cancelled orders (invoice numbers starting with `C`) |
| 4 | Removed rows with zero or negative `quantity` or `price` |
| 5 | Removed duplicate rows |
| 6 | Converted `invoice_date` to datetime |
| 7 | Created `total_price` = `quantity` × `price` |
| 8 | Created `invoice_month` from `invoice_date` for cohort analysis |
| 9 | Exported the result as `online_retail_cleaned.csv` (779,425 rows, no missing values or duplicates) |
## 🛠️ Tools Used

- **Python (Pandas)** – data cleaning and preparation
- **Tableau** – calculated fields, cohort heatmap, KPI cards, filters, dashboard design
- **PowerPoint** – project presentation

---

## 👤 Author

**Muthuvalli Elangovan**

[LinkedIn](https://www.linkedin.com/in/muthuvalli-elangovan-2a0908191/) · [GitHub](https://github.com/muthu-analytics)
