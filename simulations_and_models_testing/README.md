# Simulations and Models Testing

This folder contains a series of Jupyter notebooks dedicated to simulating and analyzing candidate assessment data through different modeling approaches — primarily the **2-Parameter Logistic (2PL) Item Response Theory (IRT)** model and a **heuristic probability model**. The overall goal is to understand how well statistical models can simulate, fit, and recover meaningful psychometric patterns from assessment data.

---

## Notebooks Overview

### 1. `simulate_candidates_2PL.ipynb`
**Simulation of Candidate Assessment and Item Responses**

This notebook demonstrates a complete workflow for simulating candidate abilities, item parameters, and assessment outcomes using the **2-Parameter Logistic (2PL)** IRT model.

**Key steps include:**
- Generating candidates with latent abilities (θ) sampled from a standard normal distribution.
- Visualizing the ability distribution with a histogram.
- Generating items with discrimination (a) and difficulty (b) parameters across multiple skill types.
- Simulating item responses probabilistically using the 2PL model and Bernoulli draws.
- Assigning project performance scores correlated with latent ability and categorizing them into low, medium, and high.
- Visualizing relationships such as:
  - Latent ability vs. performance score  
  - Item Characteristic Curves (ICCs) for items with varying difficulty and discrimination

The notebook connects the mathematical formulation of the 2PL model with visualizations to demonstrate how **a**, **b**, and **θ** influence response probabilities.  
It provides a foundation for exploring assessment simulations, response modeling, and interpretation of IRT-based evaluation metrics.

---

### 2. `simulate_candidates_heuristic.ipynb`
**Heuristic-Based Assessment Simulation**

This analysis simulates candidate responses to an assessment using a **heuristic probability model**, offering a non-IRT benchmark for comparison with formal psychometric methods.

**Key steps include:**
- Modeling candidate abilities using a **Beta distribution** to capture realistic variability within [0,1].
- Generating question difficulties from a normal distribution and clipping to ensure meaningful ranges.
- Applying a heuristic probability model to determine the likelihood of a correct response based on ability and question difficulty.
- Using binomial sampling to produce discrete assessment outcomes.
- Calculating total and skill-specific scores to study trends relative to ability.
- Simulating project performance influenced by ability with added variability, and categorizing results into low, medium, and high levels.

This notebook sets the stage for direct comparison with the 2PL IRT model, evaluating how heuristic simulations align with formal psychometric modeling.

---

### 3. `fit_IRT_2PLmodel.ipynb`
**IRT Model Validation: A Comprehensive Simulation Study**

This notebook validates the 2PL IRT model by fitting it to the simulated dataset generated in `simulate_candidates_2PL.ipynb`.  
It explores whether the fitted model can accurately recover the true parameters used during simulation.

**Key focus areas:**
- Estimating item discrimination (a) and difficulty (b) parameters.
- Comparing estimated parameters with the true simulated values.
- Evaluating model performance through visual diagnostics and statistical measures.

This study addresses a fundamental question: **Can IRT reliably uncover the latent structure that generated the observed data?**

---

### 4. `fit_IRT_heuristic.ipynb`
**IRT Analysis on Heuristic Simulation Data**

This notebook applies the IRT framework to data generated via heuristic modeling to test IRT’s robustness when the underlying data generation process deviates from its theoretical assumptions.

**Key steps include:**
- Fitting a 2PL IRT model to estimate latent abilities (θ), discrimination (a), and difficulty (b).
- Visualizing item characteristic curves, ability distributions, and ability–score relationships.
- Comparing heuristic “true” abilities with IRT-estimated abilities to assess how well IRT recovers meaningful patterns.

This analysis demonstrates how IRT modeling can reveal underlying structures even when the data is not strictly psychometric, highlighting its potential for broader applications in assessment and performance prediction.

---

## Purpose and Takeaways

Together, these notebooks form an integrated pipeline for:
- **Simulating** realistic candidate-item response data.
- **Estimating** latent psychometric parameters.
- **Comparing** theoretical and heuristic models.
- **Evaluating** the interpretability and robustness of IRT-based approaches.

This framework serves as a foundation for further research in adaptive testing, data-driven assessment design, and performance prediction through psychometric modeling.
