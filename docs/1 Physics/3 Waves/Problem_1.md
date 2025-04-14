# Interference Patterns on a Water Surface from Multiple Point Sources

## Motivation

Interference patterns on a water surface provide an intuitive visualization of wave superposition. By analyzing the interaction of waves emanating from multiple point sources arranged in regular polygon configurations, we can explore the intricate dynamics of wave phenomena, including constructive and destructive interference. This study aims to deepen our understanding of wave behavior through simulation and visualization.

## Task

Analyze the interference patterns formed on a water surface due to the superposition of waves emitted from point sources placed at the vertices of various regular polygons.

## Theoretical Foundation

The displacement of a circular wave on a water surface from a point source at $(x_0, y_0)$ is given by:

$$\eta(x, y, t) = A \cdot \cos(kr - \omega t + \phi)$$

Where:

-   $\eta(x, y, t)$ is the displacement at $(x, y)$ and time $t$.

-   $A$ is the amplitude.

-   $k = \frac{2\pi}{\lambda}$ is the wave number.

-   $\omega = 2\pi f$ is the angular frequency.

-   $r = \sqrt{(x - x_0)^2 + (y - y_0)^2}$ is the distance from the source.

-   $\phi$ is the initial phase.

The superposition of waves from $N$ sources is:

$$\eta_{sum}(x, y, t) = \sum_{i=1}^{N} \eta_i(x, y, t)$$

<details>

<summary> Python Simulation </summary>

``` python 
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

def wave_displacement(x, y, x0, y0, A, k, omega, t, phi):
    r = np.sqrt((x - x0)**2 + (y - y0)**2)
    return A * np.cos(k * r - omega * t + phi)

def superposition(x, y, sources, A, k, omega, t, phi):
    total_displacement = np.zeros_like(x)
    for x0, y0 in sources:
        total_displacement += wave_displacement(x, y, x0, y0, A, k, omega, t, phi)
    return total_displacement

def generate_sources(n, radius):
    theta = np.linspace(0, 2 * np.pi, n, endpoint=False)
    return [(radius * np.cos(t), radius * np.sin(t)) for t in theta]

def visualize_interference(sources, A, wavelength, frequency, duration, frames, filename):
    k = 2 * np.pi / wavelength
    omega = 2 * np.pi * frequency
    phi = 0
    t_values = np.linspace(0, duration, frames)
    x = np.linspace(-3, 3, 500)
    y = np.linspace(-3, 3, 500)
    X, Y = np.meshgrid(x, y)

    fig, ax = plt.subplots(figsize=(8, 8))
    img = ax.imshow(superposition(X, Y, sources, A, k, omega, 0, phi), cmap='viridis', extent=[-3, 3, -3, 3], animated=True)

    def update(frame):
        img.set_array(superposition(X, Y, sources, A, k, omega, t_values[frame], phi))
        return img,

    ani = animation.FuncAnimation(fig, update, frames=frames, blit=True)
    ani.save(filename, writer='pillow', fps=10)
    plt.close()


# Parameters
A = 1
wavelength = 1
frequency = 1
duration = 10
frames = 100

# Examples
# Triangle
triangle_sources = generate_sources(3, 1)
visualize_interference(triangle_sources, A, wavelength, frequency, duration, frames, 'triangle_interference.gif')
print("Triangle interference animation generated.")

# Square
square_sources = generate_sources(4, 1)
visualize_interference(square_sources, A, wavelength, frequency, duration, frames, 'square_interference.gif')
print("Square interference animation generated.")

# Pentagon
pentagon_sources = generate_sources(5, 1)
visualize_interference(pentagon_sources, A, wavelength, frequency, duration, frames, 'pentagon_interference.gif')
print("Pentagon interference animation generated.")

# Hexagon
hexagon_sources = generate_sources(6, 1)
visualize_interference(hexagon_sources, A, wavelength, frequency, duration, frames, 'hexagon_interference.gif')
print("Hexagon interference animation generated.")

# Octagon
octagon_sources = generate_sources(8, 1)
visualize_interference(octagon_sources, A, wavelength, frequency, duration, frames, 'octagon_interference.gif')
print("Octagon interference animation generated.")

# Circle (Approximation)
circle_sources = generate_sources(30, 1)
visualize_interference(circle_sources, A, wavelength, frequency, duration, frames, 'circle_interference.gif')
print("Circle interference animation generated.")

```
</details>


## Graphical Representations


![triangle_interference_regen](../../Animations/triangle_interference_regen.gif)
*Triangle Interference Pattern – Wave interference from 3 point sources.*




![square_interference_regen](../../Animations/square_interference_regen.gif)
*Square Interference Pattern – Wave interference from 4 point sources.*



![pentagon_interference](../../Animations/pentagon_interference.gif)
*Pentagon Interference Pattern – Wave interference from 5 point sources.*




![octagon_interference](../../Animations/octagon_interference.gif)
*Octagon Interference Pattern – Wave interference from 8 point sources.*




![circle_interference](../../Animations/circle_interference.gif)
*Circular Interference Approximation – Wave interference from 30 point sources.*




## Analysis
* **Constructive Interference:** Occurs where waves align in phase, resulting in increased amplitude. In our visualizations, these regions are bright.
* **Destructive Interference:** Occurs where waves align out of phase, resulting in decreased or zero amplitude. These regions are dark.
* **Regular Polygons:** The number of sources and their arrangement directly influence the complexity of the interference patterns. Higher numbers of sources result in more intricate patterns.
* **Circular Approximation:** As the number of sources increases, the polygon approaches a circle, resulting in a more uniform and detailed interference pattern.
* **Animation:** The animations illustrate the dynamic nature of interference patterns, showing how they evolve over time.




## Conclusion
This study demonstrates the complex interference patterns that emerge from multiple point sources arranged in regular polygons. By visualizing these patterns, we gain a deeper understanding of wave superposition and its dependence on source geometry. This analysis offers a practical approach to exploring wave phenomena and their applications in various fields.