# Problem 2



---

# 🧮 Estimating π Using Monte Carlo Methods

---

## 🎯 Overview

We’ll estimate π using **two Monte Carlo methods**:
1. **Circle-based Monte Carlo Method** (Geometric Probability)
2. **Buffon’s Needle Experiment** (Classic probability problem)

We’ll simulate, visualize, and compare the two methods based on **accuracy**, **convergence**, and **computational performance**.

---

## 📐 Part 1: Estimating π Using a Circle

### 📘 Theoretical Foundation

- Consider a **unit circle** (radius = 1) centered at the origin.
- Enclose it in a square of side length 2 (from -1 to 1 in both x and y).
- Area of the circle = π·r² = π (since r = 1)
- Area of the square = 4

So, the **ratio** of points inside the circle to all points inside the square ≈ Area of Circle / Area of Square = π / 4  
Thus,
\[
\pi \approx 4 \times \frac{\text{Points Inside Circle}}{\text{Total Points}}
\]

---

### 🧪 Simulation & Visualization

```python
import numpy as np
import matplotlib.pyplot as plt

def estimate_pi_circle(n_points=10000, visualize=True):
    x = np.random.uniform(-1, 1, n_points)
    y = np.random.uniform(-1, 1, n_points)
    inside = x**2 + y**2 <= 1

    pi_estimate = 4 * np.sum(inside) / n_points

    if visualize:
        plt.figure(figsize=(6, 6))
        plt.scatter(x[inside], y[inside], color='blue', s=1, label='Inside Circle')
        plt.scatter(x[~inside], y[~inside], color='red', s=1, label='Outside Circle')
        plt.title(f"Monte Carlo π Estimation\nn = {n_points}, π ≈ {pi_estimate:.6f}")
        plt.legend()
        plt.gca().set_aspect('equal')
        plt.show()

    return pi_estimate
```

📈 Output:
Estimated π value: 3.1412

The scatter plot was displayed showing:

Blue dots: Points inside the unit circle

Red dots: Points outside the unit circle

Title with the estimation result
---

## 🪵 Part 2: Estimating π Using Buffon’s Needle

### 📘 Theoretical Foundation

- Drop a needle of length **ℓ** onto a floor with **parallel lines** spaced **d** apart.
- If **ℓ ≤ d**, the probability that the needle crosses a line is:
\[
P = \frac{2 \ell}{\pi d}
\]
Rearranged to estimate π:
\[
\pi \approx \frac{2 \ell \cdot N}{d \cdot C}
\]
Where:
- \(N\): total number of drops
- \(C\): number of times needle crosses a line

---

### 🧪 Simulation & Visualization

```python
def estimate_pi_buffon(n_drops=10000, needle_length=1.0, line_distance=2.0, visualize=True):
    crossings = 0
    x_vals = []
    theta_vals = []

    for _ in range(n_drops):
        x = np.random.uniform(0, line_distance / 2)
        theta = np.random.uniform(0, np.pi / 2)
        if x <= (needle_length / 2) * np.sin(theta):
            crossings += 1
        x_vals.append(x)
        theta_vals.append(theta)

    if crossings == 0:
        return np.inf  # Avoid divide by zero

    pi_estimate = (2 * needle_length * n_drops) / (line_distance * crossings)

    if visualize:
        plt.figure(figsize=(8, 4))
        for i in range(100):
            x0 = np.random.uniform(0, 5)
            y0 = np.random.uniform(0, 5)
            theta = np.random.uniform(0, np.pi)
            x1 = x0 + (needle_length / 2) * np.cos(theta)
            x2 = x0 - (needle_length / 2) * np.cos(theta)
            y1 = y0 + (needle_length / 2) * np.sin(theta)
            y2 = y0 - (needle_length / 2) * np.sin(theta)
            color = 'red' if int(x1 / line_distance) != int(x2 / line_distance) else 'blue'
            plt.plot([x1, x2], [y1, y2], color=color)

        for i in range(7):
            plt.axvline(i * line_distance, color='black', linewidth=0.5)

        plt.title(f"Buffon’s Needle Simulation\nπ ≈ {pi_estimate:.6f}")
        plt.xlim(0, 5)
        plt.ylim(0, 5)
        plt.gca().set_aspect('equal')
        plt.show()

    return pi_estimate
```


![alt text](<output 9.png>)

The Monte Carlo simulation estimated π as approximately 3.152 using 10,000 random points. The visualization shows which points fell inside (blue) and outside (red) the unit circle.
---

## 📊 Convergence Analysis

```python
def convergence_analysis(estimator_func, sample_sizes, label):
    estimates = []
    for n in sample_sizes:
        est = estimator_func(n, visualize=False)
        estimates.append(est)

    plt.plot(sample_sizes, estimates, marker='o')
    plt.axhline(np.pi, color='green', linestyle='--', label='True π')
    plt.xlabel('Number of Samples')
    plt.ylabel('Estimated π')
    plt.title(f'Convergence of π Estimate — {label}')
    plt.legend()
    plt.grid(True)
    plt.show()
```

![alt text](<output 10.png>)

Here's the convergence plot for the Monte Carlo π estimation method using the circle method. As the number of samples increases, the estimated value of π approaches the true value (~3.14159), illustrating the power of probabilistic estimation.

### Run Convergence Test

```python
sizes = [100, 500, 1000, 5000, 10000, 50000]
convergence_analysis(estimate_pi_circle, sizes, "Circle Method")
convergence_analysis(estimate_pi_buffon, sizes, "Buffon’s Needle")
```

---

## 📈 Results & Discussion

| Method              | Estimation Accuracy | Convergence Rate | Computational Simplicity |
|---------------------|---------------------|------------------|---------------------------|
| Circle-Based Method | High (with enough points) | √(n) slow convergence | Very simple and fast |
| Buffon’s Needle     | Slower and more variable | Requires more trials | Geometrically rich but noisier |

---

## 🧠 Final Thoughts

- The **circle method** is more commonly used due to its simplicity and consistent convergence.
- **Buffon’s needle** is historically important and more visually intriguing, but less efficient.
- Both methods showcase how **randomness can solve deterministic problems**—a core principle of Monte Carlo methods.

---

