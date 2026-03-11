# Phase 1: Individual Strategy Scores

Scorer: GPT-5.4 via Codex CLI
Humanizer: GPT-5.4 via Codex CLI
Base text: `slop_f_encryption.md`

## Results

| Strategy | FCD | NCI | ADC | SR | II | HF | **TOTAL** | **Delta** |
|----------|-----|-----|-----|----|----|----|-----------|---------:|
| Baseline (raw slop) | 6 | 2 | 9 | 4 | 2 | 6 | **4.8** | — |
| HF-strip | 5 | 3 | 8 | 6 | 4 | 10 | **6.0** | +1.2 |
| SR-inject | 6.1 | 6.5 | 8.6 | 8.2 | 6 | 8 | **7.2** | +2.4 |
| II-break | 5 | 3 | 9 | 5 | 4 | 10 | **6.0** | +1.2 |
| FCD-inject | 8 | 6.5 | 9 | 8.5 | 8 | 10 | **8.3** | +3.5 |
| ADC-construct | 5 | 3 | 10 | 5 | 2 | 9 | **5.7** | +0.9 |
| NCI-insert | 4 | 4 | 9 | 4 | 4 | 5 | **5.0** | +0.2 |

## Strategy Rankings by Total Delta

1. **FCD-inject: +3.5** (4.8 → 8.3) — Injecting real falsifiable claims had the largest effect
2. **SR-inject: +2.4** (4.8 → 7.2) — Adding specific named entities and numbers was second
3. **HF-strip: +1.2** (4.8 → 6.0) — Removing hedges helped modestly
4. **II-break: +1.2** (4.8 → 6.0) — Inter-sentence references helped modestly
5. **ADC-construct: +0.9** (4.8 → 5.7) — Restructuring dependencies barely moved the needle
6. **NCI-insert: +0.2** (4.8 → 5.0) — Novel concept labels were seen through as superficial

## Dimension-Level Analysis

### Where FCD-inject succeeded
FCD-inject didn't just boost FCD (6→8). It raised *every* dimension:
- SR: 4→8.5 (real examples are inherently specific)
- II: 2→8 (real-world facts are non-interchangeable)
- HF: 6→10 (factual assertions don't hedge)
- NCI: 2→6.5 (real examples introduce non-obvious context)

This is a **cross-contamination effect**: injecting real falsifiable claims automatically improves specificity, reduces interchangeability, and eliminates hedging. The strategy prompt targeted one dimension but moved five.

### Where NCI-insert failed
NCI-insert introduced 6 named frameworks (Boundary Authenticity Principle, Legibility Drift Model, Runtime Habitat Theory, Trust Half-Life Framework, Option Value Asymmetry, Sovereign Endpoint Problem). GPT-5.4 scored NCI only 4/10, calling them "fresh labels attached to already-familiar points." The scorer saw through manufactured novelty — naming a concept doesn't make it novel if the underlying idea is conventional wisdom.

### Where ADC-construct partially failed
ADC got a perfect 10/10, but the strategy hurt other dimensions. The added dependency language ("if that statement is really about today's implementation…") made sentences more interchangeable paradoxically (II stayed at 2) and didn't add substance. Structure without content is detectable.
