# 🎃 What Makes a Halloween Candy Desirable?

**Authors:** Anav Vora & Lavanya Kudli
**Date:** October 28, 2024

## Overview

This project analyzes what makes Halloween candies more desirable using the **FiveThirtyEight Candy Dataset**. The dataset includes **269,000 matchup outcomes across 8,371 survey responses**, where each candy’s “win percentage” reflects how often it was preferred in head-to-head matchups. Alongside this, ten predictor variables capture candy attributes such as chocolate, fruity, caramel, peanuts/almonds, nougat, crisped rice/wafer, hardness, bar format, pluribus (packaging), and sugar percentage.

We apply **multiple linear regression** to examine the effect of these attributes on desirability, run full diagnostic checks, and refine the model using backward selection.

## Data

* File: **`candy-data.csv`**
* Source: FiveThirtyEight (Candy Power Ranking dataset).
* Response variable: `winpercent` (0–100).
* Predictors: chocolate, fruity, caramel, peanutyalmondy, nougat, crispedricewafer, hard, bar, pluribus, sugarpercent.

## Methods

* **Exploratory Data Analysis (EDA):** Histograms and bar charts to understand distributions of each feature.
* **Multiple Linear Regression (MLR):** Built a full model with all predictors (`R² = 0.44`, **F-test p < 1e-10**) to test overall significance.
* **Diagnostics & Statistical Tests:** (see table below)
* **Model Refinement:** Applied **backward selection** with **partial F-tests** to drop insignificant variables sequentially, ensuring each reduced model was statistically justified.

## Statistical Tests Summary Table

| **Test**                                           | **Purpose**                                                        | **Interpretation in this project**                                                          |
| -------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| **Overall F-test (ANOVA)**                         | Tests if at least one predictor has a nonzero effect.              | p < 1e-10 → model is highly significant.                                                    |
| **Leverage (2p/n rule)**                           | Identifies observations far from the mean of predictors.           | 3 high leverage points found, none problematic.                                             |
| **Studentized Residuals + Bonferroni Correction**  | Detects outliers in response variable.                             | Largest residual < cutoff → no outliers.                                                    |
| **Cook’s Distance**                                | Identifies influential points that can distort regression.         | All < 1 → no influential observations.                                                      |
| **Breusch–Pagan Test**                             | Checks for constant variance (homoscedasticity).                   | p = 0.13 (full) and p = 0.68 (final) → variance constant.                                   |
| **Kolmogorov–Smirnov Test (KS)**                   | Tests normality of residuals.                                      | p ≈ 4e-14 (full) and 2e-15 (final) → suggests non-normality, though diagnostics acceptable. |
| **Q-Q Plot**                                       | Visual check of normality.                                         | Mostly linear with slight tail deviation.                                                   |
| **Box–Cox Transformation**                         | Suggests if transformation needed to stabilize variance/normality. | λ \~ 1 within CI → no transformation needed.                                                |
| **Linearity Check (Partial Residuals for Sugar%)** | Confirms continuous predictors relate linearly.                    | Scatter looked random → linearity holds.                                                    |
| **Partial F-tests (Backward Selection)**           | Sequentially tests if removing variables is valid.                 | Insignificant predictors dropped step by step; chocolate + peanuts/almonds retained.        |

## Results

* Full model: **R² = 0.44**, F-test p < 1e-10.
* Final reduced model retained **chocolate** and **peanuts/almonds** as significant predictors:

  * **Chocolate**: +16.6% win rate.
  * **Peanuts/Almonds**: +7.6% win rate.
* Other predictors (caramel, nougat, crispedricewafer, sugarpercent, etc.) were not significant.

## Conclusion

An ideal Halloween candy contains **chocolate and peanuts/almonds**, which together explain a large portion of consumer preference. This project demonstrates how survey data and statistical modeling can provide **actionable insights** for consumer behavior and product design.

## Project Structure

* **`candy-data.csv`** → Dataset (FiveThirtyEight Candy Power Ranking).
* **`CS1_FA24_Anav_Lavanya_v2.Rmd`** → Main R Markdown file containing full analysis, code, and statistical tests.
* **`CS1_FA24_Anav_Lavanya_v2.pdf`** → Compiled PDF report version of the project.
* **`README.md`** → Project description and documentation.

