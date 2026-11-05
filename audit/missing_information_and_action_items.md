# Missing Information, Corrections & Action Items

**Project:** AI-Based Particle Size Distribution Prediction: Direct Volumetric 3D CNN Regression vs Classical Morphological Watershed in Packed Microtomography  
**Course:** PHC-351, Department of Physics, IIT Roorkee  
**Date:** 28 October 2026  
**Audience:** Ruhi (Student Author) & Prof. Mayank Goswami (Faculty Supervisor)  

---

## 1. Summary of Corrections Implemented in this Audit

| Issue Identified | Initial Flaw | Correction Implemented | Location of Corrected Deliverable |
|---|---|---|---|
| **Hypothetical Hardware Claims** | Speculatively claimed physical CT scanners, ball mill motors, cyclone valves, and 4D radiography to circumvent Section 3(k). | **Removed from core claims**; moved into Claims 7–9 and explicitly tagged as `[PROPOSED PROPHETIC EMBODIMENT — NOT IMPLEMENTED OR ENABLED IN REPOSITORY]`. | `submission/patent/patent_draft_provisional_complete.md`, `submission/patent/claim_mapping_matrix.md` |
| **Manufactured Patent Viability** | Drafted patent as if it were a defensible, filing-ready invention. | **Transparent Feasibility Verdict:** Honestly declared that on current evidence, patentability is unviable (watershed is more accurate; cross-hardware latency comparison; Section 3(k) bar). Prepared 5 targeted questions for the IIT Roorkee IPR Cell. | `submission/patent/patentability_assessment.md`, `submission/patent/questions_for_ipr_cell_and_patent_attorney.md` |
| **Categorical Legal Claims on Novelty** | Claimed public preprint upload "permanently destroys patentability in every jurisdiction". | **Statutory Nuance Added:** Delineated Indian strict first-to-file (Sections 29–34) vs US 12-month grace period (35 U.S.C. § 102(b)) vs EPO absolute novelty (Art. 54 EPC). Added direct official CGPDTM links and legal disclaimers. | `submission/patent/ip_protection_and_disclosure_notice.md`, `submission/preprint/README.md` |
| **Visual Verification of Preprint PDF** | Assumed compilation guaranteed quality. | **Full Visual & Textual Inspection Executed:** Extracted all text with layout, verified zero `[?]` or `??` undefined references, checked all 6 figures across pages 3–5, fixed title author line to show both Ruhi and Mayank Goswami, verified bibliography [1]–[8]. | `submission/preprint/manuscript.pdf`, `submission/preprint/README.md`, `submission/preprint/rendered_pages/` |
| **Deliverables Labelling** | Vague or over-optimistic status tags. | **Accurate Labelling Applied:** `UNFILED DRAFT (ACADEMIC EXERCISE)`, `PATENTABILITY UNVIABLE ON CURRENT EVIDENCE`, `COMPILED & VERIFIED`, `UNPUBLISHED / NOT UPLOADED`. | `submission/audit/deliverables_checklist.md` |

---

## 2. Personal Information Requiring Student Confirmation

The following placeholders remain explicitly marked in the preprint and patent drafts:

| Placeholder Marker | Document Location | Required Information | Action for Ruhi |
|---|---|---|---|
| `[CONFIRM ENROLMENT NO.]` | `manuscript.tex` (L19), `patent_draft_provisional_complete.md` (Sec 2) | Official IIT Roorkee Student Enrolment Number | Insert your official enrolment number. |
| `[CONFIRM STUDENT EMAIL]` | `manuscript.tex` (L19), `preprint/README.md` | Active IIT Roorkee Institutional Email (`@ph.iitr.ac.in`) | Replace with your active IITR email. |
| `[CONFIRM ORCID iD]` | `manuscript.tex` (L19), `preprint/README.md` | 16-digit ORCID identifier | Add ORCID if registered, or omit. |

---

## 3. Unresolved Decisions to Align with Prof. Mayank Goswami

### Decision 1: Coursework Submission for PHC-351 Grading
- **Deliverables Ready:**
  1. `submission/Google_Drive_Upload/`: The complete course submission package (ZIP archive, 6-page IEEE report, dataset splits, README).
  2. `presentation.pptx` (at root): 14-slide dark presentation deck for the VideoPPT recording.
  3. `submission/preprint/`: 6-page camera-ready manuscript PDF and complete LaTeX source.
  4. `submission/patent/`: Honest patentability feasibility study and unfiled Form 2 specification draft.
- **Academic Merit:** Presenting an honest patentability assessment that critically assesses Section 3(k) and acknowledges that the classical baseline outperforms the CNN demonstrates authentic scientific integrity and deep understanding of intellectual property law.

### Decision 2: Patent Application Review with IIT Roorkee IPR Cell
- **Options for the Supervisor:**
  - **Option A (Recommended):** Concur with the assessment that patenting a software-only synthetic model is not viable; forgo patent filing and avoid spending institutional patent funds.
  - **Option B (Institutional Consultation):** Submit the 5 questions in `submission/patent/questions_for_ipr_cell_and_patent_attorney.md` along with `patent_draft_provisional_complete.md` to the Dean SRIC / IPR Cell for an official patent attorney opinion.

### Decision 3: Pre-Print Dissemination Timing
- If **Option A** is chosen (no patent pursued): Ruhi and Prof. Goswami can immediately upload `manuscript.tex` to arXiv (`physics.comp-ph`) or `manuscript.pdf` to TechRxiv.
- If **Option B** is chosen (IPR Cell review requested): Defer online preprint upload until the IPR Cell either files a Provisional Specification or formally advises that open publication should proceed.

---

## 4. Current Repository State & Safeguards
- **Zero Public Disclosures Made:** No manuscripts have been uploaded to arXiv, TechRxiv, or GitHub; no patent forms have been submitted to the IPO; no external parties have been contacted.
- **Strictly Local Storage:** All newly generated and corrected deliverables reside safely inside `submission/`.
