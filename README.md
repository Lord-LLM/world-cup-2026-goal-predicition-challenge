# World Cup 2026 Goal Prediction Challenge

Solution repo for the [World Cup 2026 Goal Prediction Challenge](https://zindi.africa/competitions/world-cup-2026-goal-prediction-challenge) on Zindi — a community challenge to predict team performance at the FIFA World Cup 2026.

## Challenge Overview

Using historical FIFA World Cup data, the task is to build a model that predicts, for each participating team:

1. **Total goals scored** during the FIFA World Cup 2026.
2. **Stage reached** at the tournament's end — Group Stage, Round of 32, Round of 16, Quarter-finals, Semi-finals, Runner-up, or Champion.

This is a **closed-data challenge**: only the provided [Fjelstul World Cup Database](https://github.com/jfjelstul/worldcup) (CC-BY-NC-SA 4.0) may be used prior to the tournament start. External datasets, pre-computed ratings, betting odds, and web-scraped data are not permitted — all features must be derived from the challenge dataset itself. Penalty shoot-out goals are excluded from the goals target.

## Evaluation

The competition uses a **multi-metric evaluation**, combining two tasks:

| Task | Metric | Weight |
|---|---|---|
| Goals prediction | Root Mean Squared Error (RMSE) | 60% |
| Stage reached prediction | F1 Score | 40% |

Lower RMSE and higher F1 both indicate stronger performance.

## Data

| File | Description |
|---|---|
| `Fjelstul World Cup Database` | Historical team-level records from FIFA Men's World Cup tournaments; used as the training table |
| Test set | Teams participating in the FIFA World Cup 2026, to which the trained model is applied |
| `sample_submission.csv` | Example submission format — row order doesn't matter, but the `ID` and column headers must match exactly |

Data source: Fjelstul World Cup Database by Joshua C. Fjelstul, Ph.D., licensed [CC-BY-NC-SA 4.0](https://github.com/jfjelstul/worldcup).

## Repository Structure

```
.
├── data/               # Raw and processed competition data
├── notebooks/          # Exploration, feature engineering, modeling notebooks
├── src/                # Reusable data/feature/model code
├── submissions/        # Generated submission.csv files
└── README.md
```

## Approach

- **Feature engineering** from historical team-level records (e.g. past performance, squad/tournament stats available in the Fjelstul database).
- **Goals model** — regression, evaluated via RMSE.
- **Stage model** — classification over the seven possible finishing stages, evaluated via F1.

*(Update this section with the specific models, features, and validation strategy used as the solution develops.)*

## Getting Started

### Dependencies

```bash
pip install pandas numpy scikit-learn
```
*(Add/remove libraries as the modeling stack is finalized — e.g. `lightgbm`, `xgboost`, `catboost`.)*

### Running

1. Download the competition data from Zindi and place it in `data/`.
2. Run the notebooks/scripts in order to generate features, train models, and produce predictions.
3. The final step writes a submission file in the format specified by `sample_submission.csv`.

## Submission

Predictions are written to a CSV file matching the required `ID` and column headers, ready for submission to the [Zindi leaderboard](https://zindi.africa/competitions/world-cup-2026-goal-prediction-challenge).

## License

Data used under CC-BY-NC-SA 4.0 per the Fjelstul World Cup Database terms. Code in this repository is licensed separately — add a `LICENSE` file as appropriate.