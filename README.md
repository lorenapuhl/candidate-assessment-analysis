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

# WIP – current status of analysis

## Simulations and Model Testing

This repository explores the simulation and estimation of candidate performance data using different modeling approaches. The notebook **`simulate_candidates_2PL.ipynb`** generates synthetic response data based on the **2-Parameter Logistic (2PL) Item Response Theory (IRT)** model, simulating how candidate ability and item characteristics interact to produce outcomes. In parallel, **`simulate_candidates_heuristic.ipynb`** creates a comparable dataset using a **heuristic approach**, providing a non-IRT baseline for comparison. The **`fit_IRT_2PLmodel.ipynb`** notebook fits an IRT model to the data simulated under the 2PL assumptions, estimating item discrimination and difficulty parameters through maximum likelihood estimation. Similarly, **`fit_IRT_heuristic.ipynb`** applies IRT fitting techniques to the heuristic data to evaluate model robustness and sensitivity when the underlying data-generating process does not strictly follow IRT assumptions. Together, these experiments allow for testing, validation, and deeper understanding of model behavior across theoretical and heuristic conditions.


## Repository Structure

```text
├──simulations_and models_testing/
│  ├── simulate_candidates_2PL.ipynb         # simulate data using 2PL model
│  │── simulate_candidates_heuristic.ipynb   # simulate data using heursitic model
│  ├── fit_IRT_2PLmodel.ipynb                # Fit IRT model to 2PL data from simulate_candidates_2PL.ipynb 
│  ├── fit_IRT_heuristic.ipynb               # Fit IRT model to heuristic data from simulate_candidates_heuristic.ipynb
│
│
├── data/ 
│  ├── 2pl_candidate_irt_estimates1
│  ├── 2pl_item_irt_parameters1
│  ├── 2pl_item_parameters1
│  ├── 2pl_project_performance1
│  ├── 2pl_simulated_responses1
│  ├── assessment_results
│  ├── candidate_irt_estimates
│  ├── item_irt_parameters
│  ├── passed_candidates_with_performance
│  ├── project_performance
│  ├── questions_metadata
│  └── responses1
│
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


