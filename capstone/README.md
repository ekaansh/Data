### What Drives the Price of a Home?

**Author:** Ekaansh Anand

#### Executive summary
This project investigates which characteristics of a residential home most strongly influence
its sale price, and how accurately those characteristics can predict a home's market value.
Using the Ames, Iowa housing dataset (1,460 sales described by 79 features), the work cleans
and explores the data, engineers new predictive features, and builds a baseline regression
model. The analysis shows that overall quality, total living area, basement/first-floor size,
garage capacity, and neighborhood are the dominant drivers of price. A baseline Ridge
regression on log-transformed sale price explains **91% of the variance** in home prices
(test R² = 0.91), with a typical error of about **$20,000** — a strong benchmark that later,
more sophisticated models will aim to beat.

#### Rationale
Why should anyone care about this question? Buying or selling a home is the single largest
financial decision most people ever make, and mispricing is costly in both directions — a home
listed too high sits unsold, while one listed too low leaves money on the table. Today most
people rely on an agent's judgment or an opaque online estimate with little insight into *why*
a number is what it is. A model that identifies which features drive price, and by how much,
turns that black box into clear guidance a homeowner, buyer, or agent can actually act on.

#### Research Question
Which physical and locational characteristics of a residential home most influence its sale
price, and how accurately can those characteristics predict a home's market value?

#### Data Sources
The [Ames, Iowa housing dataset](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)
(Kaggle *House Prices – Advanced Regression Techniques*): 1,460 residential sales, each
described by 79 explanatory features covering size, quality, age, location, and amenities,
with `SalePrice` as the target variable.

#### Methodology
- **Data cleaning:** resolved missing values meaningfully (for many features `NaN` means the
  feature is absent, filled as `'None'` or `0`; `LotFrontage` filled by neighborhood median),
  removed duplicates, and removed the dataset's documented large-home outliers. The data was
  fully complete after imputation (0 remaining missing values, 0 duplicates).
- **Exploratory data analysis:** examined the target's distribution, feature–price
  correlations, and the relationship of key continuous and categorical variables to sale price.
- **Feature engineering:** derived `TotalSF`, `TotalBath`, `HouseAge`, `RemodAge`, and amenity
  indicators from the raw columns.
- **Baseline modeling:** a Ridge regression on `log(SalePrice)` inside a preprocessing pipeline
  (impute + scale numeric, one-hot encode categorical), evaluated with 5-fold cross-validation.
- **Evaluation metric:** RMSE on `log(SalePrice)`, with R² and MAE as supporting metrics. RMSE
  penalizes large dollar errors most heavily, and working in log space makes the error reflect
  percentage terms so it isn't dominated by the most expensive homes.

#### Results
- **Sale price is strongly right-skewed** (skew 1.88); a log transform makes it near-symmetric
  (skew 0.12), and is used as the modeling target.
- **The strongest price drivers** are overall quality rating (correlation 0.80 with price),
  above-grade living area / `GrLivArea` (0.74), total basement square footage (0.65), garage
  capacity (0.64), and first-floor size (0.63). **Neighborhood** produces large, consistent
  differences in median price.
- **Two documented outliers** (very large homes sold cheaply) were removed, leaving 1,458 rows.
- **Baseline performance:** the Ridge regression achieved a cross-validated RMSE of **0.1147**
  (log units) and a test-set **R² of 0.910**, equivalent to about **$20,071** RMSE and
  **$14,567** MAE in dollar terms. This is the benchmark future models must beat.

#### Next steps
- Compare the baseline against Lasso, Random Forest, and Gradient Boosting models.
- Tune hyperparameters with grid search.
- Produce a ranked, plain-language list of price drivers for a non-technical audience, and
  translate the model's error into pricing confidence bands useful to buyers and sellers.

#### Outline of project

- [Link to notebook: EDA & Baseline Model](./capstone_eda.ipynb)

##### Contact and Further Information
Ekaansh Anand — ekaansh.anand@gmail.com
