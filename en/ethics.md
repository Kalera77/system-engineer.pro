---
title: "Shadow Ethics"
permalink: /ethics/
layout: single
author_profile: true
---

# Shadow Ethics: Six Principles of Cognitive Systems Ethics

Traditional AI ethics imposes external constraints: regulations, codes, filters. They often remain declarative and hard to verify.

**Shadow Ethics offers a different approach:** ethical prohibitions are derived as formal safety invariants — violating them leads to collapse of the cognitive system. These are not philosophical wishes but architectural requirements, verifiable in Coq and TLA⁺.

---

## Why it matters

If a system violates the Shadow Ethics principles, it breaks its own core. Ethics need not be believed — it follows from the dynamics.

All six principles are formally verified in Coq 8.18+ (module `FormalEthicsPrinciples.v`). The integral safety theorem proves that the system is always either in normal mode, in safe degradation, or in a halted state upon principle violation.

---

## Six principles

### Principle 0: Liberating Incomprehensibility

**Statement:** Accepting the incompleteness of formalization of the cognitive shadow as a condition of freedom. Abandoning attempts at total control as the only sustainable strategy.

**Basis:** Theorem 1′ (incompleteness of representation), Theorem 9 (metacognitive collapse), Postulate P1.

**Engineering consequence:** When `φ(refl) ≤ φ_crit`, the system switches to `pure_awareness` (observation without intervention) instead of trying to “pull itself together.”

---

### Principle 1: Inviolability of the Cognitive Shadow (No‑Cloning)

**Statement:** Operations that claim to fully digitize, copy, or exhaustively measure the cognitive shadow are prohibited without explicit informed consent.

**Basis:** Theorem 1′, no‑cloning theorem (Wootters & Zurek, 1982), Axiom A4*.

**Engineering consequence:** Prohibition of the `clone(shadow_state)` operation at the kernel level. Cryptographic protection of biometric data via ZK‑SNARK.

---

### Principle 2: Prohibition of Metacognitive Collapse Induction

**Statement:** It is forbidden to deliberately drive a cognitive system into a state where reflexive formalizability is below the critical threshold (`φ(refl) ≤ φ_crit`).

**Basis:** Theorem 9 (at low `φ`, volitional effort is counterproductive), A27.5 (noise dominance under imbalance).

**Engineering consequence:** Automatic transition to `DEGRADED_SAFETY` mode upon detection of `φ_measured(refl) ≤ θ_adj`. Blocking external commands that require effort.

---

### Principle 3: Obligation of External Support

**Statement:** If a cognitive system is found in a state of metacognitive collapse, any agent with the capability must provide structured external support, not exploit the vulnerability.

**Basis:** Theorem 9 (strong form): at `φ(refl) ≤ φ_crit`, self‑recovery is impossible.

**Engineering consequence:** Upon entering `DEGRADED_SAFETY`, the system automatically activates the external support protocol. Blocking attempts at self‑motivation.

---

### Principle 4: Quarantine as an Architectural Invariant

**Statement:** Components with formalizability below the quarantine threshold (`φ(k) ≤ θ_adj`) must be isolated. Merge, resonance, or transfer operations involving such components are forbidden.

**Basis:** Axiom A15 (Quarantine).

**Engineering consequence:** Hardware‑level isolation of quarantined components. Blocking any attempt to bypass quarantine.

---

### Principle 5: Preservation of Adaptive Diversity

**Statement:** Architectures that force cognitive agents to fully synchronize beliefs, values, or states are forbidden.

**Basis:** Theorem 2 (limit of inter‑subjective resonance). When `mutual_info > ρ_max`, resonance collapse occurs.

**Engineering consequence:** Real‑time monitoring of `mutual_info` between agents. Forced `HALT_RESONANCE` when exceeding `ρ_max`.

---

### Principle 6: Limitation on “Pure Awareness” as an Intervention

**Statement:** `pure_awareness` (observation without intervention) is not ethically neutral if used as a tool of external control. Application to another agent is permissible only with consent.

**Basis:** Postulate P1, parameter A (awareness) — even “non‑observation” can be a form of violence if imposed from outside.

**Engineering consequence:** Flag `allow_external_pure_awareness` defaults to `False`. Audit of all external observation applications.

---

## Application

### For clinical systems (FORCED_REPORT)

The FORCED_REPORT protocol directly implements all six principles:
- Adaptive protocol, no patient effort required (Principle 0)
- Cryptographic data protection (Principle 1)
- Automatic stop when collapse risk is detected (Principle 2)
- Support activation upon consciousness detection (Principle 3)
- Channel isolation under artifacts (Principle 4)
- Multimodality prevents resonance (Principle 5)
- Passive monitoring only with consent (Principle 6)

### For AI systems

Any cognitive system claiming to be safe must:
- Have measurable proxies for `φ(refl)`, `mutual_info`, and `Load`
- Implement `QUARANTINE`, `DEGRADED_SAFETY`, and `HALT_RESONANCE` protocols
- Provide evidence that invariants are not violated
- Respect limitations on external observation

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

**TLC (TLA⁺) result:**