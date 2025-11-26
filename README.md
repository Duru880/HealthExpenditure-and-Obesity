# Project Proposal: Health Expenditure and Obesity

## 1. Overview

This project examines the relationship between **health expenditure per capita** and **adult obesity rates** across countries from **1990 to 2023**. The main goal is to see whether countries that spend more on healthcare tend to have higher or lower obesity prevalence.

The analysis focuses on **association**, not causation. Obesity is influenced by many factors (income, lifestyle, culture, environment), so the project is about exploring global patterns rather than proving a direct causal effect.

---

## 2. Data Description

All datasets are obtained from **Our World in Data (OWID)**, which compiles information from:

- **Obesity Rates**: WHO Global Health Observatory, via OWID  
- **Health Expenditure per Capita**: WHO / World Bank, via OWID  
- **GDP per Capita**: World Bank, via OWID  
- **Urban Population (% of total population)**: World Bank, via OWID  
- **Human Development Index (HDI)**: UNDP, via OWID  

### Variables used in the analysis

After cleaning and renaming, the analytical dataset will include:

- `Country` – country name  
- `Year` – calendar year  
- `ObesityRate` – prevalence of obesity among adults (BMI ≥ 30, %, age-standardized)  
- `HealthExpenditure` – per capita health spending (current international-$ or constant 2021 international-$)  
- `GDPperCapita` – GDP per capita (constant international-$)  
- `Urbanization` – urban population as a share of total population (%)  
- `HDI` – Human Development Index (0–1 scale)

All datasets are merged by **(Country, Year)**.

---

## 3. Research Question

**Main Research Question**

> Is there a statistically significant association between *health expenditure per capita* and *adult obesity rates* across countries?

**Sub-questions**

- Do higher levels of health expenditure per capita correspond to higher or lower obesity rates?
- Does the relationship remain after accounting for:
  - GDP per capita,
  - Urbanization rate,
  - Human Development Index (HDI)?

---

## 4. Methodology

### 4.1 Data Cleaning

Main steps:

1. **Import and inspect data**  
   - Load each CSV into a separate pandas DataFrame.  
   - Use `.info()` and `.describe()` to understand variable types and ranges.

2. **Handle missing values**  
   - Drop rows with missing values in the key variables used in the regression (obesity, health expenditure, GDP, urbanization, HDI).  
   - Optionally restrict the analysis to years where most countries have non-missing observations (e.g. 1990–2023).

3. **Standardize identifiers**  
   - Ensure country names or codes match across datasets.  
   - Keep only country-year observations that appear in all datasets.

4. **Create final analytical dataset**  
   - Merge datasets by `Country` and `Year`.  
   - Keep only the variables required for exploratory analysis and modeling.

### 4.2 Exploratory Data Analysis (EDA)

Planned EDA steps:

- **Summary statistics**
  - Compute mean, median, standard deviation and quantiles for all main variables.
- **Time trends**
  - Global trend in adult obesity rates over time.
  - Global trend in average health expenditure per capita.
- **Scatter plots**
  - Obesity rate vs. health expenditure per capita.
  - Obesity rate vs. GDP per capita.
  - Obesity rate vs. urbanization.
  - Obesity rate vs. HDI.
- **Correlation matrix**
  - Compute the correlation matrix between all continuous variables.
  - Visualize it with a heatmap to see which variables move together.

These steps will help to understand the basic patterns and potential relationships before running any statistical models.

### 4.3 Statistical Model

To formally evaluate the association between health expenditure and obesity, the project will use a **multiple linear regression** model:

\[
\text{ObesityRate}_{i,t} = \beta_0
+ \beta_1 \cdot \text{HealthExpenditure}_{i,t}
+ \beta_2 \cdot \text{GDPperCapita}_{i,t}
+ \beta_3 \cdot \text{Urbanization}_{i,t}
+ \beta_4 \cdot \text{HDI}_{i,t}
+ \epsilon_{i,t}
\]

Where:

- \( \text{ObesityRate}_{i,t} \): adult obesity rate in country \( i \) at year \( t \)  
- \( \text{HealthExpenditure}_{i,t} \): health expenditure per capita  
- \( \text{GDPperCapita}_{i,t} \): GDP per capita  
- \( \text{Urbanization}_{i,t} \): share of population living in urban areas  
- \( \text{HDI}_{i,t} \): Human Development Index  
- \( \epsilon_{i,t} \): error term  

The key parameter of interest is **\( \beta_1 \)**, which measures the association between health expenditure and obesity after controlling for other factors.

---

## 5. Expected Outcomes

Several outcomes are possible:

- **Positive association**  
  - Countries with higher health expenditure per capita may also be richer and more urbanized, which can be linked to more sedentary lifestyles and higher obesity rates.

- **Negative association**  
  - Higher health spending could mean stronger preventive care, better health education and more effective obesity treatment, leading to lower obesity prevalence.

- **No clear association**  
  - Obesity might be driven mainly by unobserved cultural and lifestyle factors that are not fully captured in the model.

Any of these results would be informative for understanding how healthcare investment relates to obesity at the country level.

---

## 6. Limitations

- **Ecological data**  
  - The analysis uses country-level data, so results cannot be interpreted as individual-level effects.

- **Correlation, not causation**  
  - The observational nature of the data means that we cannot claim that health expenditure causes changes in obesity.

- **Unobserved factors**  
  - Important determinants of obesity (diet, physical activity, food prices, cultural norms) are not included in the model.

- **Data comparability**  
  - Measurement methods and coverage may differ across countries and over time.

These limitations will be clearly acknowledged when interpreting the results.

---

## 7. Contribution

This project contributes by combining multiple international datasets to explore how **national health expenditure** is related to a major public health challenge: **rising obesity rates**.

The findings may be useful for:

- Understanding whether increased healthcare investment is associated with improvements in population health, and  
- Informing discussions about the role of prevention and lifestyle factors within health systems.
