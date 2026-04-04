## Used Car Price Prediction — Data Mining & Web Analytics
**Course:** MSc Business Analytics, Aston University
**Tools:** Python, SPSS Modeler, Scikit-learn
**Type:** Group project (5 members)

### Problem
The UK used car market is growing while new car demand declines. Dealers need data-driven pricing tools to remain competitive without sacrificing profitability.

### Approach
- Selected 10 features from a cross-sectional used car dataset using random forest feature importances
- Cleaned data: corrected typos, removed negative mileage values, imputed missing values via mode/median
- Conducted univariate, bivariate and correlation analysis to understand price drivers
- Applied K-Means clustering (k=2) to identify two market segments: economy vs premium vehicles
- Trained and tuned four predictive models: KNN, Decision Tree, Random Forest, and ANN (MLP)
- Evaluated all models using MAE against a mean-baseline benchmark of £7,473

### Results

| Model | Testing MAE |
|---|---|
| Baseline (mean) | £7,473 |
| K-Nearest Neighbours | £1,899 |
| Random Forest | £2,558 |
| Neural Network (MLP) | £1,531 |
| **Decision Tree** | **£1,497 ✅** |

Decision Tree (depth=5) selected as final model — best MAE with lowest overfitting gap.

### Key Findings
- Monthly mileage was the dominant price predictor (correlation: −0.95)
- Fuel type strongly associated with price — electric/hybrid commanding significant premiums
- Vehicle age and number of previous owners also significantly influenced pricing
- K-Means clustering confirmed two distinct market segments (economy vs premium)

### Skills Demonstrated
Feature selection, data cleaning, k-means clustering, supervised regression modelling, hyperparameter tuning, MAE-based model comparison, business interpretation

📄 [View Full Assignment (PDF)](../../Final_Report_Predictive_Analytics.pdf)
