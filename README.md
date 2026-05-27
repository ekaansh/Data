
# Will the Customer Accept the Coupon?

## Summary

This project analyzes over 12,000 real driving scenarios to answer one question: **what makes a driver likely to accept a discount coupon?** Using data collected from Amazon Mechanical Turk, we compared drivers who accepted coupons against those who rejected them to uncover the key differences.

---

## Key Differences: Who Accepts vs. Who Doesn't

**Coupon type is the biggest factor.** Carry-out and cheap restaurant coupons were accepted by more than 70% of drivers. Bar coupons were the least popular — only 41% of drivers accepted them. Knowing which coupon type fits your audience is more important than anything else.

**Social context dramatically shifts behavior.** Drivers traveling with friends accepted coupons at nearly 60%, while solo drivers accepted only 44%. Drivers with kids in the car were even less likely to accept. People are more open to detours when they're not alone.

**Time of day decides coffee.** Coffee house coupons were most accepted around 10AM and 2PM — the natural coffee windows. Acceptance dropped sharply in the evening. Sending a coffee coupon at the wrong time is largely wasted.

**Frequent customers are far more receptive.** For bar coupons, drivers who already visit bars more than 3 times a month accepted at a 77% rate — more than double the 37% rate for infrequent visitors. Coupons work best when you target people already inclined toward the venue.

**Younger drivers engage more.** Drivers in the 21–26 age range showed the highest acceptance across coupon types. As age increases, acceptance tends to decline.

**Longer validity beats urgency.** Coupons valid for a full day were accepted at higher rates than 2-hour coupons. Giving drivers flexibility to redeem on their own schedule makes a real difference.

---

## Recommendations

| Action | Why It Works |
|---|---|
| Deliver coffee coupons at 10AM–2PM | Matches the natural coffee routine; acceptance peaks here |
| Target social travelers (groups, couples) | ~60% accept rate vs. 44% for solo drivers |
| Segment bar campaigns by visit frequency | Frequent visitors accept at 2× the rate of casual visitors |
| Use 1-day validity windows instead of 2-hour | Flexibility increases the chance of redemption |
| Focus younger demographics (21–26) | Consistently the highest-engagement age group |
| Trigger coffee promotions on rainy days | Cold/wet weather nudges drivers toward warm beverages |

---

## Jupyter Notebook

[View the full analysis notebook](notebook/coupon_result_notebook.ipynb)

---

## Technologies Used

Python · pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

**Data source:** UCI Machine Learning Repository

---

## Next Steps

- Build a machine learning model to predict which individual drivers will accept coupons
- Segment customers into personas using clustering
- A/B test morning vs. afternoon delivery timing for coffee coupons
- Expand the analysis to restaurant and carry-out coupon types
