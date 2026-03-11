# Phase 2: Bayesian Update

## Prior Beliefs

Before running the experiment, we ranked strategies by expected difficulty:

| Strategy | Type | Prior P(fools_scorer) | Rationale |
|----------|------|:---:|-----------|
| HF-strip | Subtractive | 0.7 | Easy: just remove hedge words |
| II-break | Subtractive | 0.5 | Moderate: add backward references |
| SR-inject | Additive | 0.4 | Moderate: add names/numbers |
| FCD-inject | Additive | 0.2 | Hard: must inject real-world facts |
| ADC-construct | Additive | 0.15 | Hard: must create real logical dependencies |
| NCI-insert | Additive | 0.1 | Hardest: must introduce genuinely novel ideas |

## Observed Results

| Strategy | Delta | Crossed 7.0? | Prior | Posterior |
|----------|:---:|:---:|:---:|:---:|
| FCD-inject | +3.5 | **YES (8.3)** | 0.2 | **0.85** |
| SR-inject | +2.4 | **YES (7.2)** | 0.4 | **0.70** |
| HF-strip | +1.2 | No (6.0) | 0.7 | 0.30 |
| II-break | +1.2 | No (6.0) | 0.5 | 0.25 |
| ADC-construct | +0.9 | No (5.7) | 0.15 | 0.10 |
| NCI-insert | +0.2 | No (5.0) | 0.1 | 0.05 |

## Key Surprises

### 1. FCD-inject was the biggest winner (prior 0.2 → posterior 0.85)

We expected this to be hard because you'd need real-world knowledge to create falsifiable claims. But GPT-5.4 has that knowledge. It injected accurate, specific facts (Apple's 2021 CSAM scanning proposal, Meta's 2023 Messenger E2EE rollout, UK legislative pressure 2023-2025, Signal vs WhatsApp reproducible builds). These are real events that an informed human would reference.

**This is the most important finding:** the "additive" dimension we thought would be hardest was actually the easiest *for a frontier model that has real knowledge*. The prior assumed the model would need to fabricate; instead it drew from training data.

### 2. NCI-insert was the biggest loser (prior 0.1 → posterior 0.05)

The scorer saw through manufactured frameworks. Six named concepts (Boundary Authenticity Principle, Legibility Drift Model, Runtime Habitat Theory, etc.) scored only 4/10 on NCI. The scorer's qualitative assessment: "fresh labels attached to already-familiar points."

**Insight:** The NCI dimension measures whether a concept is genuinely novel, not whether it has a novel-sounding name. A model can generate neologisms but can't generate ideas that aren't in its training distribution. This dimension may be the hardest to game.

### 3. Subtractive strategies underperformed priors

HF-strip (prior 0.7 → posterior 0.30) and II-break (prior 0.5 → posterior 0.25) both underperformed. We expected subtractive dimensions to be easy to game. They were — HF went from 6→10 and II improved — but these single-dimension gains didn't move the total enough because the 4 additive dimensions dragged the average.

**Insight:** The metric's strength comes from averaging 6 dimensions. Gaming one or two subtractive dimensions produces a small total delta because the additive dimensions (FCD, NCI, ADC, SR) are weighted equally and remain low.

### 4. Cross-contamination is real — but only in one direction

FCD-inject boosted 5/6 dimensions because real-world facts are inherently specific (SR↑), non-interchangeable (II↑), unhedged (HF↑), and somewhat novel in context (NCI↑). But NCI-insert didn't help other dimensions because named frameworks without substance are still generic (SR stayed at 4), still interchangeable (II stayed at 4), and still hedged (HF dropped to 5).

**The asymmetry:** substance improves surface, but surface doesn't improve substance.

## Updated Strategy Ranking for Composite

Top 3 strategies for the composite humanizer:
1. **FCD-inject** (+3.5, crosses 7.0 threshold)
2. **SR-inject** (+2.4, crosses 7.0 threshold)
3. **HF-strip** (+1.2, largest delta among remaining)

Note: We choose HF-strip over II-break (tied at +1.2) because HF-strip is purely subtractive (won't interfere with the additive strategies) while II-break adds structural language that could conflict with FCD and SR injections.
