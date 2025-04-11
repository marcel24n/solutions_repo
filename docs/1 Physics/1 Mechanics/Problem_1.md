# Problem 1



---

## 📘 1. Theoretical Foundation

We start with the equations of **projectile motion**, assuming:
- No air resistance
- Launched from ground level
- Constant gravitational acceleration `g = 9.81 m/s²`

### ▶️ Basic Kinematic Equations:
Let a projectile be launched with:
- Initial velocity: \( v_0 \)
- Angle of projection: \( \theta \)
- From: \( y_0 = 0 \)

Split into horizontal and vertical components:
- \( v_{x} = v_0 \cos\theta \)
- \( v_{y} = v_0 \sin\theta \)

#### Time of flight (when projectile returns to ground):
\[
t_{\text{flight}} = \frac{2v_0 \sin\theta}{g}
\]

#### Horizontal Range:
\[
R = v_{x} \cdot t_{\text{flight}} = v_0 \cos\theta \cdot \left(\frac{2v_0 \sin\theta}{g}\right)
\]

\[
\boxed{R = \frac{v_0^2 \sin(2\theta)}{g}}
\]

This shows the **range depends on \( \sin(2\theta) \)** — maximum at \( \theta = 45^\circ \).

---

## 📈 2. Analysis of the Range

### 📌 Insights:
- Maximum range occurs at \( \theta = 45^\circ \)
- For angles \( \theta \) and \( 90^\circ - \theta \), the range is the same
- The range increases with initial velocity \( v_0 \), and decreases with gravity \( g \)

---

## 🔧 3. Practical Applications

This simple model works great when:
- You launch from a flat surface
- No air resistance

But real life is messy! Consider:
- Launch from a height (e.g., cliff or hill)
- Uneven ground or slopes
- Air drag (which heavily alters the trajectory)
- Wind forces or spin (like a baseball or golf ball)

In those cases, we’d modify our model with:
- Drag force: \( F_d = -kv \)
- Numerical simulation (Euler or Runge-Kutta)

---

## 💻 4. Implementation (Python Script)

Let’s implement a simulation and plot **Range vs Angle** for different velocities.

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
g = 9.81  # gravity (m/s^2)
angles = np.radians(np.linspace(0, 90, 500))  # angles in radians

# Initial velocities to compare
velocities = [10, 20, 30]  # m/s

plt.figure(figsize=(10, 6))

for v0 in velocities:
    ranges = (v0 ** 2) * np.sin(2 * angles) / g
    plt.plot(np.degrees(angles), ranges, label=f'v₀ = {v0} m/s')

plt.title('Projectile Range vs Angle of Projection')
plt.xlabel('Angle (degrees)')
plt.ylabel('Range (meters)')
plt.legend()
plt.grid(True)
plt.show()
```

---



---