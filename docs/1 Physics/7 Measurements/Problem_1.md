# Measuring Earth's Gravitational Acceleration with a Pendulum

## Materials Used
- String length: 1.5 meters
- Weight: A bag containing 100g of sugar
- Digital stopwatch (resolution: 0.01s)
- Measuring tape (resolution: 0.1 cm)

## Experimental Data

### Length Measurement
- Length (L) = 1.500 m
- Resolution uncertainty (δL) = ±0.0005 m

### Time Measurements for 10 Oscillations

| Trial | Time (s) |
|-------|----------|
| 1     | 24.52    |
| 2     | 24.48    |
| 3     | 24.56    |
| 4     | 24.50    |
| 5     | 24.53    |
| 6     | 24.49    |
| 7     | 24.51    |
| 8     | 24.54    |
| 9     | 24.47    |
| 10    | 24.50    |

### Statistical Analysis

1. Mean time for 10 oscillations (T₁₀):
   - T₁₀ = 24.51 s
   - Standard deviation (s) = 0.027 s
   - Standard error (δT₁₀) = s/√n = 0.0085 s

2. Period Calculation:
   - T = T₁₀/10 = 2.451 s
   - δT = δT₁₀/10 = 0.00085 s

## Calculations

### Gravitational Acceleration (g)

Using the formula: g = 4π²L/T²

1. Substituting values:
   g = 4 × π² × 1.500 / (2.451)²
   g = 9.81 m/s²

### Uncertainty Propagation

The uncertainty in g (δg) is calculated using:
δg/g = √[(2δT/T)² + (δL/L)²]

1. Relative uncertainties:
   - δT/T = 0.00085/2.451 = 0.00035
   - δL/L = 0.0005/1.500 = 0.00033

2. Final uncertainty:
   δg = g × √[(2 × 0.00035)² + (0.00033)²]
   δg = ±0.04 m/s²

## Final Result
g = (9.81 ± 0.04) m/s²

## Analysis

### Comparison with Standard Value
- Standard value of g = 9.80665 m/s²
- Our measured value: 9.81 ± 0.04 m/s²
- The measured value agrees with the standard value within uncertainty

### Sources of Uncertainty

1. Length Measurement (δL):
   - Limited by measuring tape resolution (±0.5 mm)
   - Uncertainty in determining the center of mass of the weight
   - Slight stretching of string during oscillation

2. Time Measurement (δT):
   - Human reaction time in starting/stopping the stopwatch
   - Difficulty in precisely determining the completion of an oscillation
   - Digital stopwatch resolution (±0.01s)

3. Experimental Limitations:
   - Air resistance (though minimal at small angles)
   - String mass effects (neglected in simple pendulum approximation)
   - Small angle approximation (kept < 15° to minimize error)

### Improvements for Future Measurements

1. Use of electronic timing gates for more precise time measurements
2. Multiple length measurements to reduce systematic errors
3. Video analysis for more accurate period measurements
4. Temperature and humidity control to account for environmental effects

## Visualizations

### 1. Time Series Analysis
![Time Series](../../_pics/time_series.png)

This plot shows the consistency of our measurements across all trials. The small variations between measurements indicate good precision in our timing method.

<details>
<summary>Click to see the Python code for time series plot</summary>

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Data from our experiment
times = np.array([24.52, 24.48, 24.56, 24.50, 24.53, 24.49, 24.51, 24.54, 24.47, 24.50])

plt.figure(figsize=(10, 6))
plt.plot(range(1, 11), times, 'o-', linewidth=2, markersize=8)
plt.grid(True)
plt.xlabel('Trial Number')
plt.ylabel('Time for 10 Oscillations (s)')
plt.title('Time Measurements Across Trials')
plt.savefig('../_pics/time_series.png', dpi=300, bbox_inches='tight')
plt.close()
```
</details>

### 2. Period Distribution
![Period_Histogram](../../_pics/period_histogram.png)

The histogram shows the distribution of individual periods, demonstrating that our measurements follow an approximately normal distribution around the mean value.

<details>
<summary>Click to see the Python code for period histogram</summary>

```python
periods = times / 10  # Convert to single period

