# Health Expenditure and Obesity  
### DSA210 — Project Proposal & Phase 2 EDA

---

## 1. Overview  
This project examines the relationship between **health expenditure per capita** and **adult obesity rates** across countries from **1990 to 2023**.  
The study focuses on **association**, not causation.

---

## 2. Data Description  
All datasets were obtained from **Our World in Data (OWID)**:

- **Obesity Rates** (WHO)  
- **Health Expenditure** (WHO / World Bank)  
- **GDP per Capita** (World Bank)  
- **UrbanPopulation (%)**  
- **HDI** (UNDP)

### Variables  
- `Country`  
- `Year`  
- `ObesityRate`  
- `HealthExpenditure`  
- `GDPperCapita`  
- `UrbanPopulation`  
- `EducationIndex`

---

## 3. Research Question  

### Main Question  
**Is there a statistically significant association between health expenditure per capita and adult obesity rates?**

### Sub-questions  
- Do higher-spending countries have higher or lower obesity levels?  
- Does controlling for GDP, EducationIndex, and UrbanPopulation change the relationship?

---

## 4. Methodology  

### 4.1 Data Cleaning  
- Loaded raw datasets  
- Inspected types & missing values  
- Handled missing values after merging using row-wise exclusion for regression analysis
- Renamed long OWID variable names  
- Merged datasets  

### 4.2 Exploratory Data Analysis  
- Summary statistics  
- Trend visualizations  
- Scatterplots  
- Correlation heatmap  

### 4.3 Regression Model  
The regression model used:

```
ObesityRate = β0  
             + β1 * HealthExpenditure  
             + β2 * GDPperCapita  
             + β3 * UrbanPopulation  
             + β4 * EducationIndex  
             + ε
```

---

## 5. Expected Outcomes  
Possible findings include:

- Positive association  
- Negative association  
- No association  

All outcomes provide meaningful insights into global health trends.

---

## 6. Limitations  
- Ecological fallacy  
- Correlation ≠ causation  
- Missing lifestyle factors  
- Cross-country measurement differences  

---

## 7. Contribution  
This project synthesizes multiple international datasets to explore how health expenditure relates to global obesity patterns.

---


# Phase 2 — Exploratory Data Analysis (EDA) & Hypothesis Testing

## 1. Data Collection  
Datasets used:

- `obesity.csv`  
- `healthexp.csv`  
- `gdp.csv`  
- `urbanization.csv`  
- `education.csv`  

