# README.md

## Powering India: Analyzing the Gap Between Renewable Energy Potential and Actual Generation



## Project Overview

India is rapidly expanding its renewable energy infrastructure to meet growing electricity demand and climate targets. However, a major challenge remains: **installed capacity and actual generation are not always aligned**, and many states with high renewable potential remain underdeveloped.

This project analyzes the gap between **Renewable Energy Potential, Installed Capacity, and Actual Generation** across Indian states to identify:

* Underutilized resources
* Infrastructure inefficiencies
* Investment priority regions

The final output is an **interactive dashboard** that supports data-driven renewable energy planning.



## Sector

**Energy & Power – Renewable Energy Planning**



## Problem Statement

Which Indian states and renewable energy sources show the largest gaps between renewable potential, installed capacity, and actual generation, and where should infrastructure investments be prioritized?



## Dataset Information

* **Source:** National Data & Analytics Platform (NDAP) – Government of India
* **Dataset:** Potential, Generation, Capacity – Renewable
* **Records:** 8,576 rows
* **Granularity:** State-wise, Year-wise, Energy Source-wise
* **Time Period:** 2008 – 2020
* **Energy Sources Covered:**

  * Solar
  * Wind
  * Small Hydro
  * Bio-Power
  * Waste-to-Energy

The dataset contains missing values, inconsistent categories, and mixed units, requiring extensive preprocessing. 



## Data Cleaning & Preparation

The raw dataset was cleaned and transformed through the following steps:

### 1. Raw Data Preservation

* Original dataset stored separately (RAW sheet)
* No direct modifications to maintain data integrity

### 2. Column Selection

Removed irrelevant fields and retained:

* State
* Year
* Energy Source
* Energy Value Type
* Value

### 3. Text Cleaning

* Removed extra spaces using TRIM
* Standardized case formatting
* Corrected inconsistent naming

### 4. Renewable Filtering

Removed non-renewable sources such as:

* Coal
* Diesel
* Natural Gas
* Nuclear

Retained only renewable categories.

### 5. Handling Missing Values

* Blank values replaced with **0**
* Blank rows and invalid records removed
* Large blocks of empty rows cleaned

### 6. Category Consolidation

* Merged variations such as:

  * Biomass-Bagasse
  * Cogeneration-Bagasse
    → **Bio-Power**

### 7. Data Restructuring

Created a Pivot structure:

* Rows: State, Year, Energy Source
* Columns: Potential, Capacity, Generation

### 8. Unit Standardization

* Potential & Capacity → MW
* Generation → MU
* Converted Generation to average power:

```
Avg_Generation_MW = (Generation_MU × 1000) / 8760
```

### 9. Final Dataset Creation

A **Final_data** sheet was created with:

* Blanks replaced using IF logic
* Clean numeric structure
* Dynamic linkage to Pivot

---

## Final Data Structure

| Column            | Description                  |
| ----------------- | ---------------------------- |
| State             | State/UT name                |
| Year              | Financial year               |
| Energy_Source     | Renewable type               |
| Potential_MW      | Estimated potential          |
| Capacity_MW       | Installed capacity           |
| Generation_MU     | Annual generation            |
| Avg_Generation_MW | Converted average generation |

---

## Key KPIs

### 1. Capacity Utilization Factor (CUF)

```
CUF = Avg_Generation_MW / Capacity_MW
```

Measures infrastructure efficiency.

---

### 2. Potential–Capacity Gap

```
Gap = Potential_MW – Capacity_MW
```

Identifies untapped investment opportunity.

---

### 3. Potential Utilization (%)

```
Capacity_MW / Potential_MW
```

Shows how much available resource has been developed.

---

## Analysis Performed

### Gap Analysis

Identified high-opportunity states such as Rajasthan and Gujarat.

### Efficiency Analysis

Compared CUF across energy sources and states.

### Trend Analysis

Observed rapid capacity growth post-2015, driven primarily by solar.

### Source Analysis

Solar dominates installed capacity, while wind shows strong generation efficiency in coastal regions. 



## Dashboard Features

### Executive KPI Scorecards

* Total Potential
* Total Installed Capacity
* National CUF
* Potential Utilization %

### Visualizations

1. Capacity vs Average Generation (Trend)
2. State-wise Potential vs Capacity Gap
3. Total Potential vs Capacity vs Generation
4. Energy Source Share
5. Efficiency (CUF) by Source

### Interactivity

* State Filter
* Energy Type Filter
* Year Filter



## Key Insights

* **Massive Untapped Potential:** Rajasthan holds the largest renewable opportunity.
* **Efficiency Variance:** Wind performs significantly better in coastal states.
* **Infrastructure Lag:** Capacity growth often outpaces generation.
* **Regional Disparity:** Southern states lead in renewable adoption.
* **Low Utilization:** Only a small fraction of national renewable potential is currently harnessed. 



## Recommendations

* Prioritize infrastructure in high-gap states
* Focus on improving efficiency of existing assets
* Invest in transmission and grid integration
* Promote Bio-Power in agricultural regions



## Limitations

* Missing historical data for some states
* Annual data hides seasonal variations
* No technology-level differentiation within sources



## Future Scope

* Weather-based efficiency modeling
* Cost analysis (LCOE)
* District-level renewable planning



## Project Outcome

This project transforms fragmented government data into a **decision-support tool** for renewable energy planning. It highlights that India’s renewable transition requires not only capacity expansion but also **better utilization, location optimization, and efficiency improvement**. 



## Team

Newton School of Technology – Capstone Project-DVA-GROUP-15
Lakshya Bapna - 2401010252 (Project Lead)
Pushpendra Singh Parihar - 2401010361
Mohan Kumar C R - 2401010282
Saswataduity Bhuin - 2401010425
Akshit vats - 2401020085
Rishita Boisnobi - 2401010382

