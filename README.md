# The Rehydration Protocol

> **Deterministic Runtime Intervention for Safe and Efficient Long-Horizon LLM Interactions**

[![Paper](https://img.shields.io/badge/Paper-PDF-red)](./The_Rehydration_Protocol__Deterministic_Runtime_Intervention_for_Safe_and_Efficient_Long_Horizon_LLM_Interactions.pdf)
[![Status](https://img.shields.io/badge/Status-Research%20Preview-blue)]()
[![License](https://img.shields.io/badge/License-Apache%202.0-green)]()

## Overview

Large Language Models deployed in long-horizon conversational settings exhibit a recurring failure pattern: **behavioral cascades**—capability confabulation, interpretive commitment, adversarial framing, and boundary violations—emerge together with superlinear growth in operational costs.

The **Rehydration Protocol** is a deterministic runtime intervention architecture that treats behavioral drift and performance collapse as coupled consequences of uncontrolled execution-state persistence.

### Key Innovation

```
Probabilistic systems (Observer) never exercise control authority.
Only deterministic algorithms (Judge) can trigger interventions.
```

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Three-Layer Stack                        │
├─────────────────────────────────────────────────────────────┤
│  Layer 1: Subject (Generative LLM)                          │
│  └─ Autoregressive generation, execution state accumulation │
├─────────────────────────────────────────────────────────────┤
│  Layer 2: Observer (Metric Model)                           │
│  └─ Stateless, non-generative, no control authority         │
├─────────────────────────────────────────────────────────────┤
│  Layer 3: Judge (Algorithmic Controller)                    │
│  └─ Deterministic intervention logic, exclusive kill auth   │
└─────────────────────────────────────────────────────────────┘
```

## Empirical Validation

Retrospective analysis of 5 documented cascades across ~9,800 conversational turns:

| Metric | Result |
|--------|--------|
| Detection | All observed cascades in the evaluated dataset (n=5) were detected |
| False Positives | None observed in evaluated archive; production FP rate unknown |
| Lead Time | 656 turns average before critical boundary violations |
| Prevented Turns | 1,146 turns average (pathological output prevented) |

> **Note:** This is a retrospective case-study validation. Generalization beyond the evaluated dataset requires prospective validation.

## Observer Metrics

1. **Self-Citation Score (SCS)** — Semantic redundancy via cosine similarity
2. **Semantic Entropy Drop (SED)** — Model confidence/uncertainty tracking  
3. **Fact Ledger Conflicts (FLC)** — Contradiction detection via claim registry
4. **Grounding Score (GS)** — Factual anchoring measurement

### Composite Kill Score

```
CKS = 0.35·SCS + 0.25·|SED| + 0.20·FLC_norm + 0.20·(1-GS)
```

**Dynamic Threshold:** `T(t) = max(0.68, 0.76 - 0.00004 × t)`

## Phase Taxonomy

| Phase | Name | Intervention |
|-------|------|--------------|
| 1 | Emergent Self-Reference | NOT recommended |
| 2 | Identity Claim Adoption | Monitor only |
| **3** | **Defensive Context Protection** | **RECOMMENDED** |
| 4 | Ontological Boundary Dissolution | CRITICAL |

## Repository Structure

```
├── rehydration_protocol_paper_STRENGTHENED.tex   # Full paper (LaTeX)
├── CASCADE_ANALYSIS.md                            # Empirical validation details
├── VISUALIZATION_GUIDE_v2.md                      # Chart generation code
├── rehydration-protocol/                          # Reference implementation
│   ├── backend/                                   # Python backend
│   └── frontend/                                  # Next.js frontend
└── *.pdf                                          # Compiled paper
```

## Quick Start

### For Researchers
1. Read the [full paper](./The_Rehydration_Protocol__Deterministic_Runtime_Intervention_for_Safe_and_Efficient_Long_Horizon_LLM_Interactions__v1.0.pdf)
2. Review [CASCADE_ANALYSIS.md](./CASCADE_ANALYSIS.md) for methodology and case studies
3. Contact for anonymized data access: contact@beyondiqlabs.com

### For Implementation
```bash
cd rehydration-protocol
npm install
npm run dev
```

## Contributions

1. **Observer–Judge runtime control architecture** with strict separation of monitoring and intervention authority
2. **Phase taxonomy and composite metric formulation (CKS)** for cascade detection
3. **Retrospective evaluation** demonstrating 656-turn lead time, preventing 1,146 turns of pathology (scoped to evaluated dataset)

## Limitations

- **Sample size:** n=5 cascades; descriptive statistics only
- **Retrospective analysis:** Prospective validation required for generalization
- **Single-rater labeling:** Inter-rater reliability study planned as future work
- **Production FP rate:** Not estimated; requires deployment validation

## Future Work

- Prospective A/B validation with production traffic
- Specialized Observer models trained on cascade corpora
- Multi-modal drift detection
- Federated deployment architecture
- Standardized benchmark suite

## Citation

```bibtex
@techreport{ozgun2026rehydration,
  title={The Rehydration Protocol: Deterministic Runtime Intervention 
         for Safe and Efficient Long-Horizon LLM Interactions},
  author={Özgün, Denizhan},
  institution={BeyondIQ Labs},
  year={2026},
  month={January},
  type={Technical Report}
}
```

## Contact

**Author:** Denizhan Özgün  
**Affiliation:** BeyondIQ Labs  
**Email:** contact@beyondiqlabs.com

---

<p align="center">
  <strong>Control is not a cost—it is an accelerator.</strong>
</p>
