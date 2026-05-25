# Healthcare Financial Analysis: Statistical Driver Assessment of Patient Billing

## 📌 Project Overview
This project investigates the underlying drivers of financial variance within a healthcare system using a dataset of 55,500 patient records. The objective was to determine whether specific operational or clinical factors—specifically **Admission Type** (Urgent vs. Elective) and **Medical Condition** (Diabetes, Hypertension, Asthma)—statistically impact the final billing amounts issued to patients.

By combining descriptive statistical profiling, targeted data auditing, and inferential hypothesis testing (T-Test, ANOVA), this analysis aims to provide hospital administrators with data-driven clarity on pricing consistencies.

## 🛠️ Tech Stack & Methods
*   **Tool:** Microsoft Excel (with Data Analysis Toolpak enabled)
*   **Techniques:** Data Auditing, Descriptive Statistics, Pivot Tables, Two-Sample T-Testing, Single-Factor ANOVA, Data Visualization.

---

## 📊 Phase 1: Data Cleaning & Descriptive Profiling
An initial exploratory data analysis (EDA) was conducted on the raw billing data to establish baseline metrics of central tendency and variance.

### 🚨 Data Integrity Audit (Anomaly Detected)
During the descriptive phase, a critical systemic error was identified:
*   **Discovery:** The baseline evaluation flagged a **Minimum Billing Amount of -$2,008.49**. 
*   **Action Taken:** Because a hospital cannot issue a negative bill, these values were identified as programmatic artifacts from synthetic data generation. A data purge was executed to filter out and delete all rows containing billing amounts less than $0 to protect downstream testing.

### Cleaned Descriptive Metrics
Following the data purge, the final baseline metrics for the **Billing Amount** column were calculated:
*   **Mean (Average Bill):** \$25,539.32
*   **Median (Middle Point):** \$25,538.07
*   **Mode (Most Common):** \$14,238.32
*   **Standard Deviation:** \$14,211.45 (Indicating an exceptionally wide spread of costs)
*   **Skewness:** -0.00097 

**Insight:** Because the skewness is roughly 0 and the Mean and Median are virtually identical, the billing distribution reflects a perfectly symmetrical bell curve distribution, making it highly eligible for parametric inferential testing.

---

## 🔮 Phase 2: Inferential Hypothesis Testing

### Test 1: Do Operational Priorities Drive Pricing? (Two-Sample T-Test)
A **Two-Sample T-Test Assuming Unequal Variances** was conducted to check if operational classification changes pricing structures.
*   **Groups:** Urgent Admissions vs. Elective Admissions
*   **Hypothesis:** 
    *   *Null Hypothesis ($H_0$):* There is no difference in the average bill between Urgent and Elective admissions.
    *   *Alternative Hypothesis ($H_1$):* There is a significant difference.
*   **Result:** Two-Tail P-Value = **0.5639**

**Statistical Verdict:** Failed to reject the null hypothesis. Because $p > 0.05$, the price difference between admission tracks is statistically insignificant. Any slight variation is purely random noise.

### Test 2: Do Clinical Diagnoses Drive Pricing? (Single-Factor ANOVA)
To see if specific diseases incur heavier billing structures, a **Single-Factor ANOVA** evaluated three independent patient cohorts simultaneously.
*   **Groups:** Diabetes Patients vs. Hypertension Patients vs. Asthma Patients
*   **Result:** P-Value = **0.7428**

**Statistical Verdict:** Failed to reject the null hypothesis. Because $p > 0.05$, there is no statistically meaningful cost variance across these three primary medical conditions.

---

## 💡 Business Conclusions & Key Takeaways
1.  **Synthetic Data Footprint:** The combination of an absolute zero skewness, identical means across clinical segments, and exceptionally high P-values confirms that the underlying dataset behaves randomly. This mathematically validates its nature as a synthetically generated pipeline.
2.  **Operational Consistency:** Within this data ecosystem, hospital administrators do not charge premium rates for urgent admissions, nor do they upcharge for chronic respiratory/metabolic diseases over cardiovascular conditions.
3.  **Data Quality Warning:** This project demonstrates the vital importance of the initial descriptive audit phase. Failing to strip out the negative billing data would have compromised the mathematical integrity of both the T-Test and ANOVA calculations.
