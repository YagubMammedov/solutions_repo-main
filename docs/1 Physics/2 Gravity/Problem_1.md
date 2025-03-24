# **Gravity: Kepler's Third Law (T² ∝ r³)**

## **1. Derivation for Circular Orbits**

### **Force Balance Equation**
For a circular orbit, gravitational force equals centripetal force:

\[
\frac{GMm}{r^2} = \frac{mv^2}{r}
\]

### **Orbital Velocity Relation**
\[
v = \frac{2\pi r}{T}
\]

### **Substitution and Simplification**
\[
\frac{GM}{r^2} = \frac{(2\pi r/T)^2}{r} \implies T^2 = \frac{4\pi^2 r^3}{GM}
\]

**Final Form:**
\[
\boxed{T^2 = \left(\frac{4\pi^2}{GM}\right) r^3}
\]

---

## **2. Python Simulation**

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.constants import G

# Constants
M_earth = 5.972e24  # kg
radii = np.linspace(3.8e8, 4.0e8, 100)  # 380,000-400,000 km (Moon's orbit range)

# Calculate periods
periods = np.sqrt(4 * np.pi**2 * radii**3 / (G * M_earth)) / (24*3600)  # in days

# Plotting
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(14,5))

# Orbit visualization
theta = np.linspace(0, 2*np.pi, 100)
ax1.plot(np.cos(theta), np.sin(theta), 'b-')
ax1.set_title("Circular Orbit")
ax1.set_aspect('equal')
ax1.grid()

# Kepler's Law verification
ax2.plot(radii**3, periods**2, 'r-')
ax2.set_xlabel('r³ (m³)')
ax2.set_ylabel('T² (days²)')
ax2.set_title("Kepler's Third Law Verification")
ax2.grid()

plt.tight_layout()
plt.show()
```

---
![alt text](image-1.png)

## **3. Graphical Representations**

### **Figure 1: Circular Orbit**
![Circular Orbit](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Circular_orbit.gif/220px-Circular_orbit.gif)

### **Figure 2: T² vs r³ Relationship**
```python
# Output from the Python code above
```
*(The right plot shows a perfect linear relationship confirming T² ∝ r³)*

---

## **4. Extension to Elliptical Orbits**

### **Generalized Kepler's Third Law**
\[
\boxed{T^2 = \frac{4\pi^2 a^3}{G(M+m)}}
\]

Where:
- \( a \) = semi-major axis
- \( M \) = primary mass
- \( m \) = secondary mass

### **Comparison Table**

| Feature       | Circular Orbit | Elliptical Orbit |
|--------------|---------------|-----------------|
| Shape        | Perfect circle | Ellipse         |
| Radius       | Constant \( r \) | Varies (min: perihelion, max: aphelion) |
| Kepler's Law | \( T^2 \propto r^3 \) | \( T^2 \propto a^3 \) |

---

## **5. Astronomical Applications**

### **Solar System Examples**
| Body       | Orbital Radius (AU) | Period (years) | T²/r³ |
|------------|---------------------|----------------|-------|
| Mercury    | 0.387               | 0.241          | 1.000 |
| Earth      | 1.000               | 1.000          | 1.000 |
| Mars       | 1.524               | 1.881          | 1.000 |

### **Key Implications**
1. **Mass Determination**: Measure \( M \) by observing \( T \) and \( r \)
2. **Exoplanet Detection**: Detect planets via orbital period variations
3. **Space Mission Planning**: Calculate transfer orbits between planets

---

## **6. Conclusion**
- Kepler's Third Law fundamentally links orbital geometry with dynamics
- Verified numerically through Python simulation
- Generalizes to elliptical orbits via semi-major axis
- Essential tool for modern astronomy and space exploration

