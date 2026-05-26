# Statistical Analysis and Modeling of Fraud Risk Factors

## 1. ANOVA Analysis: Device Type and Fraud Rates
### Hypothesis Testing
* **Null Hypothesis ($H_0$):** The mean fraud rate is equal across all device types.
* **Alternative Hypothesis ($H_1$):** At least one device type has a significantly different mean fraud rate.
(fraud_by_device.png)

### Findings & Statistical Variance
* **"Unknown" Devices:** Exhibit the highest average (mean) fraud rate and the largest variance. This marks them as the most unpredictable and critical risk category.
* **Mobile Devices:** Follow "Unknown" sources, demonstrating a higher median fraud rate than Desktop and Tablet devices.
* **Desktop & Tablet Devices:** Remain the most stable, tightly bound, and low-risk transaction channels.

### Strategic Recommendation
* Implement stricter multi-factor authentication (MFA) and verification protocol steps for "Unknown" sources to minimize economic losses and enhance transaction security.

---

## 2. ANOVA Analysis: Time of Day and Fraud Distribution
### Hypothesis Testing
* **Null Hypothesis ($H_0$):** The mean fraud rate is equal across all time periods (Morning, Afternoon, Evening, Night).
* **Alternative Hypothesis ($H_1$):** At least one time period has a significantly different mean fraud rate.
(fraud_by_hr_distribution.png)

### Findings & Distribution Dynamics
* **Evening Period:** Shows the highest median and mean fraud rates across the dataset.
* **Morning & Afternoon Periods:** Display the greatest variance and wider Interquartile Ranges (IQR), indicating less predictable behavior during daylight hours.
* **Nighttime Transactions:** Appear as the most stable window, showing the lowest overall fraud distribution.
* **Hourly Insights:** Based on operational transaction density (Military Time), fraud density begins picking up relative to legitimate transactions during non-business hours (specifically starting after hour 16:00).

### Strategic Recommendation
* Deploy time-based velocity checks and automated transaction limits during evening peak hours to actively flag and intercept high-frequency anomalies.

---

## 3. Regression Analysis (Model 1): Fraud Risk Shift by Amount Tier
### Model Framework
* **Response Variable:** `fraudulent` (The predicted probability of a transaction being fraud)
* **Predictor:** `is_high_value` (Categorized as Low Range $<\$25	ext{k}$ or High Range $>\$25	ext{k}$)

### Statistical Metrics
* **P-value:** $0.149$
* **F-statistic:** $2.081$
* **Adjusted $R^2$:** $0.000$

### Findings & Valuation Impact
* Moving from the low-value to the high-value tier indicates a directional upward trend, shifting the predicted fraud probability from approximately $4.9\%$ to $6.3\%$ (an increase of $1.39$ percentage points).
* However, the model's $p$-value ($0.149$) reveals that within this simple single-variable framework, the amount tier alone is **not statistically significant** at the $95\%$ confidence level.
* The Adjusted $R^2$ of $0.000$ confirms that transaction size alone explains a negligible portion of total fraud variance. This underscores that fraud is driven by an intersection of variables rather than isolated dollar thresholds.
* A widening confidence interval in the higher tier indicates greater statistical uncertainty for larger amounts.

### Strategic Recommendation
* Establish tiered verification thresholds for transactions exceeding $\$25,000$ to control for the baseline directional risk elevation.

---

## 4. Regression Analysis (Model 2): Multi-Factor & Interaction Effects
### Model Framework
* **Response Variable:** `fraudulent` (Predicted fraud probability)
* **Predictors:** `transaction_amount`, `device_used` (Desktop, Mobile, Tablet, Unknown), and `previous_fraudulent_transactions`
* **Interaction Term:** `device_used:transaction_amount` (Evaluates how fraud risk changes as transaction amounts increase across different devices)

### Equation Structure
$$	ext{Predicted Fraud Probability} = f( eta_0 +  eta_1(	ext{Amount}) +  eta_2(	ext{Device}) +  eta_3(	ext{PrevFraud}) +  eta_4(	ext{Amount} 	imes 	ext{Device}))$$

### Statistical Significance & Model Accuracy
* **Predictor Success:** `transaction_amount`, `device_used`, and `previous_fraudulent_transactions` are all highly statistically significant predictors of fraud.
* **Interaction Success:** The interaction effect between `device_used` and `transaction_amount` is statistically significant ($p < 0.05$). This mathematically confirms that the impact of transaction size on fraud risk varies sharply depending on the channel used.
* **Model Validation:** The significant F-statistic validates that this multi-factor model is a legitimate upgrade over baseline average guesses, proving a true mathematical relationship rather than random variance.

### Behavioral Divergences
* **"Unknown" Devices:** Exhibit the steepest upward slope, with fraud probability spiking dramatically toward $14\%$ as transaction amounts increase.
* **Mobile Devices:** Risk scales upward consistently alongside higher spending amounts.
* **Tablet Devices:** Risk remains relatively flat, showing a marginal upward trajectory.
* **Desktop Devices:** Demonstrate a unique inverse relationship; risk actually trends downward as transaction sizes increase, suggesting larger value purchases are safer on traditional computers.

### Strategic Recommendation
* Prioritize high-value "Unknown" and "Mobile" transactions for escalated security checks, as the interaction model proves they grow exponentially riskier at higher price points.

---

## 5. Account Maturity Metrics: Influence of Account Age
### Findings & Timeline Dynamics
* Analysis of account age densities reveals a noticeable distribution shift: older accounts show an increased probability of fraudulent transactions.
* A pronounced risk spike is visible within the **75â€“100 day range**. This indicates that as accounts mature, they face a higher compounding probability of credential stuffing, account takeovers, or delayed-execution breaches by malicious actors.
