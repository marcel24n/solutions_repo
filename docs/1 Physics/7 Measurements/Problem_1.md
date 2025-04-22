# Problem 1



---

# 🌍 Measuring Gravitational Acceleration (g) Using a Simple Pendulum

---

## 🎯 Objective

To measure the local acceleration due to gravity (**g**) using a simple pendulum and rigorously analyze uncertainties in length and time measurements.

---

## 🧪 Materials

| Item                  | Description |
|-----------------------|-------------|
| String (L = 1–1.5 m)  | Uniform and inextensible |
| Weight                | Small mass (e.g., keychain, washer, sugar bag) |
| Stopwatch/Timer       | Preferably with 0.01 s resolution |
| Ruler/Tape Measure    | With resolution of 1 mm (±0.0005 m uncertainty) |
| Support               | Fixed horizontal bar, rod, or similar |

---

## ⚙️ Experimental Setup

- Attach the weight to the string and suspend it from a fixed point.
- **Measure the length \( L \)** from the pivot to the center of mass of the bob.

> **Length (L):** `L = 1.245 m`  
> **Measurement resolution:** 1 mm → \( u_L = \pm 0.0005 \, \text{m} \)

---

## ⏱️ Data Collection

- Displace the pendulum by <15° to ensure simple harmonic motion.
- Measure time for **10 oscillations**, 10 times.
- Use these to calculate the **mean time**, **standard deviation**, and **uncertainty**.

### 🔢 Sample Table of Measurements

| Trial | Time for 10 Oscillations \( T_{10} \) [s] |
|-------|---------------------------------------------|
| 1     | 22.43                                       |
| 2     | 22.47                                       |
| 3     | 22.45                                       |
| 4     | 22.46                                       |
| 5     | 22.44                                       |
| 6     | 22.46                                       |
| 7     | 22.48                                       |
| 8     | 22.43                                       |
| 9     | 22.45                                       |
| 10    | 22.46                                       |

---

## 📊 Calculations

### 1. **Mean Time for 10 Oscillations**

\[
\bar{T}_{10} = \frac{1}{10} \sum_{i=1}^{10} T_{10,i} = 22.45 \, \text{s}
\]

### 2. **Standard Deviation (s)**

\[
s = \sqrt{\frac{1}{n-1} \sum (T_{10,i} - \bar{T}_{10})^2} = 0.016 \, \text{s}
\]

### 3. **Uncertainty in Mean Time (u\(_{\bar{T}}\))**

\[
u_{\bar{T}} = \frac{s}{\sqrt{n}} = \frac{0.016}{\sqrt{10}} \approx 0.0051 \, \text{s}
\]

### 4. **Period of One Oscillation**

\[
T = \frac{\bar{T}_{10}}{10} = 2.245 \, \text{s} \quad \text{with} \quad u_T = \frac{u_{\bar{T}}}{10} = 0.00051 \, \text{s}
\]

---

## 🌍 Calculating Gravitational Acceleration (g)

\[
g = \frac{4\pi^2 L}{T^2}
\]

\[
g = \frac{4\pi^2 \cdot 1.245}{(2.245)^2} \approx 9.755 \, \text{m/s}^2
\]

---

## 🧮 Uncertainty in g

### Relative Uncertainties:

\[
\left(\frac{u_g}{g}\right)^2 = \left(\frac{u_L}{L}\right)^2 + \left(2 \cdot \frac{u_T}{T}\right)^2
\]

\[
\left(\frac{u_g}{g}\right)^2 = \left(\frac{0.0005}{1.245}\right)^2 + \left(2 \cdot \frac{0.00051}{2.245}\right)^2
\]

\[
u_g \approx 0.0101 \, \text{m/s}^2
\]

### Final Value:

\[
g = 9.755 \pm 0.010 \, \text{m/s}^2
\]

---

## 🧠 Analysis

### ✅ Comparison with Standard Value

| Location | Standard g (m/s²) | Measured g (m/s²) |
|----------|-------------------|-------------------|
| Sea level | 9.80665           | 9.755 ± 0.010     |

- Our value is **within 0.5%** of the standard value.
- Measurement uncertainty is **well understood and controlled**.

---

## 🔍 Discussion

### 1. **Sources of Uncertainty**

| Source             | Impact |
|--------------------|--------|
| **Length (L)**     | Low — high resolution of tape |
| **Timing (T)**     | Medium — human reaction and stopwatch resolution |
| **Swing Angle**    | Low — <15° avoids nonlinearities |
| **Air Resistance** | Negligible for short durations |
| **Pivot Friction** | Minimal if smooth |

### 2. **Measurement Resolution Effects**

- A stopwatch with 0.01 s resolution contributes to uncertainty.
- Human reaction time introduces a **systematic bias** (~0.1–0.3 s).
- Repeating over **10 oscillations** helps minimize this.

### 3. **Suggestions for Improvement**

- Use a **photogate timer** for more accurate timing.
- Use a **longer string** for longer periods, reducing relative timing error.
- Repeat for **multiple lengths** and verify \( T^2 \propto L \).

---

## ✅ Final Results Summary

| Quantity        | Value                  |
|-----------------|------------------------|
| Pendulum Length \(L\) | 1.245 ± 0.0005 m         |
| Period \(T\)           | 2.245 ± 0.00051 s        |
| Gravitational \(g\)    | 9.755 ± 0.010 m/s²       |

---

