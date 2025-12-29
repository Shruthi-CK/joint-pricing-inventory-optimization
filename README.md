
# Joint Pricing and Inventory Optimization (Extended Newsvendor Model)

## Project Overview
This project develops a data-driven optimization framework to jointly determine the optimal selling price ($p$) and production quantity ($q$) for a product with uncertain demand. 

Moving beyond the traditional Newsvendor model, this approach incorporates **price elasticity of demand**, **rush-printing costs**, and **disposal penalties** to maximize expected profit. The model demonstrates that replacing a fixed-price strategy with a joint optimization strategy yields a measurable increase in profitability and decision robustness.

## Key Features
* **Demand Estimation:** Modeled price-demand elasticity using **OLS Linear Regression** ($R^2 \approx 0.62$).
* **Scenario Generation:** Simulated demand distributions using regression residuals to capture real-world uncertainty.
* **Optimization Models (Gurobi):**
    * **Linear Programming (LP):** Optimized inventory levels for a fixed-price baseline.
    * **Quadratic Programming (QP):** Jointly optimized price and quantity by formulating a quadratic objective function with linear constraints.
* **Sensitivity Analysis:** Performed **Bootstrap Aggregation (1,000 iterations)** to quantify the stability of the optimal policy against data perturbations.

## Technologies Used
* **Python** (Pandas, NumPy, Matplotlib)
* **Optimization:** [Gurobi Optimizer](https://www.gurobi.com/) (`gurobipy`)
* **Statistics:** `statsmodels` (OLS Regression, Influence Diagnostics)

## Methodology & Results
The project compares two distinct approaches:

1.  **Fixed-Price Extended Newsvendor (LP):** * Treats price as exogenous ($p=1$).
    * **Result:** Optimal Quantity $\approx 472$ units | Expected Profit $\approx \$231.48$.

2.  **Joint Price-Quantity Optimization (QP):**
    * Treats price as a decision variable, creating a quadratic revenue term: $p(\beta_0 + \beta_1 p + \epsilon)$.
    * **Result:** Optimal Price $\approx \$0.95$ | Optimal Quantity $\approx 535$ units | Expected Profit $\approx \$234.92$.
    * **Impact:** The QP model improved expected profit by ~1.5% by capturing the trade-off between margin and volume.

## Visualizations
The notebook includes detailed visualizations:
* **Price-Demand Regression Fit:** Visualizing elasticity.
* **Profit Landscape Contour Plots:** A 2D analysis of the convex profit function to verify global optimality.
* **Bootstrap Distributions:** Histograms and scatterplots verifying the stability of the optimal price point ($p^*$).

## Usage
1.  Ensure you have a valid Gurobi license (academic or commercial).
2.  Install dependencies:
    ```bash
    pip install pandas numpy matplotlib gurobipy statsmodels
    ```
3.  Run the notebook `inventory_optimization.ipynb`.
