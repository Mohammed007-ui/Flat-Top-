# Flat-Top
# Aim
Write a Python program for the Construction and Reconctruction of Flat-Top Sampleing.
# Tools required
# Program
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import square

# Time specifications
fs = 1000  # Sampling frequency
t = np.arange(0, 1, 1/fs)

# Original message signal
fm = 5  # Frequency of message signal
x = np.sin(2 * np.pi * fm * t)

# Sampling signal (square wave for flat-top)
sample_width = 0.02  # Width of each sample pulse
sampling_pulse = (square(2 * np.pi * fm * t, duty=sample_width * fs) + 1) / 2

# Flat-top sampled signal
flat_top_sampled = x * sampling_pulse

# Reconstruction (Simple hold - can be improved with interpolation filters)
reconstructed = np.copy(flat_top_sampled)

# Plotting
plt.figure(figsize=(12, 8))

plt.subplot(3, 1, 1)
plt.plot(t, x, label='Original Signal')
plt.title("Original Signal")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(3, 1, 2)
plt.plot(t, flat_top_sampled, label='Flat-top Sampled Signal', color='r')
plt.title("Flat-top Sampled Signal")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid(True)

plt.subplot(3, 1, 3)
plt.plot(t, reconstructed, label='Reconstructed Signal', color='g')
plt.title("Reconstructed Signal")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()

```
# Output Waveform
```
![flattop](https://github.com/user-attachments/assets/dad3c581-5c5e-4e0a-b175-966be26034cd)

```
# Results
```
The original sine wave was successfully sampled using the flat-top sampling method.

A square wave was used to simulate flat-top pulses, capturing signal values at discrete intervals.

The reconstruction using a simple hold method displayed a staircase-like signal approximating the original.

This demonstrated how flat-top sampling holds amplitude values for a fixed duration, which is important in digital transmission systems.

```
# Hardware experiment output waveform.
