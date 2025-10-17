# Simulations and Models Testing

This folder contains Jupyter notebooks for simulating and analyzing candidate assessment data using both the **2-Parameter Logistic (2PL) IRT** model and a **heuristic probability model**. The goal is to understand how well models can simulate, fit, and recover meaningful patterns in candidate performance data.

---

## Notebooks Overview

### `simulate_candidates_2PL.ipynb`
Simulates candidate abilities, item parameters, and assessment outcomes using the **2PL IRT model**. Includes:
- Generating candidates and items with latent abilities (θ), discrimination (a), and difficulty (b).  
- Simulating responses probabilistically and assigning performance scores.  
- Visualizing ability distributions, performance relationships, and Item Characteristic Curves (ICCs).

### `simulate_candidates_heuristic.ipynb`
Simulates assessment data using a **heuristic probability model**:
- Candidate abilities sampled from a Beta distribution.  
- Question difficulties modeled and clipped from a normal distribution.  
- Responses generated via heuristic probability and binomial sampling.  
- Performance scores calculated and categorized.

### `fit_IRT_2PLmodel.ipynb`
Fits a **2PL IRT model** to the simulated 2PL data to validate parameter recovery, estimating discrimination (a) and difficulty (b) and comparing estimates with true values.

**Conclusion:**  
While the 2PL model predicts total scores extremely well (r = 0.991, R² = 0.974), it performs poorly in recovering true parameters: discrimination (~32% error), difficulty (~90% error), and abilities (~155% error). This illustrates that internal consistency and predictive performance can mask fundamental inaccuracies in latent parameter estimation. Practically, the model works well for ranking and scoring but not for precise measurement of abilities or item properties.

### `fit_IRT_heuristic.ipynb`
Applies IRT fitting to **heuristic data**, comparing estimated latent abilities and item parameters with the heuristic “ground truth.”

**Conclusion:**  
The 2PL IRT model effectively captures meaningful patterns from heuristic data:
- Total scores correlate positively with both heuristic abilities and estimated θ, validating θ as a useful measure.  
- Item parameters (a and b) are recovered in an interpretable way.  
- Moderate correlation between estimated and heuristic parameters shows IRT captures underlying structure even with non-logistic data.  
- Latent ability estimates can rank candidates and guide assessment design.

---

## Purpose
These notebooks provide a pipeline for **simulating candidate responses, fitting IRT models, and evaluating model performance**, highlighting the strengths and limitations of IRT in both idealized (2PL) and heuristic scenarios. They demonstrate how models can be used for ranking, scoring, and understanding assessment design, while cautioning against over-reliance on parameter recovery accuracy.
