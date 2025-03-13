# Orbital Period and Orbital Radius

## Motivation

Kepler's Third Law states that the square of the orbital period ( $T$ ) is proportional to the cube of the orbital radius ( $r$ ) for celestial bodies in circular orbits. This fundamental law bridges Newtonian mechanics and observational astronomy, helping determine planetary masses, distances, and satellite orbits.

Mathematically, Kepler's Third Law is expressed as: 

or, using Newton’s version:

where $G$ is the gravitational constant, and $M$ is the mass of the central body.

## Derivation

From Newton’s Law of Universal Gravitation and centripetal force:


Equating both:

Solving for velocity:

Since orbital period is given by , substituting for $v$:

Thus proving Kepler's Third Law.

Applications

Calculating Planetary Masses: By observing a satellite's orbit around a planet, the mass of the planet can be determined.

Determining Orbital Distances: Used in astronomy to estimate distances of exoplanets from their host stars.

Satellite Orbits: Helps in designing artificial satellites with precise orbital periods.

Computational Model

Below is a Python simulation that verifies Kepler’s Third Law for circular orbits.

import numpy as np
import matplotlib.pyplot as plt
from scipy.constants import G

# Constants (Sun mass in kg, Earth-Sun distance in meters)
M_sun = 1.989e30
r_values = np.linspace(1e10, 1.5e12, 100)  # Orbital radii in meters
T_values = np.sqrt((4 * np.pi**2 * r_values**3) / (G * M_sun))

# Plotting Kepler's Third Law
plt.figure(figsize=(8, 6))
plt.plot(r_values, T_values**2, label="$T^2$ vs $r^3$")
plt.xlabel("Orbital Radius (m)")
plt.ylabel("Orbital Period Squared (s²)")
plt.title("Verification of Kepler's Third Law")
plt.legend()
plt.grid()
plt.show()

Results

The graph confirms the linear relationship between  and , validating Kepler's Third Law.

Extending to Elliptical Orbits

For elliptical orbits, the law holds by replacing  with the semi-major axis , so that:

This applies to planets, comets, and exoplanets, allowing astronomers to predict celestial motions accurately.

Conclusion

Kepler’s Third Law is a powerful tool in astrophysics, linking observational data with theoretical physics. By implementing computational models, we can visualize and confirm its validity, making it indispensable for studying planetary systems and beyond.

