# Problem 1

# Investigating the Range as a Function of the Angle of Projection

## Motivation

Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Yet, beneath this simplicity lies a complex and versatile framework. The equations governing projectile motion involve both linear and quadratic relationships, making them accessible yet deeply insightful.

What makes this topic particularly compelling is the number of free parameters involved in these equations, such as initial velocity, gravitational acceleration, and launch height. These parameters give rise to a diverse set of solutions that can describe a wide array of real-world phenomena, from the arc of a soccer ball to the trajectory of a rocket.

## Theoretical Foundation

1. Equations of Motion (Separating Motion into Components)
Projectile motion follows the laws of kinematics, meaning we can break it into horizontal (x) and vertical (y) components.

Horizontal Motion (Constant Velocity)
There is no acceleration in the horizontal direction (if we neglect air resistance).

The horizontal velocity remains constant:

𝑣
𝑥
=
𝑣
0
cos
⁡
𝜃
v 
x
​
 =v 
0
​
 cosθ
The horizontal displacement after time 
𝑡
t is:

𝑥
=
𝑣
0
cos
⁡
𝜃
⋅
𝑡
x=v 
0
​
 cosθ⋅t
Vertical Motion (Accelerated Motion Due to Gravity)
The vertical velocity changes due to gravitational acceleration 
𝑔
g.

The initial vertical velocity is:

𝑣
𝑦
=
𝑣
0
sin
⁡
𝜃
v 
y
​
 =v 
0
​
 sinθ
The vertical displacement at any time 
𝑡
t follows the equation:

𝑦
=
𝑣
0
sin
⁡
𝜃
⋅
𝑡
−
1
2
𝑔
𝑡
2
y=v 
0
​
 sinθ⋅t− 
2
1
​
 gt 
2
 
The first term (
𝑣
0
sin
⁡
𝜃
⋅
𝑡
v 
0
​
 sinθ⋅t) represents the upward motion due to initial velocity.

The second term (
1
2
𝑔
𝑡
2
2
1
​
 gt 
2
 ) accounts for the downward pull of gravity.

2. Time of Flight (Total Time Until the Projectile Hits the Ground)
The projectile lands when it reaches 
𝑦
=
0
y=0.
Setting the vertical motion equation to zero:

0
=
𝑣
0
sin
⁡
𝜃
⋅
𝑡
−
1
2
𝑔
𝑡
2
0=v 
0
​
 sinθ⋅t− 
2
1
​
 gt 
2
 
Factoring out 
𝑡
t:

𝑡
(
𝑣
0
sin
⁡
𝜃
−
1
2
𝑔
𝑡
)
=
0
t(v 
0
​
 sinθ− 
2
1
​
 gt)=0
Solving for 
𝑡
t, we get two solutions:

𝑡
=
0
t=0 (the moment the projectile is launched).

𝑡
=
2
𝑣
0
sin
⁡
𝜃
𝑔
t= 
g
2v 
0
​
 sinθ
​
  (the time when it lands back on the ground).

So, the total time of flight is:

𝑇
=
2
𝑣
0
sin
⁡
𝜃
𝑔
T= 
g
2v 
0
​
 sinθ
​
 
3. Range Formula (Total Horizontal Distance Traveled)
The range 
𝑅
R is the total horizontal distance covered before the projectile lands.

From our horizontal motion equation:

𝑥
=
𝑣
0
cos
⁡
𝜃
⋅
𝑡
x=v 
0
​
 cosθ⋅t
Substituting the total time of flight 
𝑇
T:

𝑅
=
𝑣
0
cos
⁡
𝜃
×
2
𝑣
0
sin
⁡
𝜃
𝑔
R=v 
0
​
 cosθ× 
g
2v 
0
​
 sinθ
​
 
Rearranging:

𝑅
=
2
𝑣
0
2
sin
⁡
𝜃
cos
⁡
𝜃
𝑔
R= 
g
2v 
0
2
​
 sinθcosθ
​
 
Using the trigonometric identity:

2
sin
⁡
𝜃
cos
⁡
𝜃
=
sin
⁡
2
𝜃
2sinθcosθ=sin2θ
We simplify the range equation to:

𝑅
=
𝑣
0
2
sin
⁡
2
𝜃
𝑔
R= 
g
v 
0
2
​
 sin2θ
​
 
Key Observations from the Range Formula
Maximum Range:

The function 
sin
⁡
2
𝜃
sin2θ is maximum when 
2
𝜃
=
90
∘
2θ=90 
∘
 

So, the optimal angle for maximum range is 
𝜃
=
45
∘
θ=45 
∘
 .

The maximum range is:

𝑅
max
=
𝑣
0
2
𝑔
R 
max
​
 = 
g
v 
0
2
​
 
​
 
Doubling Initial Velocity 
𝑣
0
v 
0
​
  Quadruples the Range:
Since 
𝑅
∝
𝑣
0
2
R∝v 
0
2
​
 , increasing 
𝑣
0
v 
0
​
  by 2 times increases 
𝑅
R by 4 times.

Effect of Gravity:

Higher gravity (
𝑔
g) reduces the range.

Example: A projectile on the Moon (where 
𝑔
g is smaller) will travel farther than on Earth.



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

