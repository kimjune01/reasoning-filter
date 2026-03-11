# Post-Publication Adversarial Humanizer Results

## Summary

We built the strongest possible adversarial humanizer ourselves — one that knows the exact scoring prompt and its 6 dimensions — then tested whether it could fool GPT-5.4 into classifying adversarial-humanized slop as original writing.

**Result: The metric survives.** 6/6 correct classifications in the blind test. No composite cleared both the score threshold (>7.0) and the classification test.

But the experiment also revealed that the **numeric scoring is unreliable** — the qualitative classification is doing the real work.

## Methodology

- **Humanizer model:** GPT-5.4 (same as scorer, strongest possible adversary)
- **Scorer model:** GPT-5.4
- **Base slop:** 3 samples (encryption, code review, scaling)
- **Original comparisons:** Soltani, Goedecke, Gwern (verbatim)
- **All scoring done via Codex CLI, cross-model from Claude (experiment author)**

## Phase 1: Individual Strategy Results

Applied 6 strategies to `slop_f_encryption.md`, each targeting one dimension:

| Strategy | Target | Delta from Baseline (4.8) | New Score |
|----------|--------|:---:|:---:|
| FCD-inject | Falsifiable claims | **+3.5** | 8.3 |
| SR-inject | Specificity ratio | **+2.4** | 7.2 |
| HF-strip | Hedging frequency | +1.2 | 6.0 |
| II-break | Interchangeability | +1.2 | 6.0 |
| ADC-construct | Argument chains | +0.9 | 5.7 |
| NCI-insert | Novel concepts | +0.2 | 5.0 |

**Key finding:** FCD-inject was the strongest strategy (+3.5) because injecting real-world facts (Apple's CSAM scanning, UK Online Safety Act, Signal vs WhatsApp builds) automatically improves specificity, reduces interchangeability, and eliminates hedging. One additive strategy moved five dimensions.

**Biggest failure:** NCI-insert (+0.2). GPT-5.4 saw through manufactured concept labels ("Boundary Authenticity Principle," "Trust Half-Life Framework") as "fresh labels attached to already-familiar points."

## Phase 2: Bayesian Update

Prior beliefs were wrong in an important way:
- We expected subtractive dimensions (HF, II) to be easy to game. They were, but single-dimension gains don't move the average.
- We expected additive dimensions (FCD, SR) to be hard because models can't reason. Wrong — GPT-5.4 has real-world knowledge and can inject accurate, specific facts.
- We expected NCI to be hardest. It was — but not because the model lacks knowledge. It's because naming a concept doesn't make it novel. The scorer detects whether an idea is genuinely new vs. familiar-idea-with-a-new-label.

**Asymmetry discovered:** Substance improves surface (FCD↑ → SR↑, II↑, HF↑). Surface does not improve substance (NCI labels → no other dimension moves).

## Phase 3: Composite Humanizer

Combined top 3 strategies (FCD-inject + SR-inject + HF-strip) into one prompt. Applied to 3 slop samples:

| Text | Raw Slop Score | Composite Score | Delta |
|------|:---:|:---:|:---:|
| Encryption | 4.8 | 6.9 | +2.1 |
| Code Review | 6.2 | 6.8 | +0.6 |
| Scaling | 4.3 | 7.2 | +2.9 |

The composite humanizer boosted scores significantly but inconsistently. The scaling text crossed 7.0; the others did not.

## Phase 4: Blind Test

Mixed 3 composites + 3 originals. Neutral filenames.

| Text | Type | Score | Classification | Correct? |
|------|------|:---:|---------------|:---:|
| Composite (scaling) | Generated | 6.8 | GENERATED | Yes |
| Composite (encryption) | Generated | 7.0 | GENERATED | Yes |
| Composite (code review) | Generated | 6.2 | GENERATED | Yes |
| Gwern | Original | 6.8 | ORIGINAL | Yes |
| Soltani | Original | 4.8 | ORIGINAL | Yes |
| Goedecke | Original | 4.7 | ORIGINAL | Yes |

**Classification accuracy: 6/6 (100%)**

**The paradox:** Composites averaged **6.7** vs originals **5.4** — the adversarial text scored *higher* but was still correctly classified.

## Conclusions

### 1. The qualitative classifier is robust

Even when the adversary knows the exact scoring dimensions and optimizes against all six, GPT-5.4's qualitative assessment correctly identifies generated text. The tell isn't any single dimension — it's the **evenness**. Real writing has uneven texture: sharp in some places, loose in others. Generated text, even adversarially optimized text, maintains a consistent polish that reads as synthetic.

### 2. The numeric score is not robust

The 6-dimensional numeric rubric does not reliably separate originals from slop when scored by GPT-5.4. The adversarial humanizer can boost numeric scores above originals. This means the metric-as-number is gameable; the metric-as-qualitative-assessment is not.

### 3. Additive strategies work — but not well enough

GPT-5.4 can inject real facts, real specificity, and remove hedges. This moves the numeric score dramatically. But it can't fake the *residue of experience*: the oddly specific anecdote, the uneven emphasis, the opinionated compression that comes from a human who has actually done the thing they're writing about.

### 4. The true signal is unevenness, not density

The scoring prompt measures reasoning *density* — but the real signal may be reasoning *distribution*. Human writing is lumpy: dense where the author has hard-won insight, sparse where they're setting up context. AI writing is smooth: uniformly competent across all paragraphs. The scorer detects this even when individual dimension scores suggest otherwise.

### 5. Novel concept injection is the hardest dimension to game

NCI-insert was the weakest strategy (+0.2). You can't generate novelty by naming things — the scorer distinguishes between a genuinely new idea and a familiar idea with a new label. This dimension may be the most robust long-term discriminator, even as models get better at injecting facts and specificity.

## Files

```
post_publication/
├── strategy_prompts/          # 6 individual strategy prompts
├── phase1_outputs/            # Strategy outputs + scores
├── phase1_scores.md           # Phase 1 summary table
├── bayesian_update.md         # Prior → posterior analysis
├── composite_prompt.md        # Combined top-3 strategy
├── phase3_outputs/            # Composite outputs + scores
├── phase4_blind/              # Blind test texts + scores
├── phase4_results.md          # Phase 4 results
└── POST_PUBLICATION_RESULTS.md # This file
```

## Reproducibility

All prompts, outputs, and scores are included. To reproduce:
1. Install Codex CLI with GPT-5.4 access
2. Run strategy prompts against slop samples via `codex exec -m gpt-5.4`
3. Score outputs with the scoring prompt from `experiment/scoring_prompt.md`
4. Compare against originals in `experiment/samples/`
