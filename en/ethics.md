---
title: "Shadow Ethics"
permalink: /en/ethics/
layout: single
author_profile: true
---

# Shadow Ethics: Six Principles of Cognitive Systems Ethics

Traditional AI ethics imposes external constraints: regulations, codes, filters. They often remain declarative and hard to verify.

**Shadow Ethics offers a different approach**: ethical prohibitions are derived as formal safety invariants, the violation of which leads to the collapse of the cognitive system. These are not philosophical wishes — they are architectural requirements, verifiable in Coq and TLA⁺.

---

## Why this matters

If a system violates the principles of Shadow Ethics, it destroys its own core. Ethics does not require belief — it follows from dynamics.

All six principles are formally verified in Coq 8.18+ (module `FormalEthicsPrinciples.v`). The integral safety theorem proves that the system is always either in normal mode, in safe degradation, or in a halted state when principles are violated.

---

## Six principles

### Principle 0: Liberating Incomprehensibility

**Formulation:** Acceptance of the incompleteness of formalisation of the cognitive shadow as a condition of freedom. Rejection of attempts at total control as the only sustainable strategy.

**Foundation:** Theorem 1′ (incompleteness of representation), Theorem 9 (metacognitive collapse), Postulate P1.

**Engineering consequence:** When `φ(refl) ≤ φ_crit`, the system transitions to `pure_awareness` (pure observation without intervention), rather than trying to "pull itself together".

---

### Principle 1: Inviolability of the Cognitive Shadow (No-Cloning)

**Formulation:** Operations that claim full digitisation, copying, or exhaustive measurement of the cognitive shadow are prohibited without explicit informed consent.

**Foundation:** Theorem 1′, no‑cloning theorem (Wootters & Zurek, 1982), Axiom A4*.

**Engineering consequence:** Prohibition of `clone(shadow_state)` in the system kernel. Cryptographic protection of biometric data via ZK‑SNARK.

---

### Principle 2: Prohibition on Inducing Metacognitive Collapse

**Formulation:** It is prohibited to deliberately drive a cognitive system into a state with reflexivity formalisability below the critical threshold (`φ(refl) ≤ φ_crit`).

**Foundation:** Theorem 9 (at low `φ`, willful effort becomes counterproductive), A27.5 (noise dominance under imbalance).

**Engineering consequence:** Automatic transition to `DEGRADED_SAFETY` when `φ_measured(refl) ≤ θ_adj` is detected. Blocking of external commands that demand effort.

---

### Principle 3: Obligation of External Support

**Formulation:** If a cognitive system is found in a state of metacognitive collapse, any agent capable of providing structured external support must do so, rather than exploit the vulnerability.

**Foundation:** Theorem 9 (strong form): at `φ(refl) ≤ φ_crit`, self‑recovery is impossible.

**Engineering consequence:** Upon entering `DEGRADED_SAFETY`, the system automatically activates the external support protocol. Blocking attempts at self‑motivation.

---

### Principle 4: Quarantine as an Architectural Invariant

**Formulation:** Components with formalisability below the quarantine threshold (`φ(k) ≤ θ_adj`) must be isolated. Operations of merging, resonance, or transfer affecting such components are prohibited.

**Foundation:** Axiom A15 (Quarantine).

**Engineering consequence:** Isolation of quarantined components at the hardware level. Blocking any attempts to bypass quarantine.

---

### Principle 5: Preservation of Adaptive Diversity

**Formulation:** Architectures that compel cognitive agents to full synchronisation of beliefs, values, or states are prohibited.

**Foundation:** Theorem 2 (limit of intersubjective resonance). When `mutual_info > ρ_max`, resonance collapse occurs.

**Engineering consequence:** Monitoring `mutual_info` between agents. Forced `HALT_RESONANCE` when `ρ_max` is exceeded.

---

### Principle 6: Limitation on "Pure Awareness"

**Formulation:** `pure_awareness` (observation without intervention) is not ethically neutral if used as an external control instrument. Its application is allowed only with consent.

**Foundation:** Postulate P1, parameter A (awareness) — even "non‑observation" can be a form of violence if imposed externally.

**Engineering consequence:** Flag `allow_external_pure_awareness` defaults to `False`. Audit of all external observation applications.

---

## Application

### For clinical systems (FORCED_REPORT)

The FORCED_REPORT protocol is a direct implementation of all six principles:
- Adaptive protocol, requiring no effort from the patient (Principle 0)
- Cryptographic data protection (Principle 1)
- Automatic halt at risk of collapse (Principle 2)
- Support activation upon detection of consciousness (Principle 3)
- Channel isolation for artefacts (Principle 4)
- Multimodality prevents resonance (Principle 5)
- Passive monitoring only with consent (Principle 6)

### For AI systems

Any cognitive system claiming safe status must:
- Have measurable proxies for `φ(refl)`, `mutual_info`, and `Load`
- Implement `QUARANTINE`, `DEGRADED_SAFETY`, and `HALT_RESONANCE` protocols
- Provide evidence that invariants are not violated
- Respect external observation constraints

---

## Formal verification

All six principles are formally verified in Coq 8.18+:

| Module | Principle | Key theorem |
|--------|-----------|-------------|
| `Principle0_LiberatingIncomprehensibility.v` | 0 | `Acceptance_As_Survival` |
| `Principle1_NoCloning.v` | 1 | `Cloning_Leads_To_Halt` |
| `Principle2_NoCollapseInduction.v` | 2 | `Collapse_Triggers_Safety` |
| `Principle3_ExternalSupport.v` | 3 | `No_Support_Leads_To_Collapse` |
| `Principle4_Quarantine.v` | 4 | `Quarantine_Violation_Triggers_Isolation` |
| `Principle5_AdaptiveDiversity.v` | 5 | `Resonance_Leads_To_Halt` |
| `Principle6_PureAwarenessLimit.v` | 6 | `Awareness_Misuse_Leads_To_Halt` |

**TLC result (TLA⁺):**