# 🌍 Kepler’s Third Law: Orbital Period and Radius

##  Motivation

Kepler's Third Law describes a beautiful relationship in orbital mechanics:

> **The square of the orbital period (T) is proportional to the cube of the orbital radius (r):**
$$
T^2 \propto r^3
$$

This law allows us to:
- Predict **satellite periods**,
- Calculate **planetary distances**,
- Estimate **masses of celestial bodies**.

---

## Derivation

For a body of mass $ m $ orbiting a central mass $ M $ (like Earth) in a circular path:

1. **Gravitational Force** provides the **centripetal force**:
$$
\frac{G M m}{r^2} = \frac{m v^2}{r}
\Rightarrow v^2 = \frac{G M}{r}
$$

2. **Orbital Period**:
$$
T = \frac{2\pi r}{v}
\Rightarrow T^2 = \frac{4\pi^2 r^3}{G M}
\Rightarrow T^2 \propto r^3
$$

---

##  Python Simulation

Paste this code into a Python file (e.g. `kepler_third_law.py`) and run it to visualize the law.

<details>
<summary> Python Code </summary>

```python
import numpy as np
import matplotlib.pyplot as plt

G = 6.67430e-11  # gravitational constant (m^3/kg/s^2)
M = 5.972e24     # mass of Earth (kg)

radii_km = np.linspace(7000, 50000, 100)
radii_m = radii_km * 1e3

T_sec = 2 * np.pi * np.sqrt(radii_m**3 / (G * M))
T_hr = T_sec / 3600

# T² vs r³
plt.figure(figsize=(8, 6))
plt.plot(radii_m**3, T_sec**2)
plt.title("Kepler's Third Law: T² ∝ r³")
plt.xlabel("r³ (m³)")
plt.ylabel("T² (s²)")
plt.grid(True)
plt.tight_layout()
plt.show()

# log-log plot
plt.figure(figsize=(8, 6))
plt.loglog(radii_m, T_sec, 'r')
plt.title("Log-Log Plot: T vs r")
plt.xlabel("r (m)")
plt.ylabel("T (s)")
plt.grid(True, which='both')
plt.tight_layout()
plt.show()
```
</details>

4. Real-World Examples
**A. Moon Orbiting Earth**

- $𝑟=384,400 km$
- $r=384,400km$

$𝑇≈27.3days$

Verifying with the formula:

### Real-world check: Moon
<details>
<summary> Python Code </summary>

```python

r_moon = 384400e3  # meters
T_moon = 2 * np.pi * np.sqrt(r_moon**3 / (G * M))
T_moon_days = T_moon / (3600 * 24)
print(f"Computed Moon Period: {T_moon_days:.2f} days")
```

</details>

Matches observed value closely.

### LEO satellite
<details>
<summary> Python Code </summary>

```python

r_leo = (6371 + 400) * 1e3  # Earth's radius + altitude
T_leo = 2 * np.pi * np.sqrt(r_leo**3 / (G * M)) / 60  # minutes
print(f"LEO Orbital Period: {T_leo:.2f} minutes")
```

</details>

Approx. 90 minutes, as expected for ISS-type orbit.

## 5. 🪐 Elliptical Orbits and Other Bodies

Kepler's Third Law holds for **elliptical orbits** as well, with the orbital radius $ r $ replaced by the **semi-major axis** $ a $:

$$
T^2 = \frac{4\pi^2 a^3}{G(M + m)}
$$

### Generalization:

- Works for **planets, moons, exoplanets, and binary stars**
- Used in:
  - 🌟 **Exoplanet detection**
  - 🌌 **Binary star system analysis**
  - 🚀 **Deep space mission planning**

---

## 6. Conclusion

Kepler’s Third Law elegantly connects **time** and **space** in celestial mechanics. Through simulation and analysis, we:

-  Verified the relation $ T^2 \propto r^3 $
- Explored real-world examples like the Moon and satellites
-  Built a solid foundation for more advanced studies in orbital dynamics

---

##  References

- Kepler, J. _Harmonices Mundi_ (1619)  
- Newton, I. _Principia Mathematica_  
- NASA & ESA Mission Data  
- [NASA Orbit Calculator](https://ssd.jpl.nasa.gov/tools/orbit_calculator.html)
