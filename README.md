# Predicting Boston Housing Prices

A regression project that builds and tunes a decision-tree model to predict home values in the Boston area, then evaluates how reliable those predictions are.

This is a completed project from Udacity's Machine Learning Nanodegree ("Model Evaluation & Validation"). It's shared here as a portfolio piece, with attribution to Udacity for the dataset, starter code, and project structure.

## A note on the dataset

The Boston housing dataset has a well-known ethical problem: one of its original features (`B`) was derived from the proportion of Black residents by town, and the dataset was in part constructed to study that variable's effect on housing prices. Because of this, scikit-learn removed it in version 1.2, and it is deprecated at the UCI repository.

The version used in this project is a reduced one with only three features — `RM`, `LSTAT`, and `PTRATIO` — and does not include `B`. Even so, `LSTAT` ("percent lower status of the population") is a socioeconomic proxy, so this project is best read as a teaching/learning exercise, not a basis for real-world pricing.

## Overview

The dataset originates from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Housing) and contains data collected in 1978 on homes in suburbs of Boston, Massachusetts. For this project the data was preprocessed by removing outliers and censored values, keeping only the three features above plus the target (`MEDV`), and scaling `MEDV` to account for market inflation.

The notebook walks through:

- **Data exploration** — descriptive statistics on housing prices and a look at how each feature relates to price
- **Model evaluation** — an R² performance metric, and a look at learning curves and model complexity (bias/variance trade-off) across different decision tree depths
- **Model tuning** — grid search with cross-validation to find the optimal `max_depth`
- **Predictions** — applying the tuned model to new client data and discussing whether the predictions are reasonable
- **Discussion** — the limitations of the model and whether it should be trusted in a real-world setting

## Project structure

```
.
├── boston_housing.ipynb   # main notebook: analysis, model, results
├── visuals.py              # helper functions for learning/complexity curve plots
├── housing.csv              # dataset (not included — see below)
└── README.md
```

## Requirements

- Python 3
- numpy
- pandas
- matplotlib
- scikit-learn
- Jupyter Notebook

Install with:

```bash
pip install numpy pandas matplotlib scikit-learn jupyter
```

## Running the project

1. Make sure `housing.csv` is in the same directory as the notebook.
2. Launch Jupyter and open the notebook:

   ```bash
   jupyter notebook boston_housing.ipynb
   ```

3. Run all cells from top to bottom.

## Key results

- The tuned decision tree regressor selected a `max_depth` of 4 via grid search.
- The model produced reasonable predictions for three sample clients, with price ordering that matched intuition from the feature analysis (more rooms, lower poverty level, and a lower student-teacher ratio all correlated with a higher predicted price).

## Limitations

- The data is from 1978 and doesn't reflect current housing markets.
- Only three features are used; real pricing depends on many more factors (e.g. proximity to city center, crime rate).
- A model trained on urban Boston data won't generalize well to rural areas, where buyers may value different things.

## Acknowledgments

- Dataset: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Housing)
- Project template and starter code: Udacity Machine Learning Nanodegree
