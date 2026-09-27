 # Wingstop Business Performance Analysis

**Independent Data Analytics Project** examining Wingstop's growth, existing-store performance, and share repurchase activity using SQL and Power BI.

## Project Overview

This project analyzes Wingstop's recent business performance by examining company growth, existing-store performance, and share repurchase activity.

The analysis was designed to look beyond overall sales growth and examine whether Wingstop's expanding restaurant footprint and higher system-wide sales were accompanied by stronger performance at existing restaurants. Share repurchase activity was also analyzed to compare capital allocation with operating performance during the same reporting periods.

## Business Question

**How is Wingstop performing as the company continues to expand, and how does its share repurchase activity compare with trends in sales growth and existing-store performance?**

## Analysis Objectives

1. Understand how Wingstop's overall sales and restaurant footprint are changing over time.
2. Evaluate whether existing restaurants are keeping pace with overall company growth by examining same-store sales and domestic average unit volume (AUV).
3. Compare share repurchase activity with operating performance during the same reporting periods.

## Methodology

Publicly available Wingstop company performance information was compiled and structured for analysis.

The data was initially organized in Excel and imported into MySQL. SQL was used to structure the data, organize the quarterly reporting periods, add supporting fields, and validate the information used in the analysis.

The prepared data was then connected to Power BI to create an interactive dashboard comparing company growth, existing-store performance, and share repurchase activity.

**Tools Used:** Excel | MySQL | SQL | Power BI

## Power BI Dashboard

The dashboard was designed to compare overall company growth with existing-store performance and capital allocation across the reporting periods analyzed.

![Wingstop Business Performance Dashboard](images/Wingstop%20Power%20BI%20Dashboard.png)

## Key Findings

### Overall Growth
Wingstop continued to expand during the periods analyzed. System-wide sales increased from **$1.347 billion in Q4 2025 to $1.411 billion in Q2 2026**, while restaurant count increased from **3,056 to 3,255**.

### Existing-Store Performance
Overall growth was not matched by stronger existing-store performance. Same-store sales remained negative, moving from **-5.8% in Q4 2025 to -8.7% in Q1 2026**, before improving to **-7.5% in Q2 2026**. Domestic AUV declined from approximately **$2.000 million to $1.893 million** over the period.

### Capital Allocation
Reported share repurchase spending increased from approximately **$60.00 million in Q4 2025 to $77.88 million in Q1 2026**. During the same Q4-to-Q1 period, same-store sales weakened and domestic AUV declined.

The comparison identifies trends occurring during the same reporting periods and does not establish that share repurchases caused changes in existing-store performance.

## Stakeholder Summary

The analysis shows that Wingstop continued to grow at the company level while existing-store performance remained under pressure.

From Q4 2025 through Q2 2026, system-wide sales and restaurant count increased, demonstrating continued overall expansion. However, domestic AUV declined and same-store sales remained negative throughout the periods analyzed.

Capital allocation provided an additional point of comparison. Reported share repurchase spending increased from approximately **$60.00 million in Q4 2025 to $77.88 million in Q1 2026**. During that same Q4-to-Q1 period, same-store sales weakened from **-5.8% to -8.7%**, while domestic AUV declined from **$2.000 million to $1.956 million**.

Overall, Wingstop's expansion and higher system-wide sales occurred alongside weaker existing-store performance, while the company was also increasing reported spending on share repurchases. These findings show concurrent trends and do not establish a causal relationship between share repurchases and operating performance.

## Selected SQL

SQL was used to structure and prepare the quarterly performance data for analysis in Power BI. Below are selected examples from the project.

### Creating a Chronological Quarter Sort

The reporting periods were stored as text, so a numeric helper column was added to preserve chronological order in Power BI.

```sql
ALTER TABLE wingstop_performance
ADD period_sort INT;
```

The reporting periods were then assigned chronological sort values.

```sql
UPDATE wingstop_performance
SET period_sort = 20254
WHERE period = 'Q4 2025';

UPDATE wingstop_performance
SET period_sort = 20261
WHERE period = 'Q1 2026';

UPDATE wingstop_performance
SET period_sort = 20262
WHERE period = 'Q2 2026';
```

### Adding Share Repurchase Data

The analysis was expanded to include share repurchase activity as a capital allocation measure.

```sql
ALTER TABLE wingstop_performance
ADD shares_repurchased INT;

ALTER TABLE wingstop_performance
ADD share_repurchase_spending_millions DECIMAL(10,2);
```

### Validating the Analysis Data

Selected fields were queried in chronological order to validate the information used for the Power BI analysis.

```sql
SELECT
    period,
    shares_repurchased,
    share_repurchase_spending_millions
FROM wingstop_performance
ORDER BY period_sort ASC;
```

## Skills Demonstrated

- **SQL / MySQL:** Table creation and modification, data updates, filtering, sorting, and validation
- **Power BI:** Data connection, interactive filtering, KPI cards, trend analysis, tooltips, and dashboard design
- **Excel:** Initial data organization and preparation
- **Data Analysis:** KPI selection, trend comparison, data-quality decisions, and interpretation
- **Business Analysis:** Developing a business question, defining analytical objectives, identifying findings, and communicating stakeholder insights



