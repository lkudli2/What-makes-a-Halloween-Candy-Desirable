# What-makes-a-Halloween-Candy-Desirable
This project explores which characteristics make Halloween candies more desirable. Using multiple regression analysis, it evaluates the impact of different attributes on consumer preference and refines the model to highlight the features that most strongly drive desirability.
---

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

* Exploratory Data Analysis (EDA) to understand distributions.
* Multiple Linear Regression (MLR) to model win percentage.
* Diagnostics: leverage, Cook’s distance, residual plots, Breusch–Pagan test, Kolmogorov–Smirnov test, Q-Q plots.
* Backward elimination and partial F-tests for feature selection.

## Results

* Full model: **R² = 0.44**, F-test p < 1e-10.
* Reduced model identifies two significant predictors:

  * **Chocolate**: +16.6% win rate.
  * **Peanuts/Almonds**: +7.6% win rate.
* Other predictors (caramel, nougat, sugarpercent, etc.) were statistically insignificant after accounting for chocolate and nuts.

## Conclusion

An ideal Halloween candy contains **chocolate and peanuts/almonds**, which together explain a large portion of consumer preference. 

## Project Structure

* **`candy-data.csv`** → Dataset (FiveThirtyEight Candy Power Ranking).
* **`CS1_FA24_Anav_Lavanya_v2.Rmd`** → Main R Markdown file containing the full analysis, code, and results.
* **`CS1_FA24_Anav_Lavanya_v2.pdf`** → Compiled PDF report version of the project.
* **`README.md`** → Project description and documentation.

---
