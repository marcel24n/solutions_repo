# Problem 1

# Investigating the Range as a Function of the Angle of Projection

## Motivation

Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Yet, beneath this simplicity lies a complex and versatile framework. The equations governing projectile motion involve both linear and quadratic relationships, making them accessible yet deeply insightful.

What makes this topic particularly compelling is the number of free parameters involved in these equations, such as initial velocity, gravitational acceleration, and launch height. These parameters give rise to a diverse set of solutions that can describe a wide array of real-world phenomena, from the arc of a soccer ball to the trajectory of a rocket.

## Theoretical Foundation

### Derivation of Governing Equations

The motion of a projectile follows Newton's second law of motion. Considering motion in two perpendicular directions:

1. **Horizontal Motion:**
   - No acceleration (ignoring air resistance), so velocity remains constant.
   - Horizontal displacement: $x = v_0 \cos(\theta) t$

2. **Vertical Motion:**
   - Subject to gravitational acceleration $g$.


   - Vertical displacement: $y = v_0 \sin(\theta) t - \frac{1}{2} g t^2$
   - Time of flight: solving $y = 0$ gives $t = \frac{2 v_0 \sin(\theta)}{g}$.

Using these equations, we derive the range formula:

$$
R = \frac{v_0^2 \sin(2\theta)}{g}
$$

### Influence of Initial Conditions

- **Initial Velocity ($v_0$)**: The range increases quadratically with $v_0$, meaning a higher launch speed results in a longer range.
- **Angle of Projection ($\theta$)**: The maximum range occurs at $\theta = 45^\circ$.
- **Gravitational Acceleration ($g$)**: A stronger gravitational pull decreases the range, as seen in environments like the Moon versus Earth.

## Analysis of the Range

### Dependence on Angle of Projection

The function $R(\theta)$ follows a sine curve due to $\sin(2\theta)$. Key observations:
- The range is symmetrical about $45^\circ$.
- Maximum range at $\theta = 45^\circ$.
- Identical ranges for complementary angles (e.g., $30^\circ$ and $60^\circ$).

### Effects of Other Parameters

- **Initial Velocity**: Since $R \propto v_0^2$, doubling $v_0$ quadruples the range.
- **Gravity**: A higher $g$ results in a shorter range, demonstrating why projectiles travel farther on the Moon.
- **Launch Height**: If launched from a height $h$, the range increases, requiring an adjusted formula.

## Practical Applications

- **Sports**: Understanding projectile motion in soccer, basketball, and golf.
- **Ballistics**: Military applications for targeting and optimizing trajectories.
- **Space Exploration**: Planning lunar and planetary landings.
- **Engineering**: Design of water fountains, roller coasters, and fireworks displays.

## Implementation

A computational tool can help visualize projectile motion. Using Python, we can:

1. Define a function to compute range for given $v_0$, $g$, and $\theta$.
2. Generate plots of range versus angle.
3. Extend to scenarios with air resistance and varying terrain.

Example code snippet:

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, g, theta):
    return (v0**2 * np.sin(2 * np.radians(theta))) / g

angles = np.linspace(0, 90, 100)
ranges = projectile_range(50, 9.81, angles)

plt.plot(angles, ranges)
plt.xlabel('Angle of Projection (degrees)')
plt.ylabel('Range (meters)')
plt.title('Projectile Range as a Function of Angle')
plt.grid()
plt.show()
```

This visualization provides clear insights into how the range behaves as a function of the launch angle.

!![alt text](<WhatsApp Image 2025-03-17 at 15.25.17_f34a94e5.jpg>)}

## Conclusion

Projectile motion, while a classical problem, remains a cornerstone of physics due to its broad applicability and insightful mathematical properties. By analyzing the dependence of range on the angle of projection, we uncover key principles that govern motion in various real-world scenarios. Through both theoretical derivations and computational simulations, we gain a deeper understanding of this fundamental phenomenon.

