## Loan Default Prediction — Advanced Data Analysis
**Course:** IB98D0 Advanced Data Analysis — MSc Business Analytics
**Tools:** Python, PyTorch, Scikit-learn, SciPy
**Type:** Individual assignment

### Problem
Consumer lending companies face a fundamental trade-off: approving too many loans
increases default exposure, while approving too few sacrifices profitable revenue. Using
2012–2013 LendingClub data, this project builds a sequential analytical pipeline to
improve loan approval policy beyond simple rule-based thresholds.

### Approach

**1. A/B Testing of Loan Review Policies**
- Designed two rule-based policies: Policy A (lenient — DTI ≤30, grades A–F) vs
  Policy B (strict — DTI ≤20, grades A–C only)
- Primary metric: average net return per application
- Welch t-test confirmed Policy A significantly outperformed Policy B
  (£949.65 vs £423.49 per application; p < 2.2×10⁻¹⁶; 95% CI: [£471.77, £580.54])

**2. Borrower Segmentation via K-Means Clustering**
- Selected 8 financial features across three risk dimensions: borrowing capacity,
  debt load, and credit behaviour. Excluded target variable to prevent leakage
- Mahalanobis distance outlier removal; Ward's linkage confirmed k=4
- Identified four borrower segments with distinct risk profiles:

| Segment | N | Avg Income | Default Rate |
|---|---|---|---|
| Prime Borrowers | 11,046 | £69,898 | 9.8% |
| High Debt-Burden | 10,934 | £69,685 | 15.3% |
| Wealthy but Aggressive | 10,272 | £102,912 | 17.8% |
| The Strugglers | 17,142 | £48,742 | 18.3% |

- Key finding: neither policy captured revolving utilisation risk — the dominant
  default driver among The Strugglers (largest segment at 17,142 borrowers)

**3. Deep Learning for Default Prediction (PyTorch)**
- Binary classification: predict loan default from 17 origination-time features
- 48,168 complete cases; 70/15/15 stratified train/validation/test split
- Dense Neural Network: funnel architecture (128→64→32 neurons) with
  BatchNorm, ReLU, Dropout, BCEWithLogitsLoss
- Class imbalance (85/15) handled via random undersampling to 50/50
- 5-round hyperparameter tuning: architecture, learning rate, weight decay,
  batch size, dropout rate

### Results

| Segment | AUC | F1 | Recall |
|---|---|---|---|
| Prime Borrowers | 0.62 | 0.61 | 0.69 |
| High Debt-Burden | 0.65 | 0.64 | 0.67 |
| Wealthy but Aggressive | 0.67 | 0.63 | 0.70 |
| The Strugglers | 0.68 | 0.66 | 0.73 |
| **Overall** | **0.66** | **0.64** | **0.70** |

DNN correctly flagged 70% of defaults overall, and 73% for The Strugglers —
outperforming both rule-based policies on the highest-risk segment.

### Key Insights
- Approval volume, not default avoidance, is the dominant driver of financial return —
  Policy B sacrificed £526/application in foregone revenue for minimal risk reduction
- Borrower risk is multi-dimensional: DTI rules work for High Debt-Burden borrowers
  but are entirely blind to liquidity stress in The Strugglers
- DNN adds genuine discriminative power by learning non-linear interactions between
  revolving utilisation, income, and DTI simultaneously
- Recommended next step: model-based threshold policy with champion/challenger
  randomised trial before full deployment

### Skills Demonstrated
A/B testing, Welch t-test, hypothesis formulation, K-Means clustering,
Mahalanobis outlier detection, deep learning (PyTorch DNN), hyperparameter
tuning, AUC-ROC evaluation, class imbalance handling, business interpretation

📄 [View Full Assignment (PDF)](../../Advanced_Data_Analysis.pdf)
