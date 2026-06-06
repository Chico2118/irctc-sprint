# AI Feature Specification: Waitlist Confirmation Probability Predictor

## Problem It Solves

This feature addresses **Problem 5: PNR Status Information Is Difficult To Interpret** from Part A.

Many users do not understand railway waitlist codes such as WL, RAC, GNWL, and RLWL. Even when users understand the codes, they cannot easily estimate whether their ticket is likely to get confirmed before the journey date.

---

## Proposed Feature — User Perspective

When a user checks their PNR status or views a waitlisted ticket, the system displays a confirmation probability score.

Example:

PNR Status: GNWL 12

Confirmation Probability: 78%

Recommendation:
High likelihood of confirmation. No alternative booking required.

This helps users make better travel decisions without searching external websites.

---

## Model or API Choice

**Model Choice:** XGBoost Classification Model

Why XGBoost?

- Works well with tabular historical railway data.
- Fast prediction speed.
- Easier to explain compared to deep learning models.
- Requires less infrastructure than large language models.

---

## Training or Input Data

The model requires:

- Historical waitlist records
- Train number
- Route
- Class type
- Journey date
- Seasonality trends
- Current waitlist position
- Historical confirmation rates

Data Source:

- IRCTC booking database
- Railway reservation history
- Public train schedule data

---

## How Output Is Shown To The User

The output appears directly on the PNR page.

Example UI:

---

PNR STATUS

GNWL 12

Confirmation Probability
78%

Recommended Action:
Continue with current booking

---

The probability is displayed alongside the existing status information.

---

## Confidence Threshold and Fallback

### High Confidence (>70%)

Display probability score and recommendation.

### Medium Confidence (40–70%)

Display probability with caution label.

### Low Confidence (<40%)

Display:

"Prediction confidence is low. Please check alternative travel options."

### Fallback

If the prediction service is unavailable:

"Confirmation prediction currently unavailable."

The user still receives standard IRCTC status information.

---

## Success Metrics

- Reduce external waitlist-related searches by 40%.
- Increase engagement with PNR status pages.
- Improve user understanding of railway status codes.
- Reduce customer support queries regarding waitlist status.

---

## Limitations and Risks

- Historical patterns may not predict unusual travel periods accurately.
- Festival seasons can reduce prediction accuracy.
- Users may rely too heavily on predictions.
- Incorrect predictions could influence travel planning decisions.

To reduce risk, probabilities should always be presented as estimates rather than guarantees.
