# Economic Analysis of Nigeria Using SQL and Data Visualization  

### Project Overview

#### Objective
The goal of this project was to analyze Nigeria's economic data over the past few decades, focusing on key indicators such as inflation, unemployment, sector contributions to GDP, and government debt. The analysis utilized SQL for data extraction and manipulation, alongside data visualization tools to provide insights into the country’s economic performance from 1990 to 2022.

#### Key Analysis Areas
- **Inflation and Unemployment Trends**: Examining the relationship between inflation and unemployment rates over time.
- **Sectoral Contributions to GDP**: Investigating how the sectors of Agriculture, Industry, and Services have contributed to Nigeria's GDP.
- **Debt-to-GDP Ratio**: Analyzing Nigeria’s growing government debt relative to GDP over time.

### Data Overview

The data for this project came from two main sources:

- **Nigeria Economy - Data Prepared by Alaoh Sodiq.xlsx**
  These datasets provided information about various economic indicators, including inflation, unemployment, GDP contributions by sector, nominal GDP, real GDP, and government debt from 1990 to 2022.

#### Columns:
- **Year**: The year the data was collected.
- **Inflation rate**: Annual inflation rate.
- **Unemployment rate**: The percentage of the labor force that is unemployed.
- **Government debt**: The total government debt.
- **Sector contributions**: Contribution of Agriculture, Industry, and Services to the GDP.
- **Nominal GDP**: GDP at current market prices.
- **Real GDP**: GDP adjusted for inflation.

### Data Cleaning and Preparation
Before beginning the analysis, the following steps were performed:
- **Standardized column names**: Ensured column names are consistent across both datasets.
- **Handled missing data**: Filled or removed any missing or redundant data.

### Exploratory Data Analysis (EDA)

#### Inflation & Unemployment Trends
The trends of inflation and unemployment rates were visualized using a line chart, tracking how these indicators have evolved over time. Insights:
- Inflation and unemployment rates fluctuate significantly, with notable spikes in the 2000s and 2010s.
- Inflation appears more volatile, while unemployment shows a gradual increase.

#### Sectoral Contribution to GDP
A stacked bar chart or area chart was used to visualize how the contributions of Agriculture, Industry, and Services to GDP have changed. Key observations:
- The Services sector shows consistent growth and is the largest contributor to GDP.
- Agriculture and Industry contributions have fluctuated, with Agriculture's share decreasing over time while Industry's share has remained relatively stable.

#### Debt-to-GDP Ratio
The Debt-to-GDP ratio was calculated and visualized using a line chart. Insights:
- The ratio was above 70% in the early 1990s but decreased significantly in the mid-1990s.
- From 2006 to 2015, the ratio began to rise, reaching about 23.7% by 2015.
- The ratio continued to rise between 2016 and 2022, reaching 37.97% by 2022, indicating increasing reliance on debt.

#### Unemployment Rate Trends
The trends in unemployment rates were visualized using a line chart, highlighting key periods of stability, growth, and fluctuations in the labor market over the years. Insights:
- The unemployment rate remained stable from 1990 to the early 2000s, with minor fluctuations.
- A gradual increase began in 2005, indicating a shift in labor market dynamics.
- Significant spikes were observed between 2015 and 2020, reflecting economic challenges, including global disruptions.
- A slight recovery trend appeared by 2022, suggesting potential improvements in employment opportunities.

### SQL Queries and Calculations

#### 4.1 Debt-to-GDP Ratio Calculation
The formula for calculating the Debt-to-GDP ratio is:(Government Debt / Nominal GDP) * 100

    ``sql
        SELECT
           Year,
           Government_Debt,
           Nominal_GDP,
           (Government_Debt / Nominal_GDP) * 100 AS Debt_to_GDP_Ratio
        FROM `osose1.nigeria_economy1.economy_analysis`
        ORDER BY Year;

4.2 Inflation & Unemployment Trends
SQL query to analyze the trends in inflation and unemployment rates:

    ``sql
        SELECT
           Year,
           Inflation_rate,
           Unemployment_rate,
           LAG(Inflation_rate) OVER (ORDER BY Year) AS Previous_Inflation,
           (Inflation_rate - LAG(Inflation_rate) OVER (ORDER BY Year)) / LAG(Inflation_rate) OVER (ORDER BY Year) * 100 AS Inflation_Growth_Rate,
           LAG(Unemployment_rate) OVER (ORDER BY Year) AS Previous_Unemployment,
           (Unemployment_rate - LAG(Unemployment_rate) OVER (ORDER BY Year)) / LAG(Unemployment_rate) OVER (ORDER BY Year) * 100 AS Unemployment_Growth_Rate
        FROM `osose1.nigeria_economy1.economy_analysis`
        ORDER BY Year;


