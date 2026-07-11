---
title: "Cognitive Shadow Theory"
permalink: /theory/
layout: single
author_profile: true
---

# Cognitive Shadow Theory

> *"The inscrutability of qualia is not a mystical mystery, but a direct physical consequence of the impossibility of measuring a non‑equilibrium chemical process without stopping it. We cannot copy a flame without extinguishing the candle."*

---

## Core Idea

Any computational system that claims to provide an exhaustive formal representation of a cognizing agent inevitably leaves an **unformalizable residue** — the cognitive shadow.

This is formally proven as **Theorem 1′** based on three independent physical barriers:

1. **Landauer’s principle** — any measurement physically alters the system
2. **Holevo bound** — limit of extractable classical information from a quantum system
3. **No‑cloning theorem** — impossibility of exact copying of an arbitrary quantum state

**Key conclusion:** consciousness cannot in principle be fully digitised, copied, or transferred. This is not philosophical speculation, but a formally derivable consequence of the axiomatics.

---

## 1. Formal Core

### 1.1. Axiomatics

The theory is built on **29 axioms** (A1–A29), divided into a static core and a dynamic extension.

**Static core (A1–A8*, A21, A23–A26):**
- Uniqueness of actual experience
- Quantum unpredictability (optional)
- Gödelian incompleteness
- Degradation of formalizability upon transfer
- Structure of paired experience
- Digitisation as a bijection
- Soundness of the model
- Resource‑bounded bridge
- Consistency of components
- Quarantine
- Quantum‑phenomenological correspondence
- Computational irreducibility of qualia
- Operational mutual_info
- Quantum correction of qualia
- Discrete homotopy

**Dynamic extension (A9–A13, A16–A20, A27–A29):**
- Dynamics of the shadow
- Leakage limit
- Topological continuity
- Recursive incompleteness
- Nonlinear computational capacity
- System profile
- Bounded associativity of merge
- Probabilistic initial entropy
- Entropy approximation
- Measurement error of φ
- Interface dynamics (C, S, I)
- Noise dominance under overload
- Plasticity and hysteresis
- Orchestrator

**Falsification criteria** are explicitly defined for each axiom. The theory is open to refutation — this makes it scientific in the Popperian sense.

### 1.2. Key Theorems

| № | Theorem | Essence |
|---|---------|---------|
| **1′** | On cognitive shadow | There exists an unformalizable residue `e*` that cannot be fully represented in system `S` with limited resources |
| **2** | On resonance limit | When `mutual_info > ρ_max`, resonant collapse (`HALT_RESONANCE`) occurs |
| **4** | On cognitive horizon | Predictability drops below 0.51 within finite time `T` |
| **6** | On resource redistribution | Interfaces compete for `R_max`; under imbalance, noise dominates the weaker channel |
| **8** | On degradation of φ(refl) | Chronic imbalance `L ≥ Δ_crit` → irreversible decline of reflexive formalizability |
| **9** | On recursive stability | When `φ(refl) ≤ φ_crit`, volitional effort is counterproductive; collapse ensues without external support |
| **10** | On the principle of signature observability | The signature mapping is non‑injective; reconstruction accuracy is limited by the entropy of the preimage |

All theorems are **constructively proven** in Coq 8.18+ (modules: `CognitiveShadow_Complete.v`, `RecursiveStabilityTheorem.v`, `InterfacesTheorem6.v`, `InterfacesTheorem7.v`, `Theorem8_Degradation.v`, etc.). Proofs do not use `Classical`, `LEM`, or `admit`.

### 1.3. Parameter M and Minimum Entropy Growth

A finite resolvability parameter of state space `M ∈ ℕ, M > 0` is introduced — the number of distinguishable macrostates of the system (hardware‑information limitation). From it, the minimum entropy growth step is derived:

$$\delta_{\min}(M) = \frac{\ln 2}{M}$$

This gives a fundamental limit for all temporal estimates in interface dynamics.

### 1.4. Formal Verification

- **Coq 8.18+** — 27 modules, all theorems proven constructively
- **TLA⁺** — specifications checked on 100% of states, all invariants hold
- **Makefile** — `make verify` reproduces the check

---

## 2. Methodological Level: The Principle of Signature Observability

The theory establishes fundamental limits on what can be observed, measured, and reconstructed about subjective experience from physical signatures.

**Formal setup:**

Let:
- **T** — the set of possible states of the cognitive shadow
- **P** — the set of observable physical states (EEG, behaviour, physiology)
- **I: T → P** — the signature mapping

Then four properties hold:

1. **Direct unobservability of the shadow:**  
   $$\forall t \in T, \quad t \notin P$$  
   The state of the shadow is not a physical state. This is an ontological distinction.

2. **Existence of signatures:**  
   $$\forall t \in T, \quad \exists p \in P: \quad I(t) = p$$  
   Every state of the shadow leaves a measurable trace in the physical world.

3. **Non‑injectivity of the mapping (degeneracy problem):**  
   $$\exists t_1, t_2 \in T: \quad t_1 \neq t_2 \wedge I(t_1) = I(t_2)$$  
   Different shadow states can have identical signatures. Reconstruction is fundamentally ambiguous.

4. **Limited reconstruction:**  
   $$\text{Accuracy} \leq 1 - \frac{H(T_p)}{H(T)}$$  
   The limiting accuracy is determined by the entropy of the preimage.

**Connections to physics:**
- Landauer’s principle (bit erasure → heat)
- Holevo bound (limit on extracting information from a quantum system)
- No‑cloning theorem (impossibility of exact copying)

