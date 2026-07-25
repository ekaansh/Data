# Data Science Projects

A collection of applied data-analysis and machine-learning projects, each in its own
self-contained folder with its own README and notebook.

---

## [Will the Customer Accept the Coupon?](notebook/coupon_result_notebook.ipynb)

Analyzes over 12,000 real driving scenarios to determine what makes a driver likely to
accept a discount coupon, using data collected from Amazon Mechanical Turk.

**Key findings:** coupon type is the biggest factor in acceptance; social context, time of
day, visit frequency, age, and validity window all shift acceptance meaningfully.

[Full write-up and notebook →](notebook/coupon_result_notebook.ipynb)

---

## [What Drives the Price of a Car?](what-drives-the-price-of-a-car/README.md)

Analyzes ~426K used vehicle listings to identify which attributes most influence price,
and translates the results into inventory and pricing recommendations for a used-car
dealership. Follows the CRISP-DM framework, with linear (Ridge/Lasso) and tree-based
(Random Forest, Gradient Boosting) regression models, cross-validated and grid-searched.

**Key findings:** car age and odometer are the strongest price drivers; vehicle type,
drivetrain, condition, and fuel type produce meaningful premiums.

[Full write-up and notebook →](what-drives-the-price-of-a-car/README.md)

---

## Technologies Used

Python · pandas · NumPy · Matplotlib · Seaborn · scikit-learn · Jupyter Notebook
