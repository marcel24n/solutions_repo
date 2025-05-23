# Problem 1



---

## 📘 Exploring the Central Limit Theorem Through Simulations

### ✨ Motivation

The Central Limit Theorem (CLT) states that the **sampling distribution of the sample mean becomes approximately normal** as the **sample size increases**, regardless of the original population distribution (under some mild conditions like finite variance). This property is fundamental in inferential statistics and enables confidence intervals, hypothesis tests, and more.

---

## 🔬 Simulation Plan

### 🧪 1. Population Distributions
We will use the following population distributions:
- **Uniform**: Flat distribution between 0 and 1.
- **Exponential**: Right-skewed, λ = 1.
- **Binomial**: Discrete, n=10, p=0.5.

### 📈 2. Sampling and Visualization
For each population:
- Draw `n_samples` (e.g., 1000) samples of size [5, 10, 30, 50].
- Compute the mean of each sample.
- Plot histograms of these sample means to visualize convergence to a normal distribution.

### ⚙️ 3. Parameter Exploration
We'll explore:
- The effect of increasing sample size on normality.
- The effect of population variance on the **spread** of the sampling distribution.

### 🌍 4. Practical Applications
The CLT is essential in:
- Estimating **population parameters** when the population distribution is unknown.
- **Quality control** and process monitoring.
- **Finance**: modeling portfolio returns.

---

## 🐍 Python Implementation (Jupyter Notebook / Script)

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Settings
np.random.seed(42)
sample_sizes = [5, 10, 30, 50]
n_samples = 1000

# Distribution generators
distributions = {
    "Uniform [0, 1]": lambda size: np.random.uniform(0, 1, size),
    "Exponential (λ=1)": lambda size: np.random.exponential(1, size),
    "Binomial (n=10, p=0.5)": lambda size: np.random.binomial(n=10, p=0.5, size=size)
}

# Plotting function
def plot_sampling_distribution(dist_name, generator):
    plt.figure(figsize=(16, 10))
    for i, n in enumerate(sample_sizes):
        means = [np.mean(generator(n)) for _ in range(n_samples)]
        plt.subplot(2, 2, i + 1)
        sns.histplot(means, kde=True, bins=30, stat="density", color="skyblue")
        plt.title(f"{dist_name} — Sample Size {n}")
        plt.xlabel("Sample Mean")
        plt.ylabel("Density")
    plt.tight_layout()
    plt.show()

# Run simulation and plot
for name, dist_func in distributions.items():
    print(f"\n🔍 Sampling from {name}")
    plot_sampling_distribution(name, dist_func)
```
Generates 1000 sample means for each distribution at each of 4 sample sizes (n = 5, 10, 30, 50).

Uses:

Uniform distribution: np.random.uniform(0, 1, size)

Exponential distribution: np.random.exponential(1, size)

Binomial distribution: np.random.binomial(10, 0.5, size)

Plots histograms of sample means with density curves (via Seaborn) in a 2x2 subplot layout.

🔍 Expected Output (Summary)
For each distribution, you'd see a 2x2 grid of histograms showing sample means:

1. Uniform [0, 1]
For n=5: Spread out and slightly flat.

n=10: A bit more concentrated.

n=30, n=50: Strong bell shape (normal-looking), centered at 0.5.

2. Exponential (λ=1)
For n=5: Right-skewed (long tail).

n=10: Still skewed.

n=30: Starting to normalize.

n=50: Almost bell-shaped, but still slightly skewed.

3. Binomial (n=10, p=0.5)
Population mean = 5

Since this is already somewhat symmetric:

n=5 shows decent bell shape.

n=10–50 become increasingly smooth and centered tightly around 5.

---

## 📊 Observations & Discussion

### 🎯 Convergence Behavior

| Distribution | Skewed? | Converges Quickly? | Notes |
|--------------|--------|-------------------|-------|
| Uniform      | No     | Yes               | Already symmetric. |
| Exponential  | Yes    | Slower            | Needs larger sample size for normality. |
| Binomial     | No     | Medium            | Discrete, but symmetric around mean. |

### 🧮 Spread of Sample Means
- As **sample size increases**, the **spread (standard deviation)** of the sampling distribution **decreases**.
- This follows the rule:  
  \[
  \text{SD of sampling distribution} = \frac{\sigma}{\sqrt{n}}
  \]

---

## 🏁 Real-World Implications

| Field          | Application                                     |
|----------------|-------------------------------------------------|
| Medicine       | Estimating average treatment effects.           |
| Manufacturing  | Monitoring variation in production lines.       |
| Finance        | Modeling returns of investment portfolios.      |
| Social Science | Analyzing survey results, polling predictions.  |

---

## 💡 Conclusion

Through simulation, we confirmed that **the CLT holds across various population types** and sample sizes. Larger samples lead to a tighter and more symmetric distribution of the mean. This powerful result underpins much of classical statistics and justifies using normal-based methods even when data is not normally distributed.

---

