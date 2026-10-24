### What Drives the Price of a Home?

**Author:** Ekaansh Anand

#### Executive summary
This project identifies which characteristics of a residential home most strongly influence
its sale price, and how accurately those characteristics can predict a home's market value.
Using the Ames, Iowa housing dataset (1,458 sales described by 79 features), the analysis
cleans the data, explores it, engineers new predictive features, and compares four machine-
learning models. The best models predict a home's sale price with high accuracy — explaining
about **92% of price variation** (R² ≈ 0.92) with a typical error of roughly **$19,400** —
and consistently point to the same handful of drivers: **overall size, quality, and
location**. The result is both an accurate price predictor and a clear, ranked explanation of
*why* homes are worth what they are.

#### Rationale
Buying or selling a home is the single largest financial decision most people ever make, and
pricing it wrong is expensive in both directions. A seller who lists too high watches the home
sit and eventually sell for less; one who lists too low leaves money on the table; a buyer
without a reliable sense of value risks overpaying by tens of thousands of dollars. Most people
rely on an agent's judgment or an opaque online estimate, with little insight into *why* a
number is what it is. This project turns that black box into plain-language answers — how much
quality, size, or neighborhood actually move the price — that a homeowner, buyer, or agent can
act on.

#### Research Question
Which physical and locational characteristics of a residential home most influence its sale
price, and how accurately can those characteristics predict a home's market value?

#### Data Sources
The [Ames, Iowa housing dataset](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
(Kaggle *House Prices – Advanced Regression Techniques*): 1,460 residential sales, each
described by 79 features covering size, quality, age, location, and amenities, with
`SalePrice` as the target.

#### Methodology
- **Data cleaning:** resolved missing values meaningfully (for many features `NaN` means the
  feature is absent, filled as `'None'` or `0`; `LotFrontage` by neighborhood median), removed
  duplicates, and removed two documented outliers. The data was fully complete afterward.
- **Exploratory analysis:** examined the price distribution, feature correlations, and key
  relationships.
- **Feature engineering:** derived `TotalSF`, `TotalBath`, `HouseAge`, `RemodAge`, and amenity
  indicators.
- **Modeling:** compared **Ridge, Lasso, Random Forest, and Gradient Boosting** on
  `log(SalePrice)`, each inside a preprocessing pipeline, with 5-fold cross-validation and
  grid-search hyperparameter tuning.
- **Evaluation metric:** RMSE on `log(SalePrice)` (reported alongside R² and dollar errors).
  RMSE penalizes large dollar misses most heavily, and the log scale keeps the error in
  percentage terms so expensive homes don't dominate it.

#### Results
| Model | Test R² | Typical error (RMSE) |
|---|---|---|
| **Gradient Boosting** | **0.917** | ~$19,400 |
| Lasso | 0.916 | ~$19,400 |
| Ridge | 0.910 | ~$20,100 |
| Random Forest | 0.875 | ~$23,600 |

- **Gradient Boosting and Lasso tied for best accuracy** (R² ≈ 0.92). Because Lasso is nearly
  as accurate *and* fully interpretable — it automatically selected 111 of 304 features and
  zeroed out the rest — it is the most useful model for this business question.
- **Size dominates:** total square footage, above-grade living area, and overall quality are
  the strongest positive drivers of price.
- **Location is decisive:** premium neighborhoods (e.g., Crawford, Stone Brook) add a clear
  premium, while commercial zoning and lower-value neighborhoods subtract.
- **Condition and age:** good functional condition and quality finishes raise price; greater
  house age lowers it.
- The regularized and tree-based models **broadly agreed** on these drivers, which increases
  confidence in the findings.

#### Important findings (for a non-technical audience)
1. **Quality and finished space matter more than raw square footage alone** — overall quality
   is one of the single biggest levers on a home's value.
2. **Location is largely fixed but decisive** — neighborhood should carry heavy weight when
   judging whether a price is fair.
3. **The model is accurate enough to be a practical pricing check** — predicting sale price
   within about $19,000 on average, enough to flag listings that are clearly over- or
   under-priced.

#### Next steps
- Validate the model on a current, local market (e.g., recent Zillow or county records) to
  test whether the Ames patterns generalize.
- Add permutation importance or SHAP values for an even more robust driver ranking.
- Package the model behind a simple interface so a non-technical user can enter a home's
  features and get an instant, explainable price estimate.

#### Outline of project

- [Notebook 1 — EDA & Baseline Model](./capstone_eda.ipynb)
- [Notebook 2 — Modeling & Final Analysis](./capstone_modeling.ipynb)

##### Contact and Further Information
Ekaansh Anand — ekaansh.anand@gmail.com
