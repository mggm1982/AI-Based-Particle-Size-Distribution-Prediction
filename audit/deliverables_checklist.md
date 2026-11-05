# PHC-351 Project Deliverables Checklist & Verification Audit

**Project:** AI-Based Particle Size Distribution Prediction: Direct Volumetric 3D CNN Regression vs Classical Morphological Watershed in Packed Microtomography  
**Academic Institution:** Indian Institute of Technology Roorkee (IIT Roorkee)  
**Course Code:** PHC-351 (Department of Physics)  
**Instructor / Supervisor:** Prof. Mayank Goswami  
**Student:** Ruhi  
**Audit Date:** 28 October 2026  

---

## Deliverables Status & Evidence Matrix

| Category | Deliverable Item | File Location | Accurate Status | Technical / Evidence Support |
|---|---|---|---|---|
| **Course Submission** | Full Project Source Code | Project root (`src/`, `tests/`, `checkpoints/`) | **COMPLETE & TESTED** | 34/34 tests pass cleanly in 4.56s; zero `#` comments |
| | Verified Submission ZIP | `submission/Google_Drive_Upload/AI_Particle_Size_Distribution_Submission.zip` | **READY FOR SUBMISSION** | 31.64 MB, CRC integrity PASS, 375 verified entries |
| | 60 Dataset Samples Split | `submission/Google_Drive_Upload/{training, validation, testing} data/` | **READY FOR SUBMISSION** | 40 train / 10 val / 10 test (strictly disjoint, zero overlap) |
| | Final IEEE Course Report PDF | `submission/Google_Drive_Upload/ieee_report.pdf` | **READY FOR SUBMISSION** | 6 pages, MiKTeX compiled, balanced Page 6 |
| | Video Presentation Deck | `presentation.pptx` (at root) | **READY FOR RECORDING** | 14 slides, dark modern layout, full spoken presenter notes |
| | Video Presentation Script | `reports/video_presentation_script.md` | **COMPLETE** | 10–12 minute full narration script |
| **Pre-Print Article** | Pre-Print LaTeX Source | `submission/preprint/manuscript.tex` | **COMPLETE (DRAFT)** | Both authors displayed, editable student placeholders |
| | Compiled Pre-Print PDF | `submission/preprint/manuscript.pdf` | **COMPILED & VERIFIED** | Exactly 6 pages (1.66 MB), 0 errors, visual audit passed |
| | Verified Bibliography | `submission/preprint/references.bib` & `manuscript.bbl` | **VERIFIED** | Real peer-reviewed citations ([1] to [8] cited in text) |
| | High-Resolution Figures | `submission/preprint/figures/` | **COMPLETE** | Figs 1–6 (Vector PDF & 300 DPI PNG) |
| | Pre-Print Submission Guide & README | `submission/preprint/README.md` | **COMPLETE** | arXiv / TechRxiv guidelines, categories, pre-upload checklist |
| | Pre-Print Public Upload | arXiv.org / TechRxiv.org | **UNPUBLISHED / NOT UPLOADED** | Preserved locally; awaiting supervisor approval |
| **Patent Application** | Patentability & Prior-Art Assessment | `submission/patent/patentability_assessment.md` | **FEASIBILITY AUDIT COMPLETE** | **PATENTABILITY UNVIABLE ON CURRENT EXPERIMENTAL EVIDENCE** (Watershed more accurate; Section 3(k) bar) |
| | Indian Patent Draft Specification (Form 2) | `submission/patent/patent_draft_provisional_complete.md` | **UNFILED DRAFT (ACADEMIC EXERCISE)** | Claims 1–6 (software); Claims 7–9 labelled PROPOSED PROPHETIC EMBODIMENTS |
| | Patent Claim Mapping Matrix | `submission/patent/claim_mapping_matrix.md` | **AUDITED MATRIX COMPLETE** | Claims 1–6 verified by code; Claims 7–9 flagged as unbuilt |
| | Prior-Art Comparison Table | `submission/patent/prior_art_comparison_table.md` | **AUDITED COMPARISON COMPLETE** | Honest accuracy & cross-hardware latency analysis |
| | IP Protection & Disclosure Notice | `submission/patent/ip_protection_and_disclosure_notice.md` | **ADVISORY COMPLETE** | Statutory links to CGPDTM; US/India/EPO grace period nuances |
| | Questions for IPR Cell & Attorneys | `submission/patent/questions_for_ipr_cell_and_patent_attorney.md` | **ACTIONABLE DRAFT COMPLETE** | 5 formal questions on Sec 3(k), Sec 2(1)(ja), Sec 10(4) |
| | Patent Drawing Sheets (A4) | `submission/patent/figures/` | **COMPLETE** | Sheets 1–5 (FIGS. 1–5; IPO A4 margins, reference numerals, 300 DPI PNG & vector PDF) |
| | Official Patent Filing | Indian Patent Office (IPO) | **NOT FILED / UNFILED** | No forms submitted, no fees paid, no public disclosure |
| **Audit & Review** | Project Technical Audit | `submission/audit/project_audit.md` | **AUDITED & VERIFIED** | Ground truth metrics verified from JSON/CSV |
| | Missing Information & Action Items | `submission/audit/missing_information_and_action_items.md` | **ACTIONABLE DRAFT COMPLETE** | Clear placeholders and unresolved decisions for student/prof |

---

## Status Definitions
- **COMPLETE & TESTED:** Implemented in code, verified by automated unit tests, and fully reproducible.
- **READY FOR SUBMISSION:** Finalized, audited, and ready to hand over for course grading.
- **COMPILED & VERIFIED:** Built from source, inspected visually across all pages, and verified free of layout or reference errors.
- **UNFILED DRAFT (ACADEMIC EXERCISE):** A formal draft prepared for course requirements and institutional review; carries no legal standing and is not submitted to any patent office.
- **PATENTABILITY UNVIABLE ON CURRENT EVIDENCE:** The objective technical verdict that the method in its present state does not meet the legal threshold for a viable patent filing under Indian law.
- **UNPUBLISHED / NOT UPLOADED:** Safely retained within the local workspace; no network disclosure or public release has taken place.
