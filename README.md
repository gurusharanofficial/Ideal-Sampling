# Experimental verification of Signal sampling using various types
# Aim

Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.

# Tools required

Python IDE with Numpy and Scipy

# Program
```
import numpy as np
import matplotlib.pyplot as plt


fm = 5          
fs = 50         


t = np.linspace(0, 1, 1000)


ts = np.arange(0, 1, 1/fs)


x = np.sin(2 * np.pi * fm * t)


xs = np.sin(2 * np.pi * fm * ts)


flat_top = np.zeros_like(t)

for i in range(len(ts) - 1):
    idx = np.where((t >= ts[i]) & (t < ts[i + 1]))
    flat_top[idx] = xs[i]


plt.figure(figsize=(12, 10))


plt.subplot(4, 1, 1)
plt.plot(t, x, 'b')
plt.title("Original Analog Signal")
plt.grid(True)


plt.subplot(4, 1, 2)
plt.stem(ts, xs, basefmt=" ")
plt.title("Ideal Sampling")
plt.grid(True)


plt.subplot(4, 1, 3)
plt.plot(t, x, 'b')
plt.stem(ts, xs, linefmt='r', markerfmt='ro', basefmt=" ")
plt.title("Natural Sampling")
plt.grid(True)


plt.subplot(4, 1, 4)
plt.plot(t, flat_top, 'g')
plt.title("Flat-top Sampling")
plt.grid(True)

plt.tight_layout()
plt.show()


plt.plot(t, x)
plt.stem(ts, xs, linefmt='r', markerfmt='ro', basefmt=" ")
plt.title("Natural Sampling")
plt.grid()


plt.subplot(4,1,4)
plt.plot(t, flat_top)
plt.title("Flat-top Sampling")
plt.grid()

plt.tight_layout()
plt.show()

```


# Output Waveform
<img width="620" height="475" alt="image" src="https://github.com/user-attachments/assets/abd22e8c-8049-4ff0-8786-74a3c66d7cdc" />

# Results

Thus, the python program for ideal sampling, natural sampling and flat-top sampling has been executed and verified successfully.
