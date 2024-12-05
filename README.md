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

4.3 Sector Contributions to GDP
SQL query for calculating sector contributions to GDP:

     ``sql
    SELECT
       Year,
       Agriculture_to_GDP / Nominal_GDP * 100 AS Agriculture_Contribution,
       Industry_to_GDP / Nominal_GDP * 100 AS Industry_Contribution,
       Services_to_GDP / Nominal_GDP * 100 AS Service_Contribution
    FROM `osose1.nigeria_economy1.economy_analysis`
    ORDER BY Year;

4.4 Unemployment Rate Analysis
SQL query for unemployment rate analysis:

    ``sql
    SELECT year, AVG(unemployment_rate) AS avg_unemployment
    FROM `osose1.nigeria_economy1.economy_analysis`
    GROUP BY year
    ORDER BY year;

    
#### Data Visualization
#### 1. Inflation & Unemployment Trends (Line Chart)
Data Source: Extracted inflation and unemployment data.
Chart Type: Line chart.
X-Axis: Year.
Y-Axis: Inflation rate and Unemployment rate.
Insight: Revealed the volatility of inflation and rising unemployment trends.


#### 2. Sectoral Contribution to GDP (Stacked Bar or Area Chart)
Data Source: Sectoral contributions (Agriculture, Industry, Services).
Chart Type: Stacked bar or area chart.
X-Axis: Year.
Y-Axis: Percentage of GDP contribution.
Insight: The Services sector dominates Nigeria's GDP, with Agriculture showing a downward trend.

#### 3. Debt-to-GDP Ratio (Line Chart)
Data Source: Debt-to-GDP ratio.
Chart Type: Line chart.
X-Axis: Year.
Y-Axis: Debt-to-GDP Ratio.
Insight: The chart illustrated how Nigeria's debt relative to GDP increased significantly after 2015, reflecting fiscal pressure.

#### 4. Unemployment Rate Analysis (Line Chart)
Data Source: Average Unemployment Rate (1990-2022).
Chart Type: Line chart.
X-Axis: Year.
Y-Axis: Average Unemployment Rate.
Insight: Illustrated periods of stability, growth, and significant spikes in unemployment from 2015 to 2020.


#### Insights and Key Findings
Inflation and Unemployment Trends
-Inflation and unemployment rates have shown a volatile and upward trend, especially in the last two decades.
-Inflation was particularly high in 2016 due to the economic recession.
-Unemployment has steadily increased since 2015, likely due to slow job creation and economic instability.


#### Sectoral Contributions to GDP

-The Services sector remains the largest contributor to GDP, signaling Nigeria's shift toward a more service-oriented economy.
Agriculture, once a leading contributor, has seen a steady decline in its share of GDP.


 #### Debt-to-GDP Ratio

Nigeria's debt-to-GDP ratio has increased significantly since 2015, reaching nearly 38% by 2022.
This trend suggests an increased reliance on government borrowing, which may have implications for future fiscal policy.
Unemployment Rate Analysis

#### Interpretation:
-Stability (1990-2004): Minimal variation, reflecting a relatively balanced labor market.
-Growth in Unemployment (2005-2020): Economic challenges, population growth, and structural job market changes contributed to a steady rise.
-Recovery (2021-2022): A decline in unemployment suggests economic recovery efforts may have taken effect post-2020 disruptions.

#### Further Insights
-Fluctuations in Inflation and Unemployment: The trend analysis shows significant fluctuations, particularly in the 2000s and 2010s, aligning with economic events such as oil price drops and global shocks.
-Inflation Volatility: Inflation in Nigeria has been volatile, with noticeable spikes, particularly in 2000 and 2016, due to economic recessions and external shocks.
-Gradual Increase in Unemployment: Unemployment has been on a consistent rise, attributed to factors such as slow economic growth, high population growth, and insufficient job creation.

#### Conclusion:
The analysis provides a comprehensive view of Nigeria's economic performance over the years:

-GDP Growth: Steady growth in GDP until a dip in 2020 due to the COVID-19 pandemic.
-Sectoral Shifts: A shift from agriculture to services, reflecting global economic trends and domestic industrialization.
