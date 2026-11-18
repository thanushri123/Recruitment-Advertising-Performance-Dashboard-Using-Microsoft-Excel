# Recruitment Advertising Performance Dashboard

An interactive Excel dashboard that analyses recruitment ad campaigns across four channels and five job categories, built to answer one question: **where should the next recruitment ad dollar go?**

> **Note:** All data is **synthetic** (generated for learning). It is not real client data.

**Tools:** Excel (formulas, Tables, PivotTables, slicers, PivotCharts, conditional formatting) | **Data:** 560 rows, 1-28 Oct 2026

## Dashboard preview

Full-dataset view (all channels, all job categories):

![Dashboard overview - all data](images/dashboard_overview_all.png)

The dashboard is interactive. Picking a **Channel** and **Job category** from the dropdowns updates every KPI, table, insight and chart. Below, it is filtered to **LinkedIn x Engineering**:

![Dashboard filtered to LinkedIn and Engineering](images/dashboard_overview_filtered.png)

![Dashboard charts filtered](images/dashboard_charts_filtered.png)

---

## Business problem

A recruitment marketing team spends money on Google Ads, LinkedIn, Indeed and Facebook to attract applicants for different roles. Leadership wants to know:

1. Which channels deliver applications at the lowest cost?
2. Which job categories are cheapest and most expensive to fill?
3. Is performance improving over time?
4. Are we hitting our CTR, CPC, cost-per-application and application-rate targets?

## Key findings (full dataset)

| Finding | Detail |
|---|---|
| Cheapest channel | **Indeed**, about **$10.65** per application |
| Most expensive channel | **LinkedIn**, about **$37.59** per application (3.5x Indeed) |
| Best click-through | **Google Ads**, 4.53% CTR |
| Best click-to-application rate | **LinkedIn**, 10.0%, but its clicks are very expensive |
| Cheapest job category to fill | **Customer Service**, about **$11.21** per application |
| Costliest job category to fill | **Engineering**, about **$27.69** per application |
| Overall | 14,007 applications from $231,108 spend, **$16.50** per application |
| Trend | Weekly applications rose from 3,345 (Week 1) to 3,574 (Week 4) while cost per application fell about 4.6% |
| Hardest combination | **LinkedIn x Engineering** costs about **$55.22** per application, the highest of any channel and category pair |

**Recommendation (illustrative):** test shifting part of the LinkedIn budget towards Indeed for high-volume roles, and keep LinkedIn for roles where its higher application rate justifies the cost.

## Dataset

560 daily records: 28 days (1-28 Oct 2026) x 4 channels x 5 job categories.

| Column | Description |
|---|---|
| Date | Campaign day |
| Campaign | Campaign name (job category + Always-On / Urgent Fill) |
| Channel | Google Ads, LinkedIn, Indeed, Facebook |
| Job_Category | Analytics, Engineering, Customer Service, Human Resources, Sales |
| Region | Americas, EMEA, APAC |
| Device | Mobile, Desktop |
| Impressions, Clicks, Applications | Funnel volumes |
| Spend_USD | Daily spend in US dollars |

Raw data is also available as CSV: [`data/recruitment_ads_raw_synthetic.csv`](data/recruitment_ads_raw_synthetic.csv)

## KPI definitions

| KPI | Formula |
|---|---|
| CTR | Clicks / Impressions |
| CPC | Spend / Clicks |
| Cost per Application | Spend / Applications |
| Application Rate | Applications / Clicks |

Targets are illustrative assumptions set by the analyst, not client benchmarks.

## Native PivotTables, slicers and PivotCharts

Besides the formula-driven dashboard, the workbook includes native Excel PivotTables built on the `tblAds` table.

### Pivot_Channel: applications by channel and job category, with slicers

Slicers for **Channel**, **Region** and **Job_Category** filter the pivot with one click.

![Pivot_Channel with slicers](images/pivot_channel_slicers.png)

### Pivot_Trend: daily spend, applications and cost per application

Built with a **Calculated Field** (`CostPerApp = Spend_USD / Applications`).

![Pivot_Trend table](images/pivot_trend_table.png)

A **PivotChart** plots the daily applications trend:

![Daily applications PivotChart](images/pivot_trend_chart.png)

### Cross-validation

Pivot grand totals match the formula-driven dashboard when no filters are applied:

| Measure | Pivot | Dashboard |
|---|---|---|
| Applications | 14,007 | 14,007 |
| Spend | $231,107.64 | $231,107.64 |
| Cost per application | $16.50 | $16.50 |

## What is inside the workbook

| Sheet | Purpose |
|---|---|
| **Dashboard** | KPI cards vs target, channel and job-category tables, auto-written insights, 4 charts. Driven by Channel and Job category dropdowns |
| **Analysis** | Formula-driven pivot-style tables: channel x category matrices, weekly and daily trends, day-of-week, region and device, campaign leaderboard, spend extremes |
| **Pivot_Channel** | Native PivotTable with Channel, Region and Job_Category slicers |
| **Pivot_Trend** | Native PivotTable with a CostPerApp calculated field, plus a PivotChart |
| **Raw_Data** | Source data as an Excel Table (`tblAds`) |
| **QA_Checks** | 8 live data-quality checks (missing values, impossible funnel rows, duplicates, reconciliation) |
| **Assumptions** | Targets and dropdown lists |
| **Read_Me** | Project guide and pivot instructions |

## Excel skills demonstrated

- **Formulas:** SUMIFS, COUNTIFS, AVERAGEIFS, MAXIFS / MINIFS, SUMPRODUCT with WEEKDAY, INDEX/MATCH, RANK, IFERROR, TEXT
- **Structure:** Excel Tables, named ranges, wildcard "All" filter logic
- **PivotTables:** multi-field pivots, calculated field, PivotChart, slicers
- **Interactivity:** data-validation dropdowns that drive KPIs, tables and charts
- **Visuals:** conditional formatting (data bars, colour scales, rules), charts that follow the filters
- **Data quality:** QA sheet that proves totals reconcile to the raw data
- **Analysis:** KPI vs target, ranking, trend, segment comparison

## How to use

1. Download `Recruitment_Ads_Dashboard_Pro.xlsx` (GitHub cannot preview Excel files, so open the file and use the **Download raw file** button).
2. Open it in Excel and enable editing.
3. On the **Dashboard** sheet, pick a Channel and Job category from the yellow dropdowns. KPIs, tables, insights and charts update.
4. Open **Pivot_Channel** and click the slicers to filter the pivot.
5. Check **QA_Checks** for data-quality status.

## Repository structure

```
.
├── README.md
├── Recruitment_Ads_Dashboard_Pro.xlsx
├── data/
│   └── recruitment_ads_raw_synthetic.csv
└── images/
    ├── dashboard_overview_all.png
    ├── dashboard_charts_all.png
    ├── dashboard_overview_filtered.png
    ├── dashboard_charts_filtered.png
    ├── pivot_channel_slicers.png
    ├── pivot_trend_table.png
    └── pivot_trend_chart.png
```

## Limitations

- Synthetic data, so findings illustrate the method and are not real-world benchmarks.
- Daily and weekly tables are built for a 28-day window; extend them if the period grows.
- Spend is not tied to hires, so cost per application is not cost per hire.

## Author

**Thanushri R**

[LinkedIn](https://www.linkedin.com/in/thanushri-r-7aab51226) | [Email](mailto:thanushri134@gmail.com)
