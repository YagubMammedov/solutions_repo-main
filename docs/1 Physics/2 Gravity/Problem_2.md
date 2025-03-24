# Problem 2
# **Escape Velocities and Cosmic Velocities**

## **1. Definitions and Physical Meaning**

### **First Cosmic Velocity (Orbital Velocity)**
- **Definition**: Minimum velocity needed to maintain a stable circular orbit around a celestial body
- **Formula**:  
  \[
  v_1 = \sqrt{\frac{GM}{R}}
  \]
- **Physical Meaning**:  
  Balances gravitational pull with centripetal force to prevent falling or escaping

### **Second Cosmic Velocity (Escape Velocity)**
- **Definition**: Minimum velocity needed to completely escape a celestial body's gravity
- **Formula**:  
  \[
  v_2 = \sqrt{\frac{2GM}{R}} = \sqrt{2} \times v_1
  \]
- **Physical Meaning**:  
  Provides enough kinetic energy to overcome gravitational potential energy

### **Third Cosmic Velocity (Solar System Escape Velocity)**
- **Definition**: Velocity needed at Earth's orbit to escape the Sun's gravitational influence
- **Formula**:  
  \[
  v_3 = \sqrt{v_{esc,\odot}^2 + v_{orb,\oplus}^2}
  \]
  Where:
  - \( v_{esc,\odot} \) = Escape velocity from Sun at Earth's orbit (~42.1 km/s)
  - \( v_{orb,\oplus} \) = Earth's orbital velocity (~29.8 km/s)

## **2. Python Simulation**

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.constants import G

# Celestial body data (radius in m, mass in kg)
bodies = {
    'Earth': (6.371e6, 5.972e24),
    'Moon': (1.737e6, 7.342e22),
    'Mars': (3.390e6, 6.390e23),
    'Jupiter': (6.991e7, 1.898e27)
}

# Calculate velocities
def cosmic_velocities(R, M):
    v1 = np.sqrt(G*M/R)
    v2 = np.sqrt(2)*v1
    return v1, v2

# Compute for all bodies
results = {}
for name, (R, M) in bodies.items():
    results[name] = cosmic_velocities(R, M)

# Third cosmic velocity (Earth-specific)
v_earth_orbit = 29.8e3  # m/s
v_sun_escape = 42.1e3    # m/s
v3 = np.sqrt(v_earth_orbit**2 + (v_sun_escape - v_earth_orbit)**2)
results['Earth'] += (v3,)
```

## **3. Graphical Representations**

### **A. Velocity Comparison Chart**
```python
# Bar chart of velocities
names = list(results.keys())
v1 = [x[0]/1000 for x in results.values()]  # km/s
v2 = [x[1]/1000 for x in results.values()]

x = np.arange(len(names))
width = 0.35

fig, ax = plt.subplots(figsize=(10,6))
bars1 = ax.bar(x - width/2, v1, width, label='1st Cosmic (Orbital)')
bars2 = ax.bar(x + width/2, v2, width, label='2nd Cosmic (Escape)')

ax.set_ylabel('Velocity (km/s)')
ax.set_title('Cosmic Velocities for Different Celestial Bodies')
ax.set_xticks(x)
ax.set_xticklabels(names)
ax.legend()
ax.grid(axis='y')

plt.show()
```
![alt text](image-7.png)
```

## **4. Formulas in Practice**

### **Example Calculation (Earth)**
\[
v_1 = \sqrt{\frac{6.674\times10^{-11} \times 5.972\times10^{24}}{6.371\times10^6}} \approx 7.91 \text{ km/s}
\]
\[
v_2 = \sqrt{2} \times 7.91 \approx 11.19 \text{ km/s}
\]
\[
v_3 = \sqrt{29.8^2 + (42.1-29.8)^2} \approx 16.6 \text{ km/s}
\]
![alt text](image-8.png)

## **7. Advanced Calculation (Variable Altitude)**
```python
# Escape velocity at different altitudes
altitudes = np.linspace(0, 1000, 100)*1000  # 0-1000 km
R_earth = bodies['Earth'][0]
v_esc = np.sqrt(2*G*bodies['Earth'][1]/(R_earth + altitudes))

plt.figure(figsize=(10,6))
plt.plot(altitudes/1000, v_esc/1000)
plt.xlabel('Altitude (km)')
plt.ylabel('Escape Velocity (km/s)')
plt.title('Escape Velocity vs Altitude (Earth)')
plt.grid()
plt.show()
```
![alt text](image-9.png)
This complete analysis provides:
- Clear definitions of cosmic velocities
- Computational verification
- Multiple visualization methods
- Practical examples and applications