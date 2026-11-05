# PHC-351 Final Project Submission
## AI-Based Particle Size Distribution Prediction: Direct Volumetric 3D CNN Regression vs Classical Morphological Watershed

**Course:** PHC-351  
**Department:** Department of Physics, Indian Institute of Technology Roorkee  
**Instructor:** Prof. Mayank Goswami  
**Submission Date:** October 2026  

---

## 1. Submission Overview & Contents

This submission folder contains all experimental data, report deliverables, and reproducible source code for the project comparing a compact 3D Convolutional Neural Network against 3D morphological watershed segmentation for particle size distribution (PSD) prediction in packed microtomography volumes.

| Item | Description |
|:---|:---|
| `training data/` | 40 synthetic $48^3$ volumes with metadata and exact analytical PSD targets |
| `validation data/` | 10 independent volumes for model validation and hyperparameter tuning |
| `testing data/` | 10 held-out volumes for benchmark evaluation |
| `ieee_report.pdf` | 6-page research paper formatted according to IEEE conference standards |
| `AI_Particle_Size_Distribution_Submission.zip` | Complete reproducible project archive (source code, tests, checkpoints, and reports) |
| `presentation.pptx` | Presentation slide deck |
| `VideoPPT` | Video presentation |
| `README.md` | Submission overview, dataset split schema, and reproduction guide |

---

## 2. Dataset Partitioning & Data Schema

The dataset consists of 60 synthetic packed-sphere volumes ($48^3$ voxels) generated via Random Sequential Addition (RSA) with packing fractions from $15\%$ to $25\%$. The volumes are partitioned according to `data/splits/pilot_48cube_splits.json`:
- **Training Set (40 samples):** `sample_000_lognormal_pf15` through `sample_059_bimodal_pf25`
- **Validation Set (10 samples):** `sample_006_lognormal_pf18`, `sample_010_lognormal_pf15`, `sample_014_lognormal_pf20`, `sample_021_lognormal_pf22`, `sample_026_lognormal_pf25`, `sample_030_bimodal_pf20`, `sample_034_bimodal_pf18`, `sample_045_bimodal_pf18`, `sample_051_bimodal_pf25`, `sample_053_bimodal_pf22`
- **Testing Set (10 samples):** `sample_004_lognormal_pf25`, `sample_007_lognormal_pf22`, `sample_018_lognormal_pf15`, `sample_025_lognormal_pf25`, `sample_027_lognormal_pf15`, `sample_035_bimodal_pf20`, `sample_036_bimodal_pf22`, `sample_044_bimodal_pf15`, `sample_049_bimodal_pf25`, `sample_052_lognormal_pf20`

All splits are disjoint ($\text{Train} \cap \text{Val} = \emptyset$, $\text{Train} \cap \text{Test} = \emptyset$, $\text{Val} \cap \text{Test} = \emptyset$) with zero sample overlap.

### Sample Structure
Each sample folder includes 5 files:
1. `ct_volume.npy`: $48 \times 48 \times 48$ float32 synthetic CT volume with detector noise and point spread blur.
2. `labeled_volume.npy`: $48 \times 48 \times 48$ int32 ground-truth particle label map.
3. `metadata.json`: Generation metadata (distribution parameters, target and achieved packing fractions, particle count).
4. `particles.csv`: Exact coordinates $(z, y, x)$ and radii for every placed sphere.
5. `psd_ground_truth.json`: Exact 20-bin analytical PSD histogram and bin boundaries.

---

## 3. Reproduction Instructions

To reproduce the benchmark results or run unit tests from the included ZIP:

1. **Extract Archive & Set Up Environment:**
   ```powershell
   Expand-Archive -Path AI_Particle_Size_Distribution_Submission.zip -DestinationPath .
   cd AI_Particle_Size_Distribution
   python -m venv .venv
   .\\.venv\\Scripts\\Activate.ps1
   pip install -r requirements.txt
   ```

2. **Run Unit Tests (34 tests):**
   ```powershell
   python -m unittest discover tests -v
   ```

3. **Run Held-Out Test Benchmark:**
   ```powershell
   python scripts/run_benchmarking.py
   ```
   Evaluates both models on the 10 test samples and outputs results to `reports/benchmark/`.

4. **Recompile IEEE Paper:**
   ```powershell
   cd reports
   bibtex ieee_report
   pdflatex ieee_report.tex
   ```
