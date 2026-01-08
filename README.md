# Credit Scoring and Risk Prediction (R)

This project develops an interpretable credit scorecard and an alternative predictive model to estimate the likelihood of credit card default using real customer and repayment history data from Taiwan (NT dollars). The focus is on rigorous data preparation, explainable modelling, and practical evaluation for business use.

## Objectives

- Prepare and transform customer credit data for modelling
- Develop a credit scoring model and scorecard using WOE binning
- Train an additional predictive model to classify “bad” customers (default = 1)
- Compare both approaches from performance and business usability perspectives
- Produce visual and statistical summaries to support risk segmentation decisions

## Dataset Summary

The dataset contains 25 variables:

- ID and demographics (6): ID, LIMIT_BAL, SEX, EDUCATION, MARRIAGE, AGE
- Repayment status (6): PAY_0, PAY_2, PAY_3, PAY_4, PAY_5, PAY_6
- Bill amounts (6): BILL_AMT1 to BILL_AMT6
- Payment amounts (6): PAY_AMT1 to PAY_AMT6
- Target (1): default.payment (1 = default next month, 0 = non default)

Notes on repayment history:

- Time moves from right to left (April to September 2005).
- Payments are typically recorded the following month (for example April bill aligns with May payment).
- Negative BILL_AMT values can occur and indicate overpayment, not an error.
- Repayment status variables (PAY_) may be inconsistent and require careful treatment.

## Methodology

1. Data preparation
   - Validate ranges and handle invalid or unknown categories
   - Treat negative bills as valid values and check for negative payments
   - Address known inconsistencies in PAY_ variables
   - Create modelling-ready formats for categorical variables

2. Feature engineering
   - Payment to bill ratios by month (with safe handling of zeros and negatives)
   - Utilisation proxy features (bill amount relative to credit limit)
   - Trend and volatility features across recent months (optional)

3. Scorecard model
   - Weight of Evidence binning and Information Value assessment
   - Logistic regression using WOE transformed features
   - Score scaling and scorecard generation
   - Model quality reporting (AUC, KS, Gini, calibration checks)

4. Predictive model
   - Train an alternative classifier (for example random forest, gradient boosting, or regularised logistic regression)
   - Compare performance using out of sample evaluation
   - Review stability, interpretability, and operational suitability

5. Comparison and business discussion
   - Compare discrimination, calibration, and error trade offs
   - Discuss interpretability and governance considerations
   - Segment customers into risk bands and describe population insights

## Tools and Packages

- R
- scorecard
- tidyverse
- caret or tidymodels
- pROC
- ggplot2
