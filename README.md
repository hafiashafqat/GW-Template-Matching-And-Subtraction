# Gravitational-Wave-Overlap-Analysis

A Python-based research repository exploring multi-source overlapping gravitational-wave signals, cross-correlation template matching, and the empirical limitations of naïve waveform subtraction.

---

## Project Overview
In modern gravitational-wave astronomy (LIGO/Virgo/KAGRA and future detectors like LISA/Einstein Telescope), detecting overlapping signals ("source confusion") from multiple black hole mergers is a significant challenge. This project investigates how overlapping signals interfere with each other, tests cross-correlation methods for template recovery, and documents why direct time-domain subtraction fails for signals with unequal mass and amplitude disparities.

---

## Key Experimental Phases in the Notebook

1. **Simulating Overlapping Signals:**
   * **Signal A (Heavy Merger):** $35 M_\odot + 30 M_\odot$ (High amplitude, full inspiral and merger).
   * **Signal B (Lighter Merger):** $15 M_\odot + 12 M_\odot$ (Injected with a tight $0.02\text{s}$ time shift to cause catastrophic collision).
   * **Composite Stream:** Combined time series representing congested multi-source astrophysical environments.

2. **Template Matching via Cross-Correlation:**
   * Scanning the congested composite stream using normalized cross-correlation (`np.correlate`) with known theoretical blueprints.
   * Successfully recovering Signal A's arrival time via towering correlation peaks.

3. **Empirical Proof of Subtraction Failure (Naïve Limits):**
   * **Observation:** When executing direct time-domain subtraction ($\text{Composite Stream} - \text{Template A}$) without scaling or grid alignment, the resulting output yields a flat zero line or indexing artifacts.
   * **Physical Cause:** Due to time-series indexing offsets, amplitude scaling disparities ($\sim 10^{-19}$ strain differences), and unaligned epoch grids, naïve subtraction fails to isolate the underlying secondary waveform.
   * **Research Takeaway:** Demonstrates that uncalibrated, direct subtraction cannot separate overlapping signals of unequal masses, reinforcing the need for formal mathematical alignment and optimal template scaling.

4. **Evolution to Scaled Subtraction (Resolution):**
   * To overcome the limitations proved in Phase 3, an optimal least-squares amplitude scaling ($\alpha$) and time-grid synchronization method was subsequently developed.
   * **Result:** Properly scaling Template A successfully subtracts it from the composite stream, cleanly revealing the hidden chirp waveform of **Signal B** in the residual.
   * 🔗 **Dedicated Follow-up Repository:** For the complete code, step-by-step alignment logic, and residual plots, visit the [Scaled Subtraction Analysis Repository](https://github.com/hafiashafqat/Scaled_Subtraction_Analysis).

---

## Methodological Trajectory & Next Steps
While optimal time-domain template scaling resolves single-parameter subtraction limits, real-world detector noise and parameter degeneracies present remaining challenges. This repository serves as the baseline proof-of-concept, paving the way for:
- **Joint Bayesian Parameter Estimation:** Simultaneous probabilistic recovery of all overlapping signal parameters without iterative subtraction artifacts.

---

## Tech Stack & Libraries
- **Python**
- **PyCBC** (Gravitational-wave data analysis and waveform generation)
- **NumPy** (Array manipulation and cross-correlation)
- **Matplotlib / Pylab** (Scientific visualization and multi-panel plotting)

---

## Getting Started
1. Clone the repository:
   ```bash
   git clone [https://github.com/hafiashafqat/Gravitational-Wave-Overlap-Analysis.git](https://github.com/hafiashafqat/Gravitational-Wave-Overlap-Analysis.git)
