## Part A: Structured

### 1. The period of a signal is 50 ms. What is its frequency in kilohertz?
$$f = \frac{1}{T} = \frac{1}{0.05\text{ s}} = 20\text{ Hz} = 0.02\text{ kHz}$$

### 2. Draw the time-domain plot of a sine wave with maximum amplitude of 15 volts, a frequency of 5, and a phase of 270 degrees.
```
Voltage (V)
 +15 |       .-.        .-.
     |      /   \      /   \
   0 |-----+----+-----+----+---- Time (s)
     |    /      \   /      \  
 -15 |  -'        `-'        `-'
     0.00 0.05  0.10  0.15  0.20
```

### 3. What is the bandwidth of a signal that can be decomposed into four sine waves with frequencies at 0, 20, 50, and 200 Hz? All maximum amplitudes are the same. Draw the frequency spectrum.
Bandwidth = 200Hz - 0Hz = 200Hz

```
Amplitude
   A |  |       |        |          |
     +--+-------+--------+----------+---> Frequency (Hz)
        0      20       50         200
```

### 4. A signal travels from point A to point B. At point A the signal power is 100W. At point B the power is 80W. What is the attenuation in decibel?
$$\text{dB} = 10\log_{10}\left(\frac{80}{100}\right) = 10\log_{10}(0.8) \approx -0.97\text{ dB}$$

### 5. Suppose a signal travels through a transmission medium and its power is reduced to one-half. What is the attenuation in decibel?
$$\text{dB} = 10\log_{10}(\frac{1}{2}) \approx -3.01\text{ dB}$$

### 6. A signal travels through an amplifier, and its power is increased 10 times. What is the attenuation in decibel?
$$\text{dB} = 10\log_{10}(10) = 10\text{ dB}$$

### 7. A line has a signal-to-noise ratio of 1000 and a bandwidth of 4000 KHz. What is the maximum data rate supported by this line?
$$C = 4,000,000 \times \log_2(1 + 1000) = 4,000,000 \times \log_2(1001)$$
$$C \approx 4,000,000 \times 9.9672 \approx 39,868,900\text{ bps} \approx 39.87\text{ Mbps}$$

### 8. A file contains 16 million bytes. How long does it take to download this file using a 56-Kbps channel? 4-Mbps channel?
$$\text{File size} = 16,000,000\text{ bytes} \times 8\text{ bits/byte} = 128,000,000\text{ bits}$$

* **56-Kbps channel ($56,000\text{ bps}$):**
$$\text{Time} = \frac{128,000,000\text{ bits}}{56,000\text{ bps}} \approx 2285.71\text{ seconds} \quad (\approx 38.1\text{ minutes})$$


* **4-Mbps channel ($4,000,000\text{ bps}$):**
$$\text{Time} = \frac{128,000,000\text{ bits}}{4,000,000\text{ bps}} = 32\text{ seconds}$$


