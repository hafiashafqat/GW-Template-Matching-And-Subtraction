# Gravitational-Wave-Overlap-Analysis

A Python-based research repository exploring multi-source overlapping gravitational-wave signals, cross-correlation template matching, and the empirical limitations of naïve waveform subtraction.

---

## Project Overview
In modern gravitational-wave astronomy (LIGO/Virgo/KAGRA), detecting overlapping signals ("source confusion") from multiple black hole mergers is a significant challenge. This project investigates how overlapping signals interfere with each other, tests cross-correlation methods for template recovery, and documents why direct time-domain subtraction fails for signals with unequal mass and amplitude disparities.

---

## Key Experimental Phases in the Notebook

1. **Simulating Overlapping Signals:**
   * **Signal A (Heavy Merger):** $35 M_\odot + 30 M_\odot$ (High amplitude, full inspiral and merger).
   * **Signal B (Lighter Merger):** $15 M_\odot + 12 M_\odot$ (Injected with a tight $0.02\text{s}$ time shift to cause catastrophic collision).
   * **Composite Stream:** Combined time series representing congested multi-source astrophysical environments.

2. **Template Matching via Cross-Correlation:**
   * Scanning the congested composite stream using normalized cross-correlation ($\text{np.correlate}$) with known theoretical blueprints.
   * Successfully recovering Signal A's arrival time via towering correlation peaks.

3. **Evaluating Subtraction Limits & Failure:**
   * Testing direct time-domain subtraction ($\text{Composite Stream} - \text{Template A}$) to isolate Signal B.
   * Demonstrating empirical failure (yielding a flat residual zero line) due to amplitude scaling disparities ($\sim 10^{-19}$ strain differences), epoch indexing offsets, and background noise dominance.

4. **Methodological Trajectory:**
   * Highlighting the flaws of iterative cleaning (such as characteristic blending and residual waveform distortion).
   * Paving the way for advanced **Joint Bayesian Parameter Estimation** (upcoming phase).

---

## Tech Stack & Libraries
* **Python**
* **PyCBC** (Gravitational-wave data analysis and waveform generation)
* **NumPy** (Array manipulation and cross-correlation)
* **Matplotlib / Pylab** (Scientific visualization and multi-panel plotting)

---

## Getting Started
1. Clone the repository:
   ```bash
   git clone [https://github.com/your-username/Gravitational-Wave-Overlap-Analysis.git](https://github.com/your-username/Gravitational-Wave-Overlap-Analysis.git)
