
# Will the Customer Accept the Coupon?

## Business Problem

Businesses frequently use coupons and discounts to increase customer engagement and drive purchases. Understanding which customers are most likely to accept coupons can help businesses improve marketing strategies and target promotions more effectively.

This project explores customer driving scenarios and analyzes which factors influence coupon acceptance.

---

## Dataset

Source: UCI Machine Learning Repository

The dataset contains simulated driving scenarios and customer responses to different coupon offers.

### Target Variable

- `Y = 1` → Customer accepted the coupon
- `Y = 0` → Customer rejected the coupon

### Coupon Categories

- Coffee House
- Carryout & Takeaway
- Bar
- Cheap Restaurant (<$20)
- Expensive Restaurant ($20–$50)

---

## Technologies Used

- Python
- pandas
- NumPy
- matplotlib
- seaborn
- Jupyter Notebook

---

## Key Findings

- Lower-cost coupons had higher acceptance rates.
- Drivers traveling with passengers accepted more coupons.
- Afternoon and evening offers performed better.
- Sunny weather slightly improved acceptance rates.
- Younger customers showed higher coupon engagement.

---

## Recommendations

- Prioritize lower-cost coupon campaigns.
- Target users during afternoon/evening commute periods.
- Personalize promotions for social/group travel scenarios.
- Use contextual data such as weather and location.
- Focus campaigns on younger demographics.

---

## Next Steps

- Build predictive machine learning models
- Perform customer segmentation
- Develop recommendation systems
- Conduct A/B testing on coupon strategies
