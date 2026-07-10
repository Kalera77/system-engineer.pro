---
title: "FORCED_REPORT Protocol"
permalink: /en/forced_report/
layout: single
author_profile: true
---

# FORCED_REPORT Protocol

## Clinical problem

**Locked‑in Syndrome (LIS)** — complete paralysis with preserved consciousness.

According to systematic reviews, **up to 40% of LIS patients are initially misclassified** as vegetative state (VS). This leads to:
- Inadequate treatment
- Severe ethical consequences
- Lack of communication with a conscious person

Behavioural scales (CRS‑R) have sensitivity **no higher than 70–80%** in the absence of motor responses. Functional MRI and PET are expensive and rarely available at the bedside.

## Solution

**FORCED_REPORT** (Formal REflexive Detection via Redundant Output Pathways) — a multimodal protocol for detecting consciousness that does not require voluntary motor control.

### Three independent channels

| Modality | Method | Activation threshold |
|----------|--------|----------------------|
| **BCI** (voluntary modulation) | Mu‑rhythm (8–12 Hz) desynchronisation during imagined movement | >3σ above noise |
| **Pupil reflex + HRV** | Pupil dilation and heart rate variability in response to significant stimuli | Dilation >0.2 mm; RMSSD >20 ms |
| **RLPFC neurofeedback** | Feedback on alpha‑power in the prefrontal cortex | Coherence increase >10% over 15 min |

### Diagnostic rule

If **at least two modalities** cross their thresholds:

$$\Sigma b_i \geq 2 \rightarrow \text{CONSCIOUS\_LOCKED (LIS)}$$

The system:
1. Changes patient status from `UNCONSCIOUS` to `CONSCIOUS_LOCKED`
2. Disables quarantine
3. Generates an emergency notification for the clinician
4. Automatically activates `external_support_active` mode (Principle 3 of Shadow Ethics)

## Status

### ✅ Formal verification

The protocol is **formally verified in Coq** (module `ForcedReportDecision.v`):
- **Soundness** proved: transition to `CONSCIOUS_LOCKED` occurs only when all triggers are satisfied
- **No false positives** guaranteed
- Consistency with Shadow Ethics proved

### ✅ Retrospective validation

On CLIS data (16 patients, 2499 epochs):
- **AUC = 0.947 ± 0.081** for CLIS vs healthy (GroupKFold)
- **Specificity confirmed:** control tasks yield AUC ≈ 0.5

### ⏳ Prospective validation

A **prospective multicentre study** on a cohort of N > 100 patients with LIS and VS is required. The protocol is ready; needed:
- Funding
- Clinical partners (intensivists, neurologists)
- Ethics committee approval

## Connection to the theory

FORCED_REPORT is a direct engineering implementation of the cognitive shadow theory:

| Shadow Ethics principle | Implementation in FORCED_REPORT |
|-------------------------|---------------------------------|
| 0 (Liberating incomprehensibility) | Adaptive protocol, requiring no effort from the patient |
| 1 (No‑Cloning) | Cryptographic data protection (ZK‑SNARK) |
| 2 (Collapse prevention) | Automatic halt when φ(refl) ≤ θ_adj |
| 3 (Support obligation) | Automatic activation when Σbᵢ < 2 |
| 4 (Quarantine) | Channel isolation upon artefacts |
| 5 (Diversity) | Multimodality (3 independent channels) |
| 6 (Pure awareness) | Optional passive monitoring with consent |

## How to participate

### For clinicians

If you work in the ICU with patients with disorders of consciousness and are interested in prospective validation of the protocol:

📧 **Email:** kalera77@gmail.com  
📝 **Subject:** "Clinical partnership FORCED_REPORT"

Please include:
- Institution name
- Specialisation (neurology, intensive care)
- Readiness to participate in clinical trials

### For researchers

If you work in BCI, neurofeedback, or neuroimaging:

📧 **Email:** kalera77@gmail.com  
📝 **Subject:** "Research collaboration FORCED_REPORT"

### For investors

If you are interested in commercialisation:

📧 **Email:** kalera77@gmail.com  
📝 **Subject:** "Commercial license FORCED_REPORT"

## Patent protection

A patent application for the FORCED_REPORT protocol has been filed in Russia (2026):
- **Claims:** 18 claims, 3 independent methods
- **Status:** Under examination

## Documentation

📄 [Full protocol](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/PROTOCOL/forced_report_protocol.md)  
📄 [Formal verification (Coq)](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/src/Ethics/ForcedReportDecision.v)  
📄 [Empirical validation](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/EMPIRICAL/Article.md)