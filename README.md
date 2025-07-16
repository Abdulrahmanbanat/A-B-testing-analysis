# 📊 A/B Testing Analysis: Old Page vs New Page

## 📝 Project Overview

This project analyzes an A/B test to evaluate whether a **new webpage design** leads to higher conversion rates compared to the **existing (old) page**. The goal is to determine — using statistical methods — whether any observed difference in conversions is statistically significant or due to random variation.

---
## 📂 Dataset Source

The dataset used in this project is publicly available on Kaggle:

[AB Testing Dataset by ZhangLuyuan](https://www.kaggle.com/datasets/zhangluyuan/ab-testing)

Please refer to the original source for more information and licensing terms.

---
## 📁 Dataset Description

The dataset includes the following features:

- `user_id`: Unique identifier for each user.
- `group_type`: Indicates whether the user is in the `control` group (old page) or `treatment` group (new page).
- `landing_page`: The actual page that the user was shown (`old_page` or `new_page`).
- `converted`: Binary variable (1 if the user converted, 0 otherwise).
- `timestamp`: Removed during cleaning since it wasn't required for this analysis.

---

## 🧹 Data Cleaning Steps

- Renamed column `group` to `group_type` for clarity.
- Dropped the `timestamp` column.
- Removed mismatched rows where:
  - Control group users saw the new page.
  - Treatment group users saw the old page.
- Checked for duplicates and missing values.

---

## 📈 Conversion Rate Analysis

After cleaning, we calculated the conversion rate for each group:

- **Control Group (Old Page)**: 12.04%
- **Treatment Group (New Page)**: 11.88%

A basic comparison showed a slightly higher conversion rate in the control group.

---

## 📊 Visualization

We plotted the conversion rates using bar plots to visualize the difference between the two groups. The visual confirmed that the old page had a marginally higher conversion rate.

---

## 🧪 Hypothesis Testing

### 🎯 Objective

Determine if the difference in conversion rates between the control and treatment groups is **statistically significant**.

### Null Hypothesis (H₀):
There is **no difference** in conversion rates between the control and treatment groups.

### Alternative Hypothesis (H₁):
There **is a difference** in conversion rates between the two groups.

---

## 🧠 Why Use a t-test and 1000 Sample Size?

### 📌 Why Use a t-test?

#### Statistical Foundation:
- We're comparing the **means of two independent groups**.
- Although conversion is binary, the **mean of a binary variable** (0/1) represents a proportion.
- With large enough samples, the sampling distribution of the mean is approximately normal.

#### Why Welch's t-test?
- Does **not assume equal variances** (`equal_var=False`).
- More **robust** when sample sizes or variances differ.
- Better at controlling Type I error rates.

#### Why Not Chi-Square?
- While valid, t-test is:
  - More intuitive for comparing group means.
  - Offers better interpretability of the **effect size**.

---

### 🎯 Why 1000 Samples per Group?

#### Power & Simplicity:
- Full dataset is large, which may lead to detecting **tiny, insignificant differences**.
- Sampling 1,000 users per group helps:
  - Speed up computation.
  - Balance the groups.
  - Focus on **practically meaningful** differences.
  - Avoid overfitting or misleading sensitivity.

#### Random Sampling Benefits:
- Ensures **representative** and unbiased subset.
- Reduces **temporal or behavioral biases**.

---

## 📊 T-test Results

- **t-statistic**: -0.56  
- **p-value**: 0.57  

### ✅ Interpretation:
- p-value > 0.05 → **Fail to reject the null hypothesis**.
- No statistically significant difference in conversion rates between the control and treatment groups.

---

## 🧩 Conclusion

Based on this analysis:

- The **new page does not significantly outperform the old page** in terms of conversion rate.
- The current design (old page) may be retained unless there are **other factors** or **business goals** justifying the redesign.

---

## 💡 Next Steps (Optional for Further Analysis)

- Run the test with a **larger sample size** to detect smaller effects.
- Use **Bayesian A/B testing** for more probabilistic insight.
- Segment users (e.g., by device, location) to see if treatment works better for certain groups.

---

## 🔗 Project Goal Summary

This notebook demonstrates a **basic A/B testing pipeline** using Python, from data cleaning to hypothesis testing and interpretation. It is a simple and clear example suitable for GitHub or a portfolio project.