Location: **data/**  

---

## 2. Data Cleaning Summary

The data cleaning process was performed in EDA_and_Hypothesis.ipynb and consisted of the following steps:

- Raw datasets were inspected individually to understand their structure and missingness patterns.
- Variable names were renamed for consistency across datasets.
- All datasets were merged first using common keys (Entity, Code, and Year).
- Missing values were handled after merging to avoid discarding valid observations present in some datasets but missing in others.

The final variables used in the analysis are:

- ObesityRate
- HealthExpenditure
- GDPperCapita
- UrbanPopulation
- EducationIndex

## 3. Exploratory Data Analysis  

### 3.1 Summary Statistics  
Descriptive statistics generated for all numeric variables.

### 3.2 Trend Analysis  
- Global obesity trend  
- Global health expenditure trend  

### 3.3 Scatter Plots  
Examined relationships between obesity and:

- Health Expenditure  
- GDP per Capita  
- UrbanPopulation  
- Education Index  

### 3.4 Correlation Matrix  
Heatmap findings:

- **UrbanPopulation** → strong positive  
- **EducationIndex** → moderate positive  
- **HealthExpenditure** → weak negative  
- **GDPperCapita** → negative  

---

## 4. Hypothesis Testing  

The hypotheses were tested using correlation analysis and linear regression models.

**H₀ (Null Hypothesis):**  
There is no statistically significant relationship between health expenditure per capita
and adult obesity rates across countries.

**H₁ (Alternative Hypothesis):**  
There is a statistically significant relationship between health expenditure per capita
and adult obesity rates across countries.

---

## 5. Regression Analysis  

### 5.1 Simple Linear Regression  
```
ObesityRate = β0 + β1 * HealthExpenditure
```

### 5.2 Multiple Linear Regression  
```
ObesityRate = β0
             + β1 * HealthExpenditure
             + β2 * GDPperCapita
             + β3 * UrbanPopulation
             + β4 * EducationIndex
             + ε
```

### Findings  
- **HealthExpenditure:** weak negative, significant  
- **GDPperCapita:** negative, significant  
- **UrbanPopulation:** strong positive  
- **EducationIndex:** large positive (likely multicollinearity)  

### Model Performance  
- **R² ≈ 0.24**

### Interpretation  
Obesity is more strongly linked to **UrbanPopulation** and **EducationIndex/education level** than to health expenditure alone.

### Confounding Variables and Sign Reversal

The change in the sign of the Health Expenditure coefficient between the simple and multiple regression models suggests the presence of confounding variables. In the simple model, health expenditure partly captures income-related effects, as wealthier countries tend to spend more on healthcare and also exhibit higher obesity rates.

Once GDP per capita, UrbanPopulation, and education index are included as control variables, the coefficient of Health Expenditure becomes negative. This indicates that, after accounting for socioeconomic factors, higher health expenditure is associated with lower obesity rates, potentially reflecting the role of preventive healthcare and public health interventions.

GDP per capita and education index therefore act as confounding variables in the relationship between health expenditure and obesity.

# Phase 3 — Machine Learning Analysis

To further evaluate the predictive relationship between obesity rates and socioeconomic indicators, supervised machine learning models were implemented. The goal of this phase is not causal inference but predictive performance comparison.

## Model Setup

The target variable is **ObesityRate**, while the following variables are used as predictors:

- HealthExpenditure  
- GDPperCapita  
- UrbanPopulation  
- EducationIndex  

The dataset was split into training (80%) and test (20%) sets. Model performance was evaluated using **RMSE (Root Mean Squared Error)** and **R² (Coefficient of Determination)**.

## Model Performance Summary

### Linear Regression (Baseline Model)

- **RMSE ≈ 9.74**  
- **R² ≈ 0.24**

The Linear Regression model explains approximately 24% of the variance in obesity rates. This level of performance is expected for a baseline linear model and indicates limited predictive power, suggesting that linear assumptions are insufficient to fully capture the relationship between obesity and the selected socioeconomic variables.

### Random Forest Regression

- **RMSE ≈ 4.14**  
- **R² ≈ 0.86**

The Random Forest model substantially outperforms Linear Regression, explaining approximately 86% of the variance in obesity rates. The lower RMSE also indicates significantly improved prediction accuracy.

## Interpretation

The large performance gap between Linear Regression and Random Forest Regression suggests that the relationship between obesity rates and socioeconomic indicators is largely non-linear. Ensemble-based models such as Random Forest are better suited to capturing complex interactions and non-linear patterns in the data.

Overall, Random Forest Regression provides stronger explanatory and predictive performance for this dataset and is therefore more appropriate for modeling obesity rates compared to a simple linear baseline model.

## Conclusion

This project investigated the relationship between health expenditure per capita and adult obesity rates across countries using global data from 1990 to 2023. By combining multiple international datasets, the analysis aimed to understand how health spending relates to obesity when broader socioeconomic factors are taken into account.

Exploratory data analysis revealed clear global trends, including a steady increase in obesity rates over time and strong associations between obesity and variables such as urban population and education level. Correlation analysis suggested that health expenditure alone has a relatively weak relationship with obesity, while socioeconomic structure appears to play a more prominent role.

Regression analysis further supported these findings. Simple linear regression showed a weak association between health expenditure and obesity, while multiple regression highlighted the importance of controlling for confounding variables such as GDP per capita, urbanization, and education index. The observed sign reversal of the health expenditure coefficient indicates that income and development-related factors partially confound the relationship between health spending and obesity outcomes.

In the final phase of the project, machine learning models were applied to evaluate predictive performance rather than causal inference. While Linear Regression provided a useful baseline with limited explanatory power, Random Forest Regression substantially improved prediction accuracy. This result suggests that the relationship between obesity and socioeconomic indicators is largely non-linear and involves complex interactions that cannot be adequately captured by linear models.

Overall, the findings indicate that obesity is more strongly associated with structural and demographic factors than with health expenditure alone. Increasing healthcare spending may contribute to lower obesity rates only when accompanied by broader socioeconomic conditions, such as education and urban development. Future research could extend this work by incorporating lifestyle variables, dietary patterns, or policy-level indicators to further improve both interpretability and predictive performance.
