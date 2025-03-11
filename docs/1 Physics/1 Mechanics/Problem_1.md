# Problem 1

Investigating the Range as a Function of the Angle of Projection
1. Theoretical Foundation
Deriving the Equations of Motion:

Projectile motion can be analyzed by breaking it into horizontal and vertical components. Assuming no air resistance, the only acceleration is due to gravity, acting downward.

Horizontal Motion:

d
2
x
d
t
2
=
0
  
⟹
  
d
x
d
t
=
v
0
x
=
v
0
cos
⁡
(
θ
)
dt 
2
 
d 
2
 x
​
 =0⟹ 
dt
dx
​
 =v 
0x
​
 =v 
0
​
 cos(θ)
x
(
t
)
=
v
0
cos
⁡
(
θ
)
⋅
t
x(t)=v 
0
​
 cos(θ)⋅t
Vertical Motion:

d
2
y
d
t
2
=
−
g
  
⟹
  
d
y
d
t
=
v
0
y
−
g
t
=
v
0
sin
⁡
(
θ
)
−
g
t
dt 
2
 
d 
2
 y
​
 =−g⟹ 
dt
dy
​
 =v 
0y
​
 −gt=v 
0
​
 sin(θ)−gt
y
(
t
)
=
v
0
sin
⁡
(
θ
)
⋅
t
−
1
2
g
t
2
y(t)=v 
0
​
 sin(θ)⋅t− 
2
1
​
 gt 
2
 
Time of Flight:

The projectile lands when 
y
(
t
)
=
0
y(t)=0:

v
0
sin
⁡
(
θ
)
⋅
t
−
1
2
g
t
2
=
0
  
⟹
  
t
(
v
0
sin
⁡
(
θ
)
−
1
2
g
t
)
=
0
v 
0
​
 sin(θ)⋅t− 
2
1
​
 gt 
2
 =0⟹t(v 
0
​
 sin(θ)− 
2
1
​
 gt)=0
t
=
0
or
t
=
2
v
0
sin
⁡
(
θ
)
g
t=0ort= 
g
2v 
0
​
 sin(θ)
​
 
Range:

Substitute the time of flight into the horizontal motion equation:

R
=
v
0
cos
⁡
(
θ
)
⋅
2
v
0
sin
⁡
(
θ
)
g
=
v
0
2
sin
⁡
(
2
θ
)
g
R=v 
0
​
 cos(θ)⋅ 
g
2v 
0
​
 sin(θ)
​
 = 
g
v 
0
2
​
 sin(2θ)
​
 
Family of Solutions:

The range 
R
R depends on the initial velocity 
v
0
v 
0
​
 , the angle of projection 
θ
θ, and gravitational acceleration 
g
g. Different initial conditions lead to different trajectories and ranges.

2. Analysis of the Range
Dependence on Angle of Projection:

The range 
R
R is maximized when 
sin
⁡
(
2
θ
)
=
1
sin(2θ)=1, i.e., 
θ
=
4
5
∘
θ=45 
∘
 . For angles less than or greater than 
4
5
∘
45 
∘
 , the range decreases symmetrically.

Influence of Initial Velocity and Gravitational Acceleration:

Initial Velocity (
v
0
v 
0
​
 ): The range increases with the square of the initial velocity.

Gravitational Acceleration (
g
g): The range decreases with increasing gravitational acceleration.

3. Practical Applications
Real-World Scenarios:

Sports: Analyzing the trajectory of a soccer ball or a golf shot.

Engineering: Designing projectile-based systems, such as water fountains or missile trajectories.

Astrophysics: Modeling the motion of celestial bodies under gravitational influence.

Adaptations:

Uneven Terrain: Adjust the initial height 
y
0
y 
0
​
  in the vertical motion equation.

Air Resistance: Incorporate a drag force proportional to the velocity, leading to more complex differential equations.

4. Implementation
Python Script for Simulation:

python
Copy
import numpy as np
import matplotlib.pyplot as plt

# Constants
g = 9.81  # gravitational acceleration (m/s^2)

def range_projectile(v0, theta, g):
    theta_rad = np.radians(theta)
    return (v0**2 * np.sin(2 * theta_rad)) / g

# Parameters
v0 = 20  # initial velocity (m/s)
angles = np.linspace(0, 90, 100)  # angles from 0 to 90 degrees
ranges = [range_projectile(v0, angle, g) for angle in angles]

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(angles, ranges, label=f'v0 = {v0} m/s')
plt.xlabel('Angle of Projection (degrees)')
plt.ylabel('Range (m)')
plt.title('Range as a Function of Angle of Projection')
plt.legend()
plt.grid(True)
plt.show()
Graphical Representation:

The plot shows the range as a function of the angle of projection for a given initial velocity. The curve peaks at 
4
5
∘
45 
∘
 , illustrating the optimal angle for maximum range.

5. Limitations and Extensions
Limitations of the Idealized Model:

Air Resistance: Neglecting air resistance can lead to overestimation of the range.

Wind Effects: Crosswinds can alter the trajectory significantly.

Spin and Lift: In sports, spin can create lift, affecting the trajectory.

Suggestions for Improvement:

Incorporating Drag: Use a more complex model that includes air resistance.

Wind Effects: Add a horizontal acceleration component to account for wind.

Spin Effects: Model the Magnus effect for spinning projectiles.

Deliverables
Markdown Document with Python Script:

The provided Python script simulates and visualizes the range as a function of the angle of projection.

Family of Solutions:

The range equation 
R
=
v
0
2
sin
⁡
(
2
θ
)
g
R= 
g
v 
0
2
​
 sin(2θ)
​
  describes a family of solutions parameterized by 
v
0
v 
0
​
 , 
θ
θ, and 
g
g.

Graphical Representations:

Plots showing the range versus angle of projection for different initial velocities.

Discussion on Limitations:

The idealized model neglects air resistance, wind, and spin effects, which are crucial for accurate real-world predictions.