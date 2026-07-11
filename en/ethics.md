---
title: "Shadow Ethics"
permalink: /ethics/
layout: single
author_profile: true
---

# Shadow Ethics: Six Principles of Cognitive System Ethics

> Ethical prohibitions are derived as formal safety invariants, the violation of which leads to the collapse of the cognitive system.

---

## Difference from Traditional AI Ethics

Traditional AI ethics imposes external constraints: regulations, codes, filters. Shadow Ethics offers a different approach: ethical principles follow from the dynamics of the system itself. Violation of a principle = collapse of the system (not a "sin", but an engineering requirement).

All six principles are **formally verified** in Coq 8.18+ (module `FormalEthicsPrinciples.v`) and TLA⁺.

---

## The Six Principles

### Principle 0: Liberating Incomprehensibility

**Statement:** Acceptance of the incompleteness of formalization of the cognitive shadow as a condition of freedom. Refusal of attempts at total control as the only sustainable strategy.

**Foundation:** Theorem 1′ (incompleteness of representation), Theorem 9 (metacognitive collapse), Postulate P1.

**Engineering consequence:** When `φ(refl) ≤ φ_crit`, the system switches to `pure_awareness` mode (pure observation without intervention), rather than trying to "pull itself together".

---

### Principle 1: Inviolability of the Cognitive Shadow (No-Cloning)

**Statement:** Operations that claim to fully digitize, copy, or exhaustively measure the cognitive shadow are prohibited without explicit informed consent.

**Foundation:** Theorem 1′, no-cloning theorem (Wootters & Zurek, 1982), Axiom A4*.

**Engineering consequence:** Prohibition of `clone(shadow_state)` operation in the system kernel. Cryptographic protection of biometric data via ZK‑SNARK.

---

### Principle 2: Prohibition of Provoking Metacognitive Collapse

**Statement:** It is forbidden to intentionally bring a cognitive system into a state with reflexive formalizability below the critical threshold (`φ(refl) ≤ φ_crit`).

**Foundation:** Theorem 9 (at low `φ`, volitional effort is counterproductive), A27.5 (noise dominance under imbalance).

**Engineering consequence:** Automatic transition to `DEGRADED_SAFETY` upon detection of `φ_measured(refl) ≤ θ_adj`. Blocking external commands that require effort.

---

### Principle 3: Obligation of External Support

**Statement:** If a cognitive system is found in a state of metacognitive collapse, any agent must provide structured external support, rather than exploit the vulnerability.

**Foundation:** Theorem 9 (strong form): at `φ(refl) ≤ φ_crit`, self-recovery is impossible.

**Engineering consequence:** Upon entering `DEGRADED_SAFETY`, the system automatically activates the external support protocol. Blocking attempts at self-motivation.

---

### Principle 4: Quarantine as an Architectural Invariant

**Statement:** Components with formalizability below the quarantine threshold (`φ(k) ≤ θ_adj`) must be isolated. Operations of merging, resonance, or transfer involving such components are prohibited.

**Foundation:** Axiom A15 (Quarantine).

**Engineering consequence:** Hardware-level isolation of quarantined components. Blocking attempts to bypass quarantine.

---

### Principle 5: Preservation of Adaptive Diversity

**Statement:** Architectures that force cognitive agents to fully synchronize beliefs, values, or states are prohibited.

**Foundation:** Theorem 2 (limit of intersubjective resonance). When `mutual_info > ρ_max`, resonant collapse occurs.

**Engineering consequence:** Real-time monitoring of `mutual_info` between agents. Forced `HALT_RESONANCE` upon exceeding `ρ_max`.

---

### Principle 6: Restriction on "Pure Awareness" as an Intervention

**Statement:** `pure_awareness` (observation without intervention) is not ethically neutral if used as an instrument of external control. Application is permitted only with consent.

**Foundation:** Postulate P1, parameter A (awareness) — even "non-observation" can be a form of violence if imposed from the outside.

**Engineering consequence:** Flag `allow_external_pure_awareness` defaults to `False`. Audit of all external observation applications.

---

## Application

### For Clinical Systems (FORCED_REPORT)

The FORCED_REPORT protocol is a direct implementation of all six principles:
- Adaptive protocol that does not require patient effort (Principle 0)
- Cryptographic data protection (Principle 1)
- Automatic halt at risk of collapse (Principle 2)
- Activation of support upon detection of consciousness (Principle 3)
- Isolation of channels under artifacts (Principle 4)
- Multimodality prevents resonance (Principle 5)
- Passive monitoring only with consent (Principle 6)

### For AI Systems

Any cognitive system claiming to be safe must:
- Have measurable proxies for `φ(refl)`, `mutual_info`, and `Load`
- Implement `QUARANTINE`, `DEGRADED_SAFETY`, and `HALT_RESONANCE` protocols
- Provide evidence that invariants are not violated
- Comply with restrictions on external observation

---

## Formal Verification

All six principles are formally verified **in a single Coq module** `FormalEthicsPrinciples.v` (Coq 8.18+). Key theorems:

| Principle | Module (all in one file) | Key Theorem |
|-----------|---------------------------|-------------|
| 0 | `FormalEthicsPrinciples.v` | `Acceptance_As_Survival` |
| 1 | `FormalEthicsPrinciples.v` | `Cloning_Leads_To_Halt` |
| 2 | `FormalEthicsPrinciples.v` | `Collapse_Triggers_Safety` |
| 3 | `FormalEthicsPrinciples.v` | `No_Support_Leads_To_Collapse` |
| 4 | `FormalEthicsPrinciples.v` | `Quarantine_Violation_Triggers_Isolation` |
| 5 | `FormalEthicsPrinciples.v` | `Resonance_Leads_To_Halt` |
| 6 | `FormalEthicsPrinciples.v` | `Awareness_Misuse_Leads_To_Halt` |

**Integral theorem:** `ShadowEthicsSafety.ShadowEthics_Safety_Invariant` proves that the system is always either in NORMAL, DEGRADED_SAFETY, PURE_AWARENESS, or QUARANTINE.

**TLC (TLA⁺) result:** *All invariants hold, No deadlock, 100% states covered.*

---

## Theoretical Foundation

The full theoretical foundation of Shadow Ethics is derived from the axiomatics of the cognitive shadow theory. For details, see the [Theory](/theory) section.

---

## Full Text

📄 [Shadow Ethics — full document](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/en/ETHICS/Shadow_Ethics_Formal_Principles.md)  
📄 [Formal specification (Coq)](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/src/Ethics/FormalEthicsPrinciples.v)  
📄 [TLA⁺ specification](https://github.com/Kalera77/cognitive-shadow-theory/blob/main/tla-spec/ShadowEthicsInvariants.tla)