# Credit Risk Analysis

This project aimed to model the credit risk data and predict if the customer is default on the loan next month.

## Installation requirement

```
pip install -r requirements.txt
```

## Feature analysis

The features of the raw data (credit_risk_data.csv) contain unexpected value in education column (5 and 6) and many zeros in marriage column. Four approaches were tried on the raw data:

- T1: treat all the unreasonable data as missing data and labeled 0.
- T2: treat all the unreasonable data as most frequent value in this column
- T3: treat all the unreasonable data as missing data and labeled 0, and for pay status, set 0 for all negatives and 1 for positives
- woe: use woe to transform all the features (transformed risk data and relevant processing code can be found in 'woe_transformation'). Details of woe_transformation package can be found in [https://github.com/boredbird/woe.git.]

## Modelling

Logistic regression and XGBoost classifier were used to model the data. Cross valudation was conducted on both models to adjust hyperparameters.

### Model performance

The model perfomance was compared based on auc under pr curve and recall value becasue the high number of false negatives will be more risky (personally).

- Both models showed better performance with woe transformation
- XGBoost classifier showed better performance than logistic regression model in auc under pr curve (0.56) and recall value (0.90).
- XGBoost classifier with woe transformation was found the best perfromance

### Model site and usage
- XGBoost classifier with woe transformation was stored as dict with key "xgb_model" in "./XGBoost/woe_data_model/model_woe_xgb.py"
- use woe to transform new raw data feature can be refered to teh code under Ne data transform in "woe_transformation/transform_data.ipynb"

## Recommendations
- worth checking the acceptence of the precision value
- try other models that may have better trade-offs between recall and precision

