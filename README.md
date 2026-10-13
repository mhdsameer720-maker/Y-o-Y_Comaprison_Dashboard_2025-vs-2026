# Year-on-Year Retail Sales Performance Dashboard (2025 vs 2026)

An interactive Power BI dashboard that compares month-wise retail sales and gross profit between 2025 and 2026, tracks achievement against targets, and highlights category-level performance across multiple regions.

## Business Problem
Management needed a single view to answer:
- How are 2026 YTD sales and gross profit performing against target?
- How do they compare with the same period last year?
- Which regions, categories, and stores are driving the variance?

## Key Insights (sample period)
- 2026 YTD Net Sales: **30.44M** vs target of **27.54M**, a **110.51%** achievement
- 2026 YTD Gross Profit: **12.45M** vs target of **11.31M**, a **110.17%** achievement
- Net sales are down **7.5% Y-o-Y** against 2025 YTD (32.91M), and gross profit is down **7.4% Y-o-Y**
- UAE contributes the largest share of sales (about 42%), followed by KSA, Oman, Kuwait, and Qatar
- Every category beat its 2026 target but declined year-on-year

## Dashboard Features
- **KPI cards:** YTD target, net sales, GP, achievement %, with colour-coded Y-o-Y arrows
- **Region-wise sales mix:** donut chart (UAE, KSA, Oman, Kuwait, Qatar)
- **Month-wise Y-o-Y comparison:** 2025 vs 2026 sales
- **Month-wise target vs achievement:** 2026 net sales against target
- **Category matrix:** target, sales, GP, achievement %, and Y-o-Y variance by H2 category
- **Slicers:** Region, Store, H2 Desc, Category Manager, LFL Stores

## Data Model
Star schema with one fact table and two dimension tables:

| Table | Type | Description |
|---|---|---|
| Sales | Fact | Date, Site, H2, Net Sales, Target Net Sales, GP Value, Target GP, Sales Qty |
| Storecode | Dimension | Site, Site Name, Region, LFL Status |
| Category Manager | Dimension | H2, H2 Desc, Category Managers |

Relationships are one-to-many from each dimension to Sales.

## Data Preparation (Power Query)
- Promoted headers, removed top rows, and set data types
- Merged the Sales table with the Storecode and Category Manager tables
- Expanded and renamed columns (for example, LFL Status to LFL Stores)

## DAX Highlights
- **YTD calculations** using `CALCULATE`, `DATESBETWEEN`, and `EDATE` for dynamic 2025 and 2026 YTD periods
- **Variance and achievement measures:** Y-o-Y variance, Y-o-Y %, YTD Ach %, GP Ach %
- **Dynamic card formatting** using `SWITCH(TRUE())`, `FORMAT`, and `UNICHAR` to show up/down arrows with the variance %

Example:

```DAX
YoY Sale Variance % = [YoY Variance] / [LY YTD Sale]
```

## Tools Used
Power BI Desktop, DAX, Power Query, Data Modelling

## Repository Contents
- `Dashboard.pbix`: Power BI report file
- `/screenshots`: dashboard and data model images
- `DAX_Measures.xlsx`: list of all DAX measures

## Note
The data in this repository is sample/anonymised and does not represent real company figures.

## Author
**Mohd Sameer**: MIS Executive / Retail Data Analyst
Power BI (PL-300 certified) | Advanced Excel | SQL | DAX
