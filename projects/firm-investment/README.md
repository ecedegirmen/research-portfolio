# Investment in New Technology – Econ 590 Final Project

[Back to portfolio](../../README.md) · [View presentation slides](ECON590_Slides.pdf)

**My contribution:** I contributed across the group project and independently authored the original README. The model, code, analysis, and presentation are collaborative work.

**Course:** Econ 590, Computational Methods for Economists, UNC Chapel Hill  
**Instructor:** Marlon Azinovic-Yang  
**Semester:** Fall 2025  
**Group Members:** Xiaohe Qiao, Ece Degirmen, Ziqiao Wang, Bowen Liao

---

## 1. Project Overview

This project analyzes how a firm decides to invest in automation (AI) capital over time. We study how the investment strategy and long-run outcomes change when AI capital becomes more easily substitutable for labor.

We solve a dynamic optimization problem using numerical methods taught in the course. Specifically, we:

- Apply value function iteration with interpolation
- Use numerical optimization for the control variable
- Simulate capital accumulation over time
- Compare results for different elasticities of substitution

We evaluate the model for three values of the elasticity of substitution between labor and AI:

σ = 1.05, 1.2, and 1.3

The goal is to understand how substitutability affects a firm’s incentive to invest in AI and the resulting productivity outcomes.

---

## 2. Economic Model

### 2.1 Production

The firm's output is determined by a CES production function with fixed labor (L = 1):

Y_t = [0.5 * L^((σ − 1) / σ) + 0.5 * A_t^((σ − 1) / σ)] ^ (σ / (σ − 1))

Where:
- A_t = AI capital at time t
- σ = elasticity of substitution between labor and AI

Higher σ means AI can replace labor more easily.

---

### 2.2 Capital Accumulation

A_{t+1} = A_t * (1 − δ_A) + I_t  
where:
- I_t = investment in AI capital  
- δ_A = depreciation rate (set to 0.1)

---

### 2.3 Objective Function

Per-period consumption:
C_t = Y_t − I_t

The firm maximizes dynamic log utility:

V(A_t) = max over I_t ≥ 0 of [ log(Y_t − I_t) + β * V(A_{t+1}) ]

Parameters used:
- β = 0.9
- δ_A = 0.1
- L = 1

---

## 3. Computational Approach

The implementation closely follows methods used in Lecture Notebook 11.

### Summary of steps

1. Set parameters and generate grid for A_t  
   - 50 grid points between 0.1 and 20

2. Define core functions:
   - production(A, σ)
   - utility_log(C)
   - get_update_AI(A, Vapprox_old, ...)
   - update_V_AI(...)
   - converge_Bellman_AI(...)
   - simulation(...)

3. Solve the Bellman equation for each σ value:
   - Obtain policy function A'(A) and value function V(A)

4. Simulate 50 periods from:
   - Low initial capital
   - Medium initial capital
   - High initial capital

5. Plot:
   - Value and policy functions
   - AI capital, investment, and output paths over time

---

## 4. Function Descriptions

### production(A, sigma_el)
Computes output using the CES production function. Ensures A stays non-negative.

### utility_log(C)
Computes log utility. Implements a minimum threshold to prevent log(0) issues.

### get_update_AI(A, Vapprox_old, beta, delta_A, Agrid, sigma_el)
For a given AI capital A:
- Uses scipy.optimize.minimize to determine optimal next-period capital
- Enforces nonnegative investment through the optimizer lower bound
- Computes consumption and utility
- Returns updated value and optimal next capital

### update_V_AI(Agrid, Vapprox, beta, delta_A, sigma_el)
Performs one Bellman update across all grid points. Builds new spline functions for:
- Value function
- Policy function

### converge_Bellman_AI(...)
Iterates Bellman updates until convergence or max iterations. Returns:
- Converged value function
- Policy function
- Success flag

### simulation(Astart, Anextapprox, T, sigma, deltaA)
Evaluates the cubic policy and adjusts next-period capital to keep investment nonnegative and consumption positive.

Simulates T periods:
- A_t (AI capital)
- Y_t (output)
- I_t (investment)
- C_t (consumption)

---

## 5. How to Run the Code

1. Open `590project_K-Investment_revised(1).ipynb`
2. Ensure required packages are installed:
   ```
   pip install numpy matplotlib scipy
   ```
3. Run all cells in order
4. Outputs include:
   - Convergence messages
   - Model solution results
   - Plots for each σ value

---

## 6. Key Findings

- Higher σ values lead to greater AI capital accumulation and higher output at the end of the simulated horizon.
- σ = 1.05 produces a lower level of AI capital than the higher-elasticity cases by the end of the simulation.
- σ = 1.2 and 1.3 produce progressively higher investment and AI capital levels at the end of the simulation.
- For each σ, paths starting from low, medium, and high capital move toward similar levels, although endpoints still differ after 50 periods.

**Interpretation:**  
Within this model, easier substitution strengthens the incentive to invest in AI capital. Higher elasticity supports higher output and consumption in the tested simulations.

---

## 7. AI Use Statement

Generative AI (ChatGPT) was used to assist in reviewing the structure of the code and README documentation. All coding, model decisions, and interpretation of results were completed by the group members.

---

### Revisions — October 2026
The revised notebook corrects the nonnegative-investment bound and constrains simulated choices to the feasible range while retaining cubic interpolation. All nine tested paths have nonnegative investment and positive consumption. Documentation and figures reflect these changes; feasibility checks do not establish full numerical accuracy or global stability. ChatGPT assisted with these later revisions.

## 8. What's included in the project

✔ `590project_K-Investment_revised(1).ipynb` – Python implementation  
✔ `README.md` – Documentation  
✔ Presentation slides (separate file)  

---

## 9. Final Notes

- The code uses approaches covered in class
- The results address the research question within the model and tested scenarios

---


