# January Flight Delay Prediction and Classification Analysis

Project report for STAT 303-2 (Winter 2026), examining whether U.S. domestic flight arrival delays can be predicted using logistic regression.

**Author:** Sophia Perez

## Overview

This project uses logistic regression to classify whether a U.S. domestic flight will arrive delayed (`ARR_DEL15`). The model is trained on January 2019 flight data and tested on January 2020 flight data to evaluate how well it generalizes to a new year.

Predictors include departure time block, day of week, distance, origin airport, and carrier. Polynomial transformations and interaction terms are explored, and LASSO (L1) regularization with cross-validation is used for variable selection and to reduce overfitting. Model performance is assessed with accuracy, precision, recall, AUC, and the confusion matrix, with particular attention paid to how class imbalance (most flights are on time) affects these metrics. The report also interprets which predictors are associated with higher delay risk and offers recommendations for airline, airport, and business analyst stakeholders.

## Data

Source: [Flight Delay Prediction dataset on Kaggle](https://www.kaggle.com/datasets/divyansh22/flight-delay-prediction), originally collected by the U.S. Bureau of Transportation Statistics.

- `Jan_2019_ontime.csv` — training data (~584,000 flights from January 2019)
- `Jan_2020_ontime.csv` — test data (flights from January 2020)

## Repository Structure

```
.
├── data/
│   ├── Jan_2019_ontime.csv        # training data
│   └── Jan_2020_ontime.csv        # test data
├── notebooks/
│   ├── Project_Code_Template.ipynb    # full analysis code
│   └── Project_Report_Template.ipynb  # written report (narrative + code)
├── htmls/
│   ├── Project_Code_Template.html     # rendered code notebook
│   └── Project_Report_Template.html   # rendered report notebook
└── README.md
```

The `htmls/` folder contains rendered (Quarto-exported) versions of the notebooks in `notebooks/`, matched by filename, for easy viewing without running any code.

## Report Sections

1. Inspiration
2. Stakeholders
3. Task and Metrics
4. Data
5. Prediction (unregularized model, regularization/cross-validation, decision threshold, interpretation)
6. Inference
7. Recommendation to Stakeholders
8. Conclusion

## Key Takeaways

- Evening departures and flights from major hub airports (especially ORD) were associated with higher delay probability.
- Flight distance and most day-of-week effects were not statistically reliable predictors.
- Accuracy stayed high (~81–86%) largely due to class imbalance; AUC and recall remained low, showing limited ability to catch actual delayed flights.
- Regularization improved variable selection, but the model overall explained only a modest share of delay variation — suggesting other operational/environmental factors (e.g., weather, air traffic) matter but weren't captured in this dataset.

## How to Run

1. Clone the repo and make sure `data/Jan_2019_ontime.csv` and `data/Jan_2020_ontime.csv` are present.
2. Open the notebooks in `notebooks/` in Jupyter.
3. Run cells top to bottom — key libraries used: `pandas`, `numpy`, `seaborn`, `matplotlib`, `statsmodels`, `scikit-learn`.

## Viewing Without Running

Open either file in `htmls/` directly in a browser to view the rendered notebook output.
