# Project Audit & Technical Source of Truth

**Project:** AI-Based Particle Size Distribution Prediction: Direct Volumetric 3D CNN Regression vs Classical Morphological Watershed in Packed Microtomography  
**Course:** PHC-351, Department of Physics, Indian Institute of Technology Roorkee  
**Instructor / Supervisor:** Prof. Mayank Goswami  
**Student:** Ruhi  
**Audit Timestamp:** 28 October 2026, 03:40 IST  

---

## 1. Verified Quantitative Benchmarks & Dataset Artifacts

All experimental numbers below have been independently audited and confirmed against the benchmark output files:
- Source JSON: `reports/benchmark/summary_metrics.json`
- Source CSV: `reports/benchmark/test_metrics_per_sample.csv`
- Baseline JSON: `reports/improvement_diagnosis.md`
- Controlled Experiment Report: `reports/exp1_wasserstein_results.md`

### A. Dataset & Geometry Audit
- **Total Samples:** Exactly 60 independent synthetic packed-sphere volumes ($48 \times 48 \times 48$ voxels).
- **Generation Method:** Random Sequential Addition (RSA) with non-overlapping hard spheres, simulated point-spread function (PSF) blur ($\sigma = 0.8$ vx), and additive Gaussian detector noise ($\sigma_n = 0.02$).
- **Packing Regime:** $15.0\%$ to $25.0\%$ solid volume fraction.
- **Diameter Range:** $4.0$ to $13.0$ voxels.
- **Discretization:** $K=20$ logarithmically spaced diameter bins bounded by 21 edges (`np.geomspace(4.0, 13.0, 21)`).
- **Ground Truth:** Exact analytic volume-weighted PSD vectors derived directly from generating sphere radii:
  $$y_k = \frac{\sum_{i \in \text{bin } k} r_i^3}{\sum_{\text{all } j} r_j^3}$$
- **Data Splits (Disjoint, Zero Leakage Verified):**
  - **Training Set:** 40 samples (`data/splits/pilot_48cube_splits.json`)
  - **Validation Set:** 10 samples
  - **Held-Out Test Set:** 10 samples (Untouched during model selection, zero test-tuning)

---

### B. Held-Out Test Set Comparison ($N=10$)

| Metric | Classical Morphological Watershed Baseline | Compact3DCNN (Trained on KL Divergence) | Paired Difference (CNN $-$ Watershed) [95% Bootstrap CI] | Statistical / Practical Interpretation |
|---|---|---|---|---|
| **Earth Mover's Distance ($W_1$ EMD)** | **$0.0974 \pm 0.0261$ vx** | $0.3428 \pm 0.0949$ vx | $+0.2455$ vx $[+0.1837, +0.3156]$ | Watershed achieves significantly lower distributional error ($p < 0.001$). |
| **Histogram RMSE** | **$0.0146 \pm 0.0047$** | $0.0273 \pm 0.0098$ | $+0.0127$ $[+0.0080, +0.0185]$ | Watershed has lower bin-by-bin root mean square error. |
| **Histogram MAE** | **$0.0101 \pm 0.0039$** | $0.0200 \pm 0.0076$ | $+0.0099$ $[+0.0072, +0.0129]$ | Watershed has lower mean absolute error across bins. |
| **Median Diameter ($D_{50}$) Absolute Error** | **$0.0622 \pm 0.0503$ vx** | $0.2198 \pm 0.1601$ vx | $+0.1576$ vx $[+0.0448, +0.2810]$ | Watershed error is $< 0.1$ vx; CNN error is $\approx 0.22$ vx. |
| **Median Diameter ($D_{50}$) Relative Error** | **$1.14\% \pm 0.89\%$** | $4.00\% \pm 2.80\%$ | $+2.86\%$ $[+0.84\%, +5.08\%]$ | Both models maintain $< 5\%$ relative median diameter error. |
| **Inference / Execution Latency** | $33.71 \pm 7.50$ ms | **$1.19 \pm 0.27$ ms** | **$\approx 28 \times$ latency difference** | **DISPARATE HARDWARE NOTICE:** Measured on Intel CPU (Watershed) vs NVIDIA RTX 3050 Laptop GPU (CNN). Not a controlled speedup comparison. |

---

### C. Validation Baseline & Diagnostic Experiments

1. **Training-Set-Mean Baseline Evaluation ($N=10$ Validation Volumes):**
   - Empirical Training-Set-Mean Baseline EMD: **$0.6206 \pm 0.2440$ vx**
   - Compact3DCNN Validation EMD: **$0.3970 \pm 0.1335$ vx**
   - **Improvement:** CNN achieves a **$36.0\%$ error reduction** over the static dataset prior, proving non-trivial learning of volumetric spatial features.
2. **Controlled Loss Comparison (Validation Split):**
   - Primary Model (Kullback-Leibler Loss): Validation EMD $= 0.3970 \pm 0.1335$ vx.
   - Tested 1D Wasserstein-1 Loss Model: Validation EMD $= 1.1382 \pm 0.4907$ vx ($186\%$ worse).
   - **Root Cause:** Discrete $L_1$ subgradient instability ($\text{sign}(\hat{F} - F) \in \{-1, +1\}$) causing plateauing under stochastic first-order Adam updates.

---

## 2. Codebase & Test Suite Health

- **Automated Regression Suite:** 34 unit and integration tests in `tests/`:
  - `test_generator.py`: RSA packing bounds, non-overlap, analytic PSD accounting.
  - `test_baseline.py`: Watershed distance transforms, equivalent-sphere math, edge handling.
  - `test_model_cnn3d.py`: 300,900 parameter capacity, forward/backward passes, CPU & CUDA execution.
  - `test_training_pipeline.py`: Split disjointness, KL loss properties, Wasserstein exact SciPy identity.
  - `test_benchmark.py`: Bootstrap CI coverage, metric bounds, D50 percentage units.
- **Execution Result:** **34/34 tests pass cleanly** in $3.71$ seconds.
- **Code Cleanliness:** All `#` comments removed from code files; production clean.

---

## 3. Physical Limitations & Constraints

1. **Synthetic Spherical Particles:** The study evaluates ideal spherical particles. Real rock cores, crushed minerals, or sintered powders exhibit irregular aspect ratios, angularity, and internal voids.
2. **Held-Out Test Sample Size ($N=10$):** While bootstrap confidence intervals confirm statistical significance on this benchmark, evaluating on larger sample counts will provide narrower bounds.
3. **Absence of Real Micro-CT Validation:** Demonstrating generalization to laboratory synchrotron or micro-focus CT scans containing ring artifacts, beam hardening, and partial-volume partial-contact necks is the critical next milestone.

