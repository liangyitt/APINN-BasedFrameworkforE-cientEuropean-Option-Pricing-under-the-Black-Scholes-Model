# APINN-BasedFrameworkforE-cientEuropean-Option-Pricing-under-the-Black-Scholes-Model

### 1. Problem Statement and Objective:
The goal of this project was to implement a physics-informed neural network (PINN) framework to efficiently price European call options under the Black-Scholes model. Traditional numerical methods such as finite difference or Monte Carlo can be computationally expensive, especially in higher dimensions or complex scenarios. PINNs offer a data-driven and PDE-constrained approach that directly incorporates financial theory and market constraints into the modeling process, aiming to achieve accurate, grid-free, and efficient approximations.

### 2. Theoretical Background:
- **Black-Scholes PDE**: Governs the pricing dynamics of European call options.
  $$
  \frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2 S^2 \frac{\partial^2 V}{\partial S^2} + rS \frac{\partial V}{\partial S} - rV = 0
  $$
- **Terminal Condition**: 
  $$
  V(S,T) = \max(S - K,0)
  $$
- **Analytical Benchmark**: Closed-form solution provided by the Black-Scholes formula for validation.

### 3. Research Methodology:
- **PINN Model Construction**:
  - Neural network inputs: Asset price \( S \) and time \( t \).
  - Network outputs: Option price \( V(S,t) \).
  - Loss function incorporates:
    - PDE residuals (enforcing PDE compliance)
    - Terminal conditions (correct payoff at maturity)
    - Boundary conditions (correct asymptotic behavior at extremes).

- **Data Sampling Scheme**:
  - Collocation points were randomly sampled within the domain.
  - Additional boundary points at \( S=0 \), \( S=S_{\max} \), and terminal points at \( t=T \).

### 4. Numerical Experiments and Results:
- **Parameters**:
  - Strike price \( K=40 \), volatility \( \sigma=0.2 \), risk-free rate \( r=0.05 \).
  - Price range \( S \in [0,160] \), time range \( t \in [0,1] \).

- **Training Process**:
  - Utilized Adam optimizer with around 10,000 epochs.
  - Loss curves demonstrated stable convergence:
    - PDE loss, terminal loss, and boundary loss all steadily declined, indicating successful training.

- **Visualizations and Performance**:
  - **3D Surface Plots**: Demonstrated smooth and accurate option price predictions across the entire domain.
  - **Cross-sectional Analysis**: PINN predictions at maturity closely matched analytical solutions.
  - **Loss Curves**: Illustrated a stable, decreasing trend in total loss and individual components (PDE, terminal, boundary) throughout training.

### 5. Key Findings and Conclusions:
- The PINN model accurately captured the option's price dynamics, matching closely the analytical solutions provided by the Black-Scholes formula.
- PINNs proved effective for option pricing by avoiding the complexity and computational overhead of traditional numerical schemes, without sacrificing accuracy.
- The method's flexibility allows it to easily adapt to different parameters and conditions, making it a strong candidate for pricing more complex derivatives or handling market changes.
