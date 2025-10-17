# Adaptive Assessment Simulation — 10-Day Predictive Hiring Experiment

### A Data Science Simulation to Improve Assessment Predictive Power

---

## Project Overview

This is a work-in-progess project simulating a **10-day hiring pipeline** where a company must onboard candidates quickly while improving the predictive accuracy of its assessment.  
The main question:  
> _Does performance on the assessment predict real-world project outcomes?_

Using **Item Response Theory (IRT)** and **machine learning**, this simulation models how assessments can be tuned daily to better identify top performers — just like a data-driven talent acquisition system.

---

## Objectives

- Simulate an assessment and project outcome scenario for 300+ candidates.
- Estimate item difficulty, discrimination, and candidate ability using **IRT**.
- Measure correlations between assessment results and project performance.
- Iteratively **refine** the assessment over 10 simulated days.
- Build an **ML predictor** to track how accuracy improves as the test evolves.

---

## Methodology

### Step 1 — Data Simulation
- Generate:
  - 300 candidates
  - 50 questions across 3 skill types  
- Assign true latent ability θ for each candidate  
- Simulate responses using a **2-Parameter Logistic IRT model (2PL)**:  
  $\( P(R_{j,i}=1) = \frac{1}{1+e^{-a_i(\theta_j - b_i)}} \)$

### Step 2 — IRT Modeling
- Fit the 2PL model to estimate:
  - `a_i`: discrimination (how well a question separates strong from weak candidates)
  - `b_i`: difficulty (how hard the question is)
  - `θ_j`: estimated ability per candidate  
- Evaluate correlation between θ̂ and project quality (low / medium / high) using **Spearman’s ρ**.

### Step 3 — Adaptive Refinement (Days 3–6)
- Identify weak or redundant items (too easy, too hard, or low discrimination).
- Adjust item parameters or simulate replacements.
- Re-simulate responses for new candidates and re-fit the model.

### Step 4 — Continuous Evaluation (Days 7–10)
- Repeat estimation → adjustment → simulation.
- Track how the correlation between assessment and project performance improves.

### Step 5 — Predictive Modeling
- Use estimated ability θ and skill-type scores as features.
- Train an **ordinal logistic regression** and **random forest** to predict project outcomes.
- Measure predictive performance (accuracy, macro-F1) over 10 simulated days.

---

## 📁 Repository Structure

```text
simulations_and models_testing/
│
├── data/
│   ├── simulated_responses_day1.csv        # Initial candidate responses
│   ├── simulated_responses_day10.csv       # Final iteration responses
│   └── project_performance.csv             # Project outcome labels (low, medium, high)
│
├── notebooks/
│   ├── 01_data_simulation.ipynb            # Generate candidate and response data
│   ├── 02_IRT_modeling.ipynb               # Fit IRT model, estimate difficulty/discrimination
│   ├── 03_predictive_analysis.ipynb        # Correlation and ML prediction analysis
│   ├── 04_adaptive_improvement.ipynb       # Adaptive item replacement and simulation
│   └── 05_visualizations_dashboard.ipynb   # Visualization and reporting
│
├── scripts/
│   ├── simulate_candidates.py              # Create candidate/item data
│   ├── fit_IRT.py                          # Estimate IRT parameters
│   ├── evaluate_correlation.py             # Compute correlations and significance
│   └── update_assessment.py                # Adaptive refinement logic
│
├── results/
│   ├── item_parameters_day1.csv
│   ├── item_parameters_day10.csv
│   ├── model_performance.json
│   └── plots/
│       ├── item_curves.png
│       ├── theta_distributions.png
│       ├── correlation_heatmap.png
│       ├── performance_trend.png
│
├── requirements.txt                        # Dependencies list
└── README.md                               # Project documentation

```

---

## ⚙️ Tech Stack

- **Python:** `pandas`, `numpy`, `scipy`, `matplotlib`, `scikit-learn`
- **IRT Modeling:** `pyirt`, `PyMC`, or `mirt`
- **Machine Learning:** `statsmodels`, `scikit-learn`
- **Visualization:** `seaborn`, `plotly`

---

## Next Steps

This simulation forms the foundation for **Project 2**, where real-world assessment data will be used to:
- Validate the model on actual candidate performance.
- Explore **Bayesian IRT** and **multi-dimensional ability modeling**.
- Build a **live adaptive testing prototype** that updates items dynamically.