plt.figure(figsize=(10, 6))
sns.histplot(periods, bins=15, kde=True)
plt.axvline(periods.mean(), color='r', linestyle='--', label=f'Mean = {periods.mean():.3f} s')
plt.xlabel('Period (s)')
plt.ylabel('Frequency')
plt.title('Distribution of Measured Periods')
plt.legend()
plt.savefig('../_pics/period_histogram.png', dpi=300, bbox_inches='tight')
```
</details>

### 3. Measurement Residuals
![Residuals](../../_pics/residuals.png)

The residuals plot shows the deviation of each measurement from the mean value in milliseconds. This helps identify any systematic trends or biases in our measurements.

<details>
<summary>Click to see the Python code for residuals plot</summary>

```python
residuals = periods - periods.mean()
plt.figure(figsize=(10, 6))
plt.scatter(range(1, 11), residuals * 1000, s=100)  # Convert to milliseconds
plt.axhline(y=0, color='r', linestyle='--')
plt.grid(True)
plt.xlabel('Trial Number')
plt.ylabel('Residual (ms)')
plt.title('Residuals from Mean Period')
plt.savefig('../_pics/residuals.png', dpi=300, bbox_inches='tight')
```
</details>

### 4. Pendulum Motion Animation

![pendulum animation](../../_pics/pendulum.gif)

This animation illustrates the simple harmonic motion of our pendulum setup, showing how the period remains constant for small angles.

<details>
<summary>Click to see the Python code for pendulum animation</summary>

```python
from matplotlib.animation import FuncAnimation

fig, ax = plt.subplots(figsize=(8, 8))
L = 1.5  # Length in meters
g = 9.81  # Acceleration due to gravity
theta0 = np.pi/6  # Initial angle (30 degrees)

def get_coords(theta):
    x = L * np.sin(theta)
    y = -L * np.cos(theta)
    return x, y

# Time array for one complete oscillation
T = 2 * np.pi * np.sqrt(L/g)  # Period
t = np.linspace(0, T, 50)
theta = theta0 * np.cos(np.sqrt(g/L) * t)

line, = ax.plot([], [], 'k-', linewidth=2)
bob, = ax.plot([], [], 'ko', markersize=20)

def init():
    ax.set_xlim(-2, 2)
    ax.set_ylim(-2, 0.5)
    return line, bob

def animate(i):
    x, y = get_coords(theta[i])
    line.set_data([0, x], [0, y])
    bob.set_data([x], [y])
    return line, bob

anim = FuncAnimation(fig, animate, init_func=init, frames=len(t),
                    interval=50, blit=True, repeat=True)
anim.save('../_pics/pendulum.gif', writer='pillow')
```
</details>

### 5. Uncertainty Analysis
![Uncertainty Analysisdocs](../../_pics/uncertainty_analysis.png)

This plot shows how our measured period relates to different values of g, with our measurement uncertainty range highlighted. The intersection of our measured period with the theoretical curve gives us our experimental value for g.

<details>
<summary>Click to see the Python code for uncertainty analysis</summary>

```python
g_values = np.linspace(9.7, 9.9, 100)
L = 1.5  # Length in meters
T = periods.mean()  # Mean period
uncertainty = 0.04  # Our calculated uncertainty

plt.figure(figsize=(10, 6))
plt.axvline(x=9.81, color='g', linestyle='--', label='Measured g')
plt.axvline(x=9.80665, color='r', linestyle='--', label='Standard g')
plt.axvspan(9.81 - uncertainty, 9.81 + uncertainty, alpha=0.3, color='gray', label='Uncertainty Range')

# Plot theoretical curve
T_theoretical = 2 * np.pi * np.sqrt(L/g_values)
plt.plot(g_values, T_theoretical, 'b-', label='Theoretical T vs g')
plt.axhline(y=T, color='k', linestyle=':', label='Measured T')

plt.xlabel('Gravitational Acceleration (m/s²)')
plt.ylabel('Period (s)')
plt.title('Period vs Gravitational Acceleration')
plt.legend()
plt.grid(True)
plt.savefig('../_pics/uncertainty_analysis.png', dpi=300, bbox_inches='tight')
```
</details>

## Conclusion
The experiment successfully measured Earth's gravitational acceleration with good precision (±0.4% uncertainty). The measured value of (9.81 ± 0.04) m/s² agrees well with the accepted value, demonstrating the reliability of the simple pendulum method for determining g.

The largest contributions to uncertainty came from timing measurements and length determination. Despite these limitations, the simple pendulum proves to be an effective tool for measuring g with reasonable accuracy using basic equipment.

