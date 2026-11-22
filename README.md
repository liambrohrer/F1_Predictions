# Formula 1 Race Predictions

A machine learning project that uses historical Formula 1 race results and championship standings to predict driver finishing positions. The project retrieves data through the Jolpica-F1 API and FastF1, trains and evaluates regression models, and exports predictions in JSON format for use in a web application.

## Project Overview

The notebook (`fastf1_Predictions_final_v2.ipynb`) contains the complete data collection, preprocessing, modelling, evaluation, and prediction pipeline.

The project has three main objectives:

- **Historical prediction evaluation:** Evaluate how accurately machine learning models can predict race finishing positions using information available from previous races.
- **Latest race predictions:** Generate out-of-sample predictions for the most recently completed race and compare them with actual results.
- **Upcoming race predictions:** Generate finishing-position predictions for the next scheduled Formula 1 race.

## Data Sources

The project uses two primary data sources:

| Source | Purpose |
|---|---|
| [Jolpica-F1 API](https://github.com/jolpica/jolpica-f1) | Historical race results, driver information, constructor information, and championship standings. |
| [FastF1](https://docs.fastf1.dev/) | Formula 1 event schedules and upcoming race information. |

API responses and historical season datasets are cached locally to reduce repeated requests and improve reliability.

## Predictive Modelling

The target variable is `positionOrder`, representing a driver's numerical finishing position.

Six predictor variables are used, each representing information from the driver's previous race:

| Predictor | Description |
|---|---|
| `grid_lag1` | Starting grid position in the previous race. |
| `positionOrder_lag1` | Finishing position in the previous race. |
| `driver_points_per_round_lag1` | Driver championship points per round. |
| `driver_wins_per_round_lag1` | Driver championship wins per round. |
| `constructor_points_per_round_lag1` | Constructor championship points per round. |
| `constructor_wins_per_round_lag1` | Constructor championship wins per round. |

### Models

The notebook implements and evaluates four regression approaches:

- Ridge Regression
- Partial Least Squares Regression (PLS)
- Gradient Boosting Regression
- Multi-layer Perceptron (Neural Network)

Hyperparameter selection for
