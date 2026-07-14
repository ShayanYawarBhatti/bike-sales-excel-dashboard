# Bike Sales Dashboard — Excel Data Analysis

An interactive Excel dashboard that analyzes what drives bike purchases — examining income, gender, age, commute distance, and other demographics — built end to end, from raw data cleaning through modeling to an interactive, slicer-driven dashboard.

<p align="center">
  <img src="images/bike_project_dashboard.png" alt="Bike Sales Dashboard" width="100%">
</p>

---

## Project Overview

A retailer wants to understand its potential bike-buying customers. Using a survey-style dataset of roughly 1,000 individuals, this project answers a core business question:

**Which customer characteristics are most associated with buying a bike, and where should marketing focus?**

The final deliverable is an interactive Excel dashboard that lets a user slice the data by marital status, region, and education, and instantly see how income, age, and commute distance relate to purchase behavior.

---

## Dataset

The dataset contains one row per respondent with the following fields:

| Field | Description |
|---|---|
| ID | Unique respondent identifier |
| Marital Status | Married / Single |
| Gender | Male / Female |
| Income | Annual income |
| Children | Number of children |
| Education | Highest education level |
| Occupation | Occupation category |
| Home Owner | Yes / No |
| Cars | Number of cars owned |
| Commute Distance | Distance from home to work (banded) |
| Region | Geographic region |
| Age | Respondent age |
| Purchased Bike | Target variable — Yes / No |

---

## Tools and Skills

Microsoft Excel, using:

- Data cleaning — Remove Duplicates, Find and Replace, number and currency formatting
- Feature engineering — nested `IF` formula to create age brackets
- PivotTables — aggregating and summarizing across dimensions
- PivotCharts — clustered column and line visualizations
- Slicers — interactive cross-filtering across all charts
- Dashboard design — layout, alignment, and color theming

---

## Workflow

```mermaid
flowchart LR
    A[Raw Data] --> B[Data Cleaning]
    B --> C[PivotTables]
    C --> D[PivotCharts]
    D --> E[Slicers and Layout]
    E --> F[Interactive Dashboard]
```

### 1. Data Cleaning

Worked on a copy of the raw data, keeping the original untouched on a separate sheet for safety, and prepared it for analysis:

- Removed duplicate records to prevent double-counting.
- Standardized coded values for readability — replaced `M`/`S` with `Married`/`Single` and `M`/`F` with `Male`/`Female` so the dashboard is understandable to a non-technical audience.
- Formatted income as currency for consistent, clean display.
- Reworded the commute band `10+ Miles` to `More than 10 Miles` so categories sort in a logical order.

### 2. Feature Engineering

Created an Age Brackets column using a nested `IF` formula to group individual ages into three readable segments:

```excel
=IF(Age<31,"Adolescent",IF(Age<55,"Middle Age","Old"))
```

Bucketing continuous age into brackets makes the age analysis far easier to read than plotting dozens of individual ages.

### 3. Data Modeling (PivotTables)

Built PivotTables to summarize the data for each view:

- Average income by gender, split by purchase decision
- Count of purchases by commute distance
- Count of purchases by age bracket

### 4. Visualization (PivotCharts)

- Average Income by Gender and Purchase — clustered column chart
- Bike Purchases by Age Bracket — line chart showing the shape across ordered age groups
- Bike Purchases by Commute Distance — line chart across distance bands

### 5. Dashboard Assembly

- Arranged charts on a dedicated dashboard sheet, removed gridlines, and added a title banner.
- Added three slicers — Marital Status, Region, and Education — and connected them to all PivotTables through Report Connections so every chart filters together in real time.
- Applied a consistent navy and grey color theme for a clean, professional look.

---

## Key Insights

- **Buyers earn more.** In both genders, people who purchased a bike had a higher average income than those who did not, suggesting income is a meaningful purchase driver.
- **Middle-aged customers dominate.** Respondents aged 31 to 54 purchased far more bikes than adolescents (under 31) or older customers (55 and over).
- **Short commuters buy more.** Purchases are highest among people with the shortest commutes and generally taper off as commute distance grows.
- **Income skews by gender** in this sample, with males reporting higher average income than females.

---

## Business Recommendations

- Prioritize the middle-aged, higher-income segment in paid marketing, where purchase intent concentrates.
- Target short-commute and urban customers, who over-index on buying, with commuter-focused messaging.
- Test premium positioning, since buyers consistently earn more than non-buyers, indicating potential room to move up-market.

---

## Reflections and Next Steps

This was one of my first end-to-end Excel dashboards, and building it start to finish surfaced a few things I want to carry into future projects:

- **Match the chart type to the data.** I used a line chart for commute distance, but those bands are categorical, not continuous — a clustered column chart would communicate the comparison more honestly. Next time I'll be more deliberate about chart-type selection up front.
- **Lead with headline numbers.** The dashboard would read more like a real business tool with KPI cards (total respondents, overall purchase rate, average income of buyers) at the top. I plan to include summary metrics by default going forward.

Documenting these here so I can hold myself to them — and so the progression is visible across my next projects.
