# Problem 2
## Escape Velocities and Cosmic Velocities
### Motivation
Understanding escape velocity is crucial for space exploration. The first, second, and third cosmic velocities define the speed needed to:

* Stay in orbit (first cosmic velocity).
* Escape a planet’s gravity (second cosmic velocity).
* Leave a star system (third cosmic velocity).
These concepts are fundamental for launching satellites, interplanetary travel, and deep-space missions.

## Cosmic Velocities Definitions
### First Cosmic Velocity (Orbital Velocity)
The minimum speed required to stay in a circular orbit around a planet. Derived from:

$v1​\=RGM​​$


​
 
​
 
### Second Cosmic Velocity (Escape Velocity)
The speed needed to break free from a planet’s gravity without further propulsion.
 
​“v2​\=2​⋅v1​\=R2GM​​”

 
Third Cosmic Velocity (Interstellar Escape)
The velocity required to leave the Sun’s gravitational influence:

𝑣“v3​\=2​⋅dGM⊙​​​”


​
 
​
 
where $M ⊙$ is the Sun’s mass and $𝑑$ is the distance from the Sun.

Calculations for Earth, Mars, and Jupiter
Using standard gravitational values:

Planet	Mass ($kg$)	Radius ($m$)	First Cosmic Velocity ($km/s$)	Second Cosmic Velocity ($km/s$)
Earth	
$$5.972
×
10
24
5.972×10 
24
 	
6.371
×
10
6
6.371×10 
6
 	7.91	11.19$$
Mars	
$$6.39
×
10
23
6.39×10 
23
 	
3.389
×
10
6
3.389×10 
6
 	3.55	5.03$$
Jupiter	
$$1.898
×
10
27
1.898×10 
27
 	
6.991
×
10
7
6.991×10 
7
 	42.1	59.5$$
## Python Implementation
### Python Script (cosmic_velocities.py)
python
Copy
Edit
import math

# Gravitational constant (m^3 kg^-1 s^-2)
G = 6.67430e-11  

# Celestial body data (mass in kg, radius in meters)
celestial_bodies = {
    "Earth": {"mass": 5.972e24, "radius": 6.371e6, "distance_sun": 1.496e11},
    "Mars": {"mass": 6.39e23, "radius": 3.389e6, "distance_sun": 2.279e11},
    "Jupiter": {"mass": 1.898e27, "radius": 6.991e7, "distance_sun": 7.785e11}
}

def first_cosmic_velocity(mass, radius):
    return math.sqrt(G * mass / radius)

def second_cosmic_velocity(mass, radius):
    return math.sqrt(2) * first_cosmic_velocity(mass, radius)

def third_cosmic_velocity(mass_sun, distance):
    return math.sqrt(2 * G * mass_sun / distance)

# Sun's mass
mass_sun = 1.989e30

# Compute and display results
for body, data in celestial_bodies.items():
    v1 = first_cosmic_velocity(data["mass"], data["radius"]) / 1000  # km/s
    v2 = second_cosmic_velocity(data["mass"], data["radius"]) / 1000  # km/s
    v3 = third_cosmic_velocity(mass_sun, data["distance_sun"]) / 1000  # km/s
    
    print(f"{body}:")
    print(f"  First Cosmic Velocity: {v1:.2f} km/s")
    print(f"  Second Cosmic Velocity: {v2:.2f} km/s")
    print(f"  Third Cosmic Velocity: {v3:.2f} km/s\n")
## Jupyter Notebook (Interactive Simulations)
The accompanying Jupyter Notebook contains:

* Detailed explanations
* Interactive graphs
* Velocity comparisons across planets
@ Download Jupyter Notebook (Link to the file on your site)@

##Graphical Representations
Below is a sample visualization of escape velocities for different planets:

(Include a velocity vs. planet graph from the Jupyter Notebook output.)

## Importance in Space Exploration
Satellites: Need at least the first cosmic velocity.
Moon & Mars Missions: Require second cosmic velocity to leave Earth.
Interstellar Travel: Future missions must reach the third cosmic velocity.
### Conclusion
Understanding cosmic velocities is key to space travel. With this knowledge, we can design better rockets, plan efficient space missions, and explore beyond our solar system.

