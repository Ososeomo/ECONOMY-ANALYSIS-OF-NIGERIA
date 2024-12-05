# Economic Analysis of Nigeria Using SQL and Data Visualization  

## Project Overview

### Objective
This project aims to analyze Nigeria's economic data from 1990 to 2022, focusing on key indicators such as inflation, unemployment, sector contributions to GDP, and government debt. The analysis leverages SQL for data extraction and manipulation, alongside data visualization tools to derive insights into the country's economic performance.

### Key Analysis Areas
- **Inflation and Unemployment Trends:** Examining the relationship between inflation and unemployment over time.
- **Sectoral Contributions to GDP:** Investigating contributions from Agriculture, Industry, and Services sectors to Nigeria's GDP.
- **Debt-to-GDP Ratio:** Analyzing Nigeria’s government debt relative to GDP over time.

---

## Data Overview

### Data Sources
- **Primary Dataset:** `Nigeria Economy - Data Prepared by Alaoh Sodiq.xlsx`
  
This dataset provides information on economic indicators such as inflation, unemployment, GDP contributions by sector, nominal GDP, real GDP, and government debt from 1990 to 2022.

### Columns
- **Year:** The year the data was collected.
- **Inflation rate:** Annual inflation rate.
- **Unemployment rate:** Percentage of the labor force unemployed.
- **Government debt:** Total government debt.
- **Sector contributions:** Contributions of Agriculture, Industry, and Services to GDP.
- **Nominal GDP:** GDP at current market prices.
- **Real GDP:** GDP adjusted for inflation.

---

## Data Cleaning and Preparation
Before analysis, the following steps were taken:
- **Standardized Column Names:** Ensured consistency across datasets.
- **Handled Missing Data:** Filled or removed missing/redundant data.

---

## Exploratory Data Analysis (EDA)

### 1. Inflation & Unemployment Trends
- **Visualization:** Line charts were used to show trends over time.
- **Insights:**
  - Inflation and unemployment rates showed significant fluctuations, especially in the 2000s and 2010s.
  - Inflation is more volatile, while unemployment trends show a gradual rise over the years.

### 2. Sectoral Contributions to GDP
- **Visualization:** Stacked bar/area charts illustrate sector contributions over time.
- **Key Observations:**
  - The **Services** sector consistently grew, becoming the largest contributor to GDP.
  - The **Agriculture** sector's share decreased, while the **Industry** sector remained relatively stable.

### 3. Debt-to-GDP Ratio
- **Visualization:** Line charts were used to show changes in the Debt-to-GDP ratio.
- **Insights:**
  - The ratio exceeded 70% in the early 1990s, then fell in the mid-1990s.
  - A rise was observed from 2006, reaching 37.97% by 2022, indicating increased reliance on debt.

### 4. Unemployment Rate Trends
- **Visualization:** Line charts tracked unemployment rates from 1990 to 2022.
- **Insights:**
  - Stability in unemployment was noted during the 1990s and early 2000s.
  - A gradual increase started in 2005, with significant spikes from 2015 to 2020.
  - A recovery trend appeared in 2022.

---

## SQL Queries and Calculations

### 1. Debt-to-GDP Ratio Calculation
- **Purpose:** Calculate the Debt-to-GDP ratio for each year.
- **Key Output:** Year, government debt, nominal GDP, and calculated ratio as a percentage.
- **Explanation:** Sorting by year allows for chronological trend analysis.

### 2. Inflation & Unemployment Trends
- **Purpose:** Retrieve inflation and unemployment rates for each year.
- **Key Output:** Year, inflation rate, and unemployment rate.
- **Explanation:** Sorting by year is essential for identifying trends.

### 3. Sector Contributions to GDP
- **Purpose:** Calculate year-over-year growth rates for Agriculture, Industry, and Services contributions to GDP.
- **Key Output:** 
  - Year
  - Sectoral contributions
  - Previous year’s contributions (using `LAG`)
  - Growth rates as percentages.
- **Explanation:** The `LAG` function allows for year-over-year comparisons to identify shifts in sectoral performance.

### 4. Unemployment Rate Analysis
- **Purpose:** Analyze year-over-year unemployment trends.
- **Key Output:** 
  - Year
  - Current unemployment rate
  - Previous year’s rate (`LAG`)
  - Rate change percentage.
- **Explanation:** Percentage changes highlight periods of labor market stability and shifts over time.

---

## Conclusion
This project provides insights into Nigeria’s economic trends over three decades using SQL and data visualization. Key findings include sectoral shifts in GDP contributions, evolving unemployment patterns, and an increasing reliance on debt. These insights can inform policy decisions and economic strategies for future growth.


