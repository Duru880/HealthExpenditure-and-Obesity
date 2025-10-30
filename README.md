# Project Proposal: Health Insurance Coverage and Obesity

## 1. Overview
This project aims to investigate the relationship between **health insurance coverage** and **obesity prevalence** across countries between **2010 and 2023**.  
The main research question is whether wider access to health insurance is associated with higher or lower obesity rates in the population.  
The motivation is to understand if better healthcare access promotes healthier lifestyles or, conversely, reduces individual incentives to maintain health (a possible “moral hazard” effect).

---

## 2. Data Description
- **Obesity Rates:** Adult obesity rate (% of adults with BMI ≥ 30) — *World Health Organization (WHO)*, *Our World in Data*  
- **Health Coverage:** % of population covered by health insurance — *World Bank*, *OECD Health Statistics*  
- **Health Expenditure:** Per capita health expenditure (USD, PPP) — *World Bank*  
- **Control Variables:** GDP per capita, urbanization rate, education index — *World Bank*, *UN Data*  
- **Unit:** Country-year (panel data)  
- **Period:** 2010–2023  

---

## 3. Data Collection Plan
1. **Retrieve datasets** from WHO, OECD, and World Bank open data portals.  
2. **Download and merge** all CSV files using ISO-3 country codes.  
3. **Clean and preprocess** (handle missing years, normalize variables).  
4. **Exploratory Analysis:** summary statistics, scatter plots, and correlation heatmaps.  
5. **Modeling:** multiple linear regression of the form  
   \[
   ObesityRate_{i,t} = \beta_0 + \beta_1(InsuranceCoverage_{i,t}) + \beta_2(HealthExpenditure_{i,t}) + \beta_3(GDP_{i,t}) + \epsilon_{i,t}
   \]

---

## 4. Expected Outcomes
- Identify whether expanding health insurance coverage is linked to **lower obesity** (preventive care effect) or **higher obesity** (moral hazard effect).  
- Provide evidence-based insights for health policy and public health planning.  
- Discuss limitations and potential confounding factors (e.g., income inequality, lifestyle differences).

---

## 5. Author
- *[Zeynep Duru Arca]* — Sabancı University


