---
title: "FORCED_REPORT Protocol"
permalink: /en/forced_report/
layout: single
author_profile: true
---

## Diagnosing Locked‑in Syndrome

**Problem:** Up to 40% of LIS patients are misdiagnosed as vegetative state.

**Solution:** FORCED_REPORT — a multimodal consciousness detection protocol.

### Three independent channels
1. **BCI** — motor imagery classification accuracy ≥70%
2. **Pupillary** — response to salient stimuli (dilation ≥0.2 mm)
3. **Neurofeedback** — correlation r > 0.3

### Diagnostic rule
Σbᵢ ≥ 2 → CONSCIOUS_LOCKED (LIS)

### Status
- ✅ Formally verified in Coq (module `ForcedReportDecision.v`)
- ✅ Retrospective validation: AUC = 0.947
- ✅ Patent application RU 2026XXXXXX (18 claims)
- ⏳ Requires prospective clinical trials

📄 [More about the protocol](https://github.com/Kalera77/cognitive-shadow-theorem/blob/main/forced_report_protocol.md)