## Wage Determinants — Exploratory Data Analysis
**Course:** BBM126 Programming for Data Analytics — MSc Business Analytics, Aston University
**Tools:** Python, Pandas, Seaborn, Matplotlib, Plotly, SciPy, Statsmodels
**Type:** Individual assignment

### Problem
What demographic and human-capital factors drive hourly wage differences across individuals?

### Approach
- Cleaned and imputed a 525-record wage dataset across 7 variables
- Conducted univariate, bivariate and multivariate visualisations to surface distributional patterns
- Applied chi-square test to assess association between gender and marital status
- Conducted Welch's t-test comparing wages between high-education, high-experience males vs females
- Built a multivariate OLS regression model, refined via VIF analysis and p-value filtering
- Final model: hourly_wage = −2.62 + 1.69×gender + 0.51×education + 0.15×experience + 0.78×married

### Key Findings
- Gender was the strongest demographic predictor — males earned £3.60/hr more than females at equivalent education and experience levels
- Each additional year of education added ~£0.51/hr; each year of employment added ~£0.15/hr
- Race and number of dependants were not significant predictors once other variables were controlled
- Model explained ~35% of wage variation (Adj. R² = 0.342)

### Skills Demonstrated
Exploratory data analysis, missing value imputation, hypothesis testing, OLS regression, model refinement, assumption testing

📄 [View Full Assignment (PDF)](../../EDA_Coursework_250301807.pdf)
