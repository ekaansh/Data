# What Drives the Price of a Car?

## Overview
This project analyzes a used-car dataset (~426K vehicles scraped from Craigslist) to
identify the factors that most influence price, and translates the results into
actionable recommendations for a used-car dealership fine-tuning its inventory. The work
follows the **CRISP-DM** framework (Business Understanding → Data Understanding → Data
Preparation → Modeling → Evaluation → Findings).

## Link to Notebook
[View the full analysis notebook →](./car_price_analysis.ipynb)

## Summary of Findings
- **Car age and odometer are the strongest price drivers.** Newer, lower-mileage cars
  command the highest prices; both effects are strongly negative as they increase.
- **Vehicle type and drivetrain matter.** Trucks, pickups, and 4WD / diesel vehicles
  retain value best; older front-wheel-drive compacts sit at the low end of the market.
- **Condition and fuel type produce meaningful premiums.** Verified "excellent" / "like
  new" condition and diesel / electric fuel are associated with higher prices.
- A **tuned Ridge regression** on log-price (5-fold cross-validation with a grid-searched
  regularization strength) was the best-performing linear model, evaluated primarily by
  **RMSE**, with R² and MAE reported as supporting metrics. Random Forest and Gradient
  Boosting ensembles were also fit for comparison.

## Recommendations to the Dealership
1. Prioritize newer, low-mileage inventory — these attributes move price the most.
2. Stock trucks / pickups and 4WD / diesel vehicles where local demand supports it.
3. Document vehicle condition accurately to justify premium pricing.
4. Discount older, high-mileage FWD compacts to move them faster.

## Next Steps
- Tune the tree-based ensembles (grid/random search over `n_estimators`, `max_depth`,
  learning rate) to push accuracy further.
- Reincorporate `model` and `region` via target encoding rather than dropping them.
- Refine outlier-removal thresholds with dealer domain knowledge.
- Add permutation importance or SHAP values for a more robust, direction-aware view of
  feature effects in the tree models.

## Repository Structure
```
what-drives-the-price-of-a-car/
├── README.md                  # this file
├── car_price_analysis.ipynb   # full CRISP-DM analysis notebook
└── data/
    └── vehicles.csv            # dataset (from course starter zip)
```

## How to Run
1. Make sure `vehicles.csv` is in the `data/` folder alongside the notebook.
2. Open `car_price_analysis.ipynb` and run all cells top to bottom.

Requires: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`.