**Empirical illustration:** AUC = 0.947 for LIS vs healthy, but AUC = 0.742 for VS vs MCS− — a direct manifestation of non‑injectivity.

**Kantian turn:**

| Kant | Theory of Observable Boundaries |
|------|----------------------------------|
| Thing‑in‑itself (Ding an sich) | Cognitive shadow |
| Appearance (Erscheinung) | Signatures (observable) |
| Transcendental conditions | Formal limits of reconstruction |

> We cannot observe the shadow itself, but we can analyse its signatures within fundamental limits.

---

## 3. Empirical Validation

### 3.1. Data

**265,956 EEG epochs** from 9 independent datasets:
- CLIS (16 patients, 2,499 epochs)
- DOC (VS, MCS−, MCS+)
- CAP Sleep Database (86,479 epochs)
- BBBD (65,069 epochs)
- Anesthesia (LOC vs ROC)
- and others

### 3.2. Index φ as Operationalisation of the Signature

$$\varphi = (C \cdot S \cdot I)^{1/3}$$

- **C** — capacity (normalised signal power)
- **S** — selectivity (signal‑to‑noise ratio)
- **I** — integrity (coherence between frontal and occipital leads)

This is a **heuristic 1st‑order model** — not a strict derivation from axiomatics, but a practical approximation. The theory works with any monotonically increasing function of C, S, I.

### 3.3. Key Results

- **AUC = 0.947 ± 0.081** for LIS vs healthy (GroupKFold, 5‑fold)
- **AUC = 0.887** in cross‑population validation (Random Forest + SMOTE)
- **Specificity:** control tasks yield AUC ≈ 0.5
- **MCS− < VS paradox:** φ(MCS−) = 0.154 vs φ(VS) = 0.168 (p = 2.52×10⁻⁴) — confirmation of Theorem 8
- **Parameter A (Awareness):** confirmed (p = 0.045)
- **T (Temporal Coherence):** partially (REM‑sleep only)
- **F (Flexibility) and R (Resilience):** require active protocols

### 3.4. Limitations

- Correlations with the clinical CRS‑R scale are **not significant** (p > 0.05)
- DOC groups do not differ statistically significantly under proper validation
- The 1st‑order model does not explain the context‑dependence of component dominance

---

## 4. Shadow Ethics (six principles — summary)

Shadow Ethics are not external constraints, but **architectural invariants** whose violation leads to system collapse. All six principles are formally verified in Coq.

| Principle | Essence | Engineering consequence |
|-----------|---------|--------------------------|
| **0** | Liberating incomprehensibility | When `φ(refl) ≤ φ_crit` → `pure_awareness` mode |
| **1** | Inviolability of the shadow (No‑Cloning) | Prohibition of `clone(shadow_state)`; ZK‑SNARK |
| **2** | Prohibition of provoking collapse | Automatic `DEGRADED_SAFETY` upon `φ(refl) ≤ θ_adj` |
| **3** | Obligation of external support | Activation of support protocol on collapse |
| **4** | Quarantine as invariant | Isolation of components with `φ(k) ≤ θ_adj` |
| **5** | Preservation of adaptive diversity | Monitoring `mutual_info`; `HALT_RESONANCE` |
| **6** | Restriction on pure awareness | Prohibition of external observation without consent |

For details, see the separate [Shadow Ethics](/ethics) section.

---

## 5. FORCED_REPORT Protocol (brief)

**FORCED_REPORT** — a multimodal protocol for detecting consciousness in patients with complete paralysis, based on three independent channels (BCI, pupillary reflex, neurofeedback). Decision rule: **at least two of three** modalities cross thresholds → `CONSCIOUS_LOCKED`.

- **AUC = 0.947** for LIS vs healthy (retrospective)
- **Formally verified** in Coq (module `ForcedReportDecision.v`)
- **Patent application filed** with Rospatent (18 claims, 3 independent)

For details, see the separate [FORCED_REPORT](/forced_report) section.

---

## 6. Limitations and Open Questions

The theory explicitly acknowledges:

1. **The formula φ = (C·S·I)^(1/3) is a heuristic 1st‑order model**, not a strict derivation from axioms.
2. **Correlations with the CRS‑R clinical scale are not significant** (all p > 0.05).
3. **DOC groups do not differ statistically significantly** under proper validation.
4. **Parameters T and F require new experimental designs** (active protocols).
5. **The 2nd‑order matrix model requires huge samples** for calibration.
6. **The FORCED_REPORT protocol requires prospective multicentre validation.**

This is not weakness. This is **maturity**.

---

## 7. Invitation to Collaborate

The theory has been built by a single researcher, but its development requires interdisciplinary collaboration:
- Neurobiologists — to test predictions on astrocytic networks
- Clinicians — to validate FORCED_REPORT
- Mathematicians — to develop the matrix model
- Philosophers — to critique the ontological foundations
- Engineers — to implement the architectural invariants

All materials are open, code is verifiable, data are reproducible.

---

## Document Navigation

- [Formal core (full text)](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/THEORY/cognitive_shadow_core.md)
- [Dynamic extension (full text)](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/THEORY/cognitive_shadow_dynamics.md)
- [Empirical validation article](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/EMPIRICAL/Article.md)
- [Shadow Ethics (full text)](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/ETHICS/Shadow_Ethics_Formal_Principles.md)
- [Responses to critics](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/EMPIRICAL/Responses_to_Critics.md)
- [Code repository](https://github.com/Kalera77/cognitive-shadow-theory)