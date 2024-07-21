# showimport matplotlib.pyplot as plt
import numpy as np

def soap_bubble_colors(thickness):
    # Thin film interference equation: delta = 2 * n * thickness
    # Where delta is the phase difference and n is the refractive index (approximately 1.33 for soap film)

    # Calculate wavelength of light (visible spectrum)
    wavelength = np.linspace(400, 700, 100)  # nm

    # Calculate phase difference
    delta = 2 * thickness * 1.33 / wavelength  # in nanometers

    # Calculate intensity of reflected light (using cosine function)
    intensity = np.cos(2 * np.pi * delta) ** 2

    # Convert intensity to RGB values for visualization
    red = intensity * 255
    green = np.zeros_like(red)
    blue = (1 - intensity) * 255

    return red, green, blue

# Example thickness of soap film (in nanometers)
thickness = 1000  # nanometers

# Calculate RGB values based on soap bubble thickness
red, green, blue = soap_bubble_colors(thickness)

# Plot the colors
plt.figure(figsize=(8, 4))
plt.fill_between(np.linspace(400, 700, 100), 0, 1, color=[red/255, green/255, blue/255])
plt.title(f"Colors of Soap Bubble (Thickness: {thickness} nm)")
plt.xlabel("Wavelength (nm)")
plt.ylabel("Intensity")
plt.xlim(400, 700)
plt.ylim(0, 1)
plt.show()
