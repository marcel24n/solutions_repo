# Problem 2



---

# 🌀 **Investigating the Dynamics of a Forced Damped Pendulum**

---

## 📘 **1. Theoretical Foundation**

### **Equation of Motion**

The motion of a forced damped pendulum is described by the nonlinear second-order differential equation:

\[
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \sin\theta = A \cos(\omega t)
\]

Where:
- \(\theta(t)\): angular displacement  
- \(\gamma\): damping coefficient  
- \(\omega_0 = \sqrt{g/L}\): natural angular frequency  
- \(A\): amplitude of external forcing  
- \(\omega\): angular frequency of the driving force  

---

### **Small-Angle Approximation**

For small oscillations (\(\theta \ll 1\)), we use \(\sin\theta \approx \theta\), simplifying the equation to:

\[
\frac{d^2\theta}{dt^2} + \gamma \frac{d\theta}{dt} + \omega_0^2 \theta = A \cos(\omega t)
\]

This is a **driven damped harmonic oscillator**, solvable analytically.

---

### **General Solution (Small Angles)**

The solution consists of:
- **Transient** (decays due to damping)
- **Steady-state** (driven solution):

\[
\theta(t) = \theta_0 e^{-\gamma t/2} \cos(\Omega t + \phi) + B \cos(\omega t - \delta)
\]

Where:
- \(B = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + (\gamma \omega)^2}}\)
- \(\delta = \tan^{-1}\left(\frac{\gamma \omega}{\omega_0^2 - \omega^2}\right)\)

---

### **Resonance Condition**

Occurs when driving frequency \(\omega \approx \omega_0\).  
- System absorbs maximum energy.  
- Amplitude \(B\) reaches a peak.  
- Damping reduces resonance sharpness.

---

## 🔬 **2. Analysis of Dynamics**

### **Effect of Parameters**

- **Damping \(\gamma\)**:
  - Low \(\gamma\): sustained oscillations.
  - High \(\gamma\): motion dies out quickly.
- **Driving Amplitude \(A\)**:
  - Small \(A\): linear-like motion.
  - Large \(A\): complex, possibly chaotic behavior.
- **Driving Frequency \(\omega\)**:
  - Near resonance → large response.
  - Far from resonance → low amplitude.

---

### **Regular vs Chaotic Motion**

- **Regular**: predictable, periodic or quasiperiodic.
- **Chaotic**: sensitive to initial conditions, irregular, non-repeating.

Transition to chaos happens by increasing \(A\) or tuning \(\omega\).

---

## 🧠 **3. Real-World Applications**

| Application | Description |
|-------------|-------------|
| 🏗️ Suspension Bridges | External forcing (wind, traffic) causes oscillations |
| ⚡ RLC Circuits | Analogous to pendulum with inductance/resistance |
| 🚶 Biomechanics | Human gait as forced pendulum |
| ⚙️ Energy Harvesting | Uses resonance for maximizing power |

---

## 💻 **4. Python Implementation (Simulation)**

Below is a Python script using `scipy` and `matplotlib`.

### 🔧 Required Libraries
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp
```

### 🔁 Simulation Function
```python
# Parameters
gamma = 0.1        # damping
omega0 = 1.5       # natural frequency (sqrt(g/L))
A = 1.2            # driving amplitude
omega = 2/3        # driving frequency

def pendulum(t, y):
    theta, dtheta = y
    d2theta = -gamma * dtheta - omega0**2 * np.sin(theta) + A * np.cos(omega * t)
    return [dtheta, d2theta]
```

### 🧪 Solve the Equation
```python
# Initial conditions
theta0 = 0.2
dtheta0 = 0.0
t_span = (0, 100)
t_eval = np.linspace(*t_span, 5000)

sol = solve_ivp(pendulum, t_span, [theta0, dtheta0], t_eval=t_eval)
```

### 📈 Plot Time Evolution
```python
plt.figure(figsize=(10,4))
plt.plot(sol.t, sol.y[0], label='θ(t)')
plt.title('Forced Damped Pendulum - Angular Displacement Over Time')
plt.xlabel('Time')
plt.ylabel('Angle (rad)')
plt.grid(True)
plt.legend()
plt.show()
```

---

### 🌌 Phase Portrait
```python
plt.figure(figsize=(6,6))
plt.plot(sol.y[0], sol.y[1], lw=0.5)
plt.title('Phase Portrait: θ vs dθ/dt')
plt.xlabel('θ (rad)')
plt.ylabel('Angular velocity (rad/s)')
plt.grid(True)
plt.show()
```

---

### 🌀 Poincaré Section
Sample the state every period of the driving force:

```python
T_drive = 2 * np.pi / omega
sample_times = np.arange(0, 100, T_drive)
theta_samples = []
omega_samples = []

for t_sample in sample_times:
    index = np.abs(sol.t - t_sample).argmin()
    theta_samples.append(sol.y[0][index])
    omega_samples.append(sol.y[1][index])

plt.figure(figsize=(6,6))
plt.scatter(theta_samples, omega_samples, s=5)
plt.title('Poincaré Section')
plt.xlabel('θ (rad)')
plt.ylabel('dθ/dt (rad/s)')
plt.grid(True)
plt.show()
```

---

## 📉 **5. Optional: Bifurcation Diagram**

Try plotting steady-state angle values for a range of amplitudes \(A\):

```python
def get_bifurcation_data(A_values, omega=2/3):
    points = []
    for A in A_values:
        def pend(t, y):
            theta, v = y
            return [v, -0.1 * v - 1.5**2 * np.sin(theta) + A * np.cos(omega * t)]
        
        sol = solve_ivp(pend, (0, 300), [0.1, 0], t_eval=np.linspace(200, 300, 1000))
        T_drive = 2*np.pi / omega
        for t in np.arange(250, 300, T_drive):
            idx = np.abs(sol.t - t).argmin()
            points.append((A, sol.y[0][idx]))
    return points

A_values = np.linspace(1.0, 1.5, 200)
data = get_bifurcation_data(A_values)

A_vals, theta_vals = zip(*data)
plt.figure(figsize=(10,5))
plt.plot(A_vals, theta_vals, ',k')
plt.title('Bifurcation Diagram: A vs θ')
plt.xlabel('Driving Amplitude A')
plt.ylabel('θ')
plt.grid(True)
plt.show()
```

---

## 🚧 **6. Limitations & Extensions**

| Limitation | Extension |
|------------|-----------|
| Assumes constant \(\gamma, A, \omega\) | Add time-dependent forcing |
| Only single pendulum | Model coupled pendulums |
| Idealized | Add friction, noise, or nonlinear damping |