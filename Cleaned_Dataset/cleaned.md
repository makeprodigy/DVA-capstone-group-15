# Cleaned Data Documentation

**Project:** Powering India – Renewable Energy Analysis
**Dataset:** Potential, Generation, Capacity – Renewable (NDAP)



## Overview

This document summarizes all data cleaning and preparation steps performed to transform the raw NDAP dataset into a structured and analysis-ready format for KPI calculation and dashboard development.



## 1. Raw Data Preservation

* The original dataset was stored in a separate sheet:

  * **Sheet Name:** RAW
* No modifications were made to the raw data to maintain:

  * Data integrity
  * Transparency
  * Reproducibility



## 2. Column Selection

Unnecessary columns were removed to simplify analysis.
Only the following columns were retained:

* State
* Financial Year
* Types of Energy Sources
* Energy Value Type (Potential / Installed Capacity / Generation)
* Values for Renewable Electricity

This reduced complexity and focused the dataset on relevant renewable energy metrics.



## 3. Whitespace Cleaning

* Applied `TRIM()` to text columns:

  * State
  * Energy Source
  * Energy Value Type
* Removed leading and trailing spaces to avoid duplicate categories.



## 4. Text Standardization

* Applied `PROPER()` function to:

  * State names
  * Energy source names
  * Energy value type
* Ensured consistent formatting for accurate grouping and aggregation.



## 5. Year Extraction

* Extracted numeric year from Financial Year using:

```
=VALUE(RIGHT(Financial_Year,4))
```

* Created a new column: **Year**
* Enabled time-series analysis and trend visualization.



## 6. Renewable Energy Filtering

Only renewable sources were retained:

* Solar
* Wind
* Small Hydro
* Biomass / Biomass-Bagasse
* Waste to Energy

Removed non-renewable sources such as:

* Coal
* Diesel
* Natural Gas
* Lignite
* Nuclear
* Hydro (large)

This aligned the dataset with the renewable energy focus of the project.



## 7. Missing Value Handling

* Blank values in **Value_MW** were replaced with **0**
* Rows with zero values were **retained**, as they represent:

  * No installed capacity
  * No generation
  * Untapped potential
* Rows were removed only if critical fields were missing:

  * State
  * Energy Source
  * Energy Value Type



## 8. Duplicate Removal

Duplicates were removed based on the combination of:

* State
* Year
* Energy Source
* Energy Value Type

This ensured accurate aggregation and prevented double counting.



## 9. Data Type Validation

* Year → Numeric
* Value → Numeric
* State / Energy Source / Energy Value Type → Text

Ensured compatibility with formulas, pivot tables, and charts.



## 10. Category Standardization

Standardized **Energy Value Type** into three categories:

* Potential
* Installed Capacity
* Generation

This allowed proper pivot restructuring.



## 11. Unit Verification

* Potential and Installed Capacity → **MW (Power)**
* Generation → **MU (Million Units)** (Annual Energy)

Column names were standardized after pivot:

* Generation_MU
* Capacity_MW
* Potential_MW



## 12. Data Restructuring (Pivot)

Created a Pivot Table with:

**Rows**

* State
* Year
* Energy Source

**Columns**

* Energy Value Type

**Values**

* Sum of Renewable Electricity

This produced a structured dataset at:
**State–Year–Source level**



## 13. Final Data Sheet Creation

* Pivot results were transferred to a new sheet: **Final_data**
* Used formulas:

```
=IF(PivotCell="",0,PivotCell)
```

* Converted blank cells into 0
* Maintained dynamic linkage to the Pivot



## 14. Generation Conversion

Since Generation was annual energy (MU), it was converted to average power:

```
Avg_Generation_MW = (Generation_MU × 1000) / 8760
```

This allowed comparison with installed capacity.



## 15. KPI Creation

### 15.1 Capacity Utilization Factor (CUF)

```
CUF = Avg_Generation_MW / Capacity_MW
```

Measures infrastructure efficiency.



### 15.2 Potential–Capacity Gap

```
Gap = Potential_MW − Capacity_MW
```

Identifies untapped investment opportunity.



### 15.3 Potential Utilization

```
Utilization = Capacity_MW/ Potential_MW
```

Measures how much natural renewable potential is being used.



## 16. Final Dataset Structure

| State | Year | Energy_Source | Generation_MU | Avg_Generation_MW | Capacity_MW | Potential_MW | CUF | Gap | Utilization |

This dataset supports:

* Gap analysis
* Efficiency analysis
* State comparison
* Source comparison
* Trend analysis
* Dashboard creation



## Outcome

The dataset was cleaned, standardized, restructured, and enriched with performance KPIs to enable accurate and decision-oriented renewable energy analysis for India.
