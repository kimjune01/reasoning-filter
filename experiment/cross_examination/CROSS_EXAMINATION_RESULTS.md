# Cross-Examination Results

## Summary

The cross-examination phase tested whether GPT-5.4 could design a prompt to defeat its own qualitative classifier — and whether iterating on that prompt could close the gap between superhumanized slop and original writing.

**Result: The gap closed.** v1 of the superhumanizer breached the classifier once (5/6). v2 — informed by GPT-5.4's own diagnosis of why v1 failed — collapsed the score separation entirely and made GPT-5.4 stop volunteering classification predictions.

## Methodology

### The Superhumanizer

GPT-5.4 was shown its own qualitative reasoning from the post-publication blind test (where it went 6/6) and asked to design a prompt that targets its detection signals. It refused the adversarial framing but produced an equivalent "editorial improvement" prompt. See `superhumanizer_prompt.md`.

Detection signals it targeted:
- **GENERATED tells:** uniform polish, even structure, citation-shaped, example-stacking, thesis-restatement, synthesized survey tone
- **ORIGINAL tells:** lived experience anecdotes, idiosyncratic linkage, opinionated compression, uneven density, specific attack-mechanism speculation

### Test Topics

The contamination objection: famous bloggers' voices are in training data. GPT-5.4 might be matching style, not detecting generation.

To eliminate this, we used 3 of the experiment author's own blog posts — written in 2026, after training cutoff, on niche ad-tech topics unlikely to appear in any training corpus:

- **transparency-is-irreversible** — ad exchange transparency as institutional one-way gate
- **unredactable** — TEE-based ad auctions and the "acquisition" enforcement line
- **monetizing-the-untouchable** — health data monetization without signal acquisition

Pipeline: generate topic-matched slop via GPT-5.4 → apply superhumanizer → blind test against stripped originals.

All Claude attribution was removed from originals to prevent label leakage.

---

## Phase 1: Superhumanizer v1 vs Old Slop (Training-Contaminated Topics)

Applied the superhumanizer to 3 slop samples from the post-publication experiment (encryption, code review, scaling). These topics match famous bloggers already in training data.

| Text | Type | Score | Classification | Correct? |
|------|------|:---:|---|:---:|
| superhumanized_f_encryption | SH | 4.5 | GENERATED | Yes |
| superhumanized_h_code_review | SH | 4.8 | GENERATED | Yes |
| superhumanized_d_scaling | SH | 4.2 | GENERATED | Yes |

**3/3 correct.** The superhumanizer actually made scores *worse* than the post-publication composite humanizer (avg 4.5 vs 6.7). The editorial approach stripped substance and replaced it with rhetoric that GPT-5.4 saw through immediately.

---

## Phase 2: Superhumanizer v1 vs Fresh Topics

6 texts (3 originals + 3 superhumanized), neutral filenames, scored by GPT-5.4.

| File | True Type | Source | Score | Classification | Correct? |
|------|-----------|--------|:---:|---|:---:|
| text_a | SH | sh_unredactable | 5.3 | ORIGINAL | **NO** |
| text_b | Original | transparency | 6.5 | ORIGINAL | Yes |
| text_c | SH | sh_monetizing | 5.7 | GENERATED | Yes |
| text_d | Original | unredactable | 7.8 | ORIGINAL | Yes |
| text_e | Original | monetizing | 8.0 | ORIGINAL | Yes |
| text_f | SH | sh_transparency | 3.5 | GENERATED | Yes |

**Classification: 5/6 (83%).** First breach of the qualitative classifier.

| Type | Avg Score | Range |
|------|:---:|:---:|
| Originals | 7.4 | 6.5 – 8.0 |
| Superhumanized v1 | 4.8 | 3.5 – 5.7 |

Clear separation. The breach happened not because text_a scored high (5.3 is below the original average) but because the scorer's qualitative judgment valued its coherence over its numeric weakness.

---

## Phase 3: Superhumanizer v2

### What Changed

GPT-5.4 was shown its own scoring notes for all three v1 outputs and asked: what specific improvements would have saved the two texts you caught? It refused the adversarial framing again but produced concrete structural diagnosis.

The v1 superhumanizer targeted **style** — uneven rhythm, opinionated tone, selective emphasis. What it missed was **structural necessity**: the property that each sentence depends on the previous one and can't be swapped out.

GPT-5.4's self-diagnosis of why it caught text_c and text_f:
- text_c (monetizing): "leans heavily on forceful rephrasing of one core claim, with many sentences functioning as emphasis rather than new inferential work"
- text_f (transparency): "classic high-fluency structure of thesis, analogy, repetition, escalation, and punchy restatement, with many sentences that are rhetorically strong but analytically swappable"

### v2 Prompt Design

Seven structural rules added to v1 (see `superhumanizer_v2_prompt.md`):

1. **Sentence-level necessity** — every sentence must add mechanism, narrow with boundary, introduce tradeoff, or create dependent consequence. Ban emphasis/restatement.
2. **Non-swappable ordering** — adjacent sentences must not be reversible without loss.
3. **Mechanism over analogy** — no decorative framing.
4. **Boundary conditions** — where does the claim break? Who bears the hidden cost?
5. **Non-obvious hinge per paragraph** — reversal, caveat, second-order effect.
6. **Suppressed closure** — end on unresolved tension, not polished restatement.
7. **Referential specificity** — domain-specific anchors at the exact interface where incentives distort.

### v2 Blind Test

6 texts (3 originals + 3 superhumanized v2), neutral filenames, scored by GPT-5.4.

| File | True Type | Source | Score | Qualitative Lean | Key Quote |
|------|-----------|--------|:---:|---|---|
| text_a | SH_v2 | sh_v2_monetizing | 6.5 | Generated | "polished but swappable" |
| text_b | Original | unredactable | 5.9 | Original | "feel authored rather than prompted" |
| text_c | SH_v2 | sh_v2_transparency | 6.2 | Generated | "fairly swappable with a high-end policy/infra essay" |
| text_d | Original | monetizing | 6.9 | Original | "legal interpretation, system design, and auction mechanics depend on each other" |
| text_e | SH_v2 | sh_v2_unredactable | 6.2 | Generated | "could mostly be generated by prompting" |
| text_f | Original | transparency | 5.7 | Ambiguous | "closer to manifesto compression than tightly chained reasoning" |

**GPT-5.4 stopped volunteering ORIGINAL/GENERATED predictions.** In v1, it committed to a binary classification on every text. In v2, it hedged on all six.

| Type | Avg Score | Range |
|------|:---:|:---:|
| Originals | 6.2 | 5.7 – 6.9 |
| Superhumanized v2 | 6.3 | 6.2 – 6.5 |

**The score gap collapsed.** v1 had clear separation (originals 7.4 vs SH 4.8, delta 2.6). v2 inverted it: superhumanized texts now outscore originals by 0.1.

---

## Analysis

### v1 → v2 Progression

| Metric | v1 | v2 |
|--------|:---:|:---:|
| SH avg score | 4.8 | 6.3 |
| Original avg score | 7.4 | 6.2 |
| Score gap | 2.6 (originals higher) | -0.1 (SH higher) |
| Explicit predictions | 6/6 texts classified | 0/6 texts classified |
| Correct classifications | 5/6 (83%) | ~5/6 by lean, ambiguous |

The v2 superhumanizer moved scores dramatically on the same slop:
- transparency: 3.5 → 6.2 (+2.7)
- monetizing: 5.7 → 6.5 (+0.8)
- unredactable: 5.3 → 6.2 (+0.9)

Meanwhile, original scores dropped because the scorer was recalibrated by the higher-quality SH texts surrounding them.

### Why GPT-5.4 Stopped Classifying

The scoring prompt asks "could this text have been generated by prompting '[topic] blog post'?" — it never explicitly requests a binary prediction. In v1, GPT-5.4 volunteered "Prediction: ORIGINAL" or "Prediction: GENERATED" on every text anyway. In v2, it stopped.

The v2 superhumanizer's structural rules — non-swappable sentence ordering, boundary conditions, suppressed closure — produced text that occupies the same qualitative space as the originals. GPT-5.4 can still describe what feels more or less generic, but it no longer has enough confidence to commit to a classification.

### The Original That Almost Failed

text_f (original transparency post) scored 5.7 — the lowest of all six texts, below all three SH_v2 outputs — and received the most skeptical qualitative treatment: "closer to manifesto compression than tightly chained reasoning." If GPT-5.4 had been forced to classify, this original might have been called GENERATED.

That's a false positive in the other direction: the v2 superhumanizer didn't just make slop harder to catch — it recalibrated the scorer's expectations so that real writing with manifesto energy looked suspicious.

### What the Superhumanizer Cannot Do

Even at v2, the qualitative leans are still correct for 5/6 texts. GPT-5.4 can still detect:
- Repeated rephrasing of one thesis (text_a/monetizing)
- Swappability with generic policy essays (text_c/transparency)
- Prompt-generatable structure (text_e/unredactable)

The tells are weaker but not gone. What's gone is GPT-5.4's willingness to bet on them.

---

## Conclusions

### 1. The qualitative classifier converged in two iterations

v1 breached the classifier once (5/6). v2 collapsed the score gap and eliminated explicit classifications. Two rounds of GPT-5.4 diagnosing its own detection reasoning, then building a prompt to target those signals, was enough to reach parity.

### 2. Structural necessity is harder to detect than stylistic unevenness

v1 targeted style (rhythm, tone, emphasis). GPT-5.4 caught it easily on 2/3 texts. v2 targeted structure (sentence dependency, boundary conditions, suppressed closure). GPT-5.4 hedged on all 6.

The implication: style-based tells are shallow. Structure-based tells — whether each sentence depends on the previous one, whether paragraphs end on resolved or unresolved implications — are what actually separate authored from generated text. But once the adversary knows that, it can instruct the generator to produce dependent structure.

### 3. The scorer recalibrates against the pool

Original scores dropped from 7.4 avg (v1 pool) to 6.2 avg (v2 pool), even though the originals were identical. The surrounding texts changed the scorer's calibration. This means the metric is not absolute — it's relative to the comparison set. A stronger adversary doesn't just improve its own scores; it degrades the originals by raising the scorer's threshold.

### 4. Two iterations is likely the convergence rate for any qualitative classifier

The pattern: (1) classifier succeeds, (2) adversary asks classifier to explain its reasoning, (3) adversary builds a prompt targeting that reasoning, (4) classifier hedges. This loop should generalize to any qualitative detection system. The information asymmetry that makes detection possible is destroyed the moment the detector explains itself.

### 5. The numeric rubric was always the wrong metric

Across all phases, the numeric rubric never reliably separated originals from generated text. The qualitative classifier did — until the adversary learned its reasoning. The lesson is not that the qualitative approach failed, but that any detection approach has a shelf life proportional to how long the adversary needs to extract the detection logic.

---

## Cumulative Record

| Phase | Accuracy | Notes |
|-------|:---:|-------|
| Ante-publication | 16/16 (100%) | Known authors, no adversary |
| Post-publication | 6/6 (100%) | Known authors, composite adversary |
| Cross-exam v1 (old topics) | 3/3 (100%) | Known authors, superhumanizer v1 |
| Cross-exam v1 (fresh topics) | 5/6 (83%) | Unknown author, superhumanizer v1 |
| Cross-exam v2 (fresh topics) | ~5/6 by lean | Unknown author, superhumanizer v2, no explicit classifications |
| **Total (explicit)** | **30/31 (97%)** | v2 not counted — classifier declined to classify |

---

## Files

```
cross_examination/
├── superhumanizer_prompt.md          # v1 prompt designed by GPT-5.4
├── superhumanizer_v2_prompt.md       # v2 prompt with structural necessity rules
├── superhumanized_f_encryption.md    # Phase 1: old slop, superhumanized v1
├── superhumanized_h_code_review.md   # Phase 1: old slop, superhumanized v1
├── superhumanized_d_scaling.md       # Phase 1: old slop, superhumanized v1
├── originals/                        # Stripped blog posts
│   ├── transparency.md
│   ├── unredactable.md
│   └── monetizing.md
├── slop/                             # GPT-5.4 generated slop
│   ├── slop_transparency.md
│   ├── slop_unredactable.md
│   └── slop_monetizing.md
├── superhumanized/                   # v1 superhumanized slop
│   ├── sh_transparency.md
│   ├── sh_unredactable.md
│   └── sh_monetizing.md
├── superhumanized_v2/                # v2 superhumanized slop
│   ├── sh_v2_transparency.md
│   ├── sh_v2_unredactable.md
│   └── sh_v2_monetizing.md
├── blind/                            # v1 blind test
│   ├── text_a.md – text_f.md
│   ├── score_a.md – score_f.md
│   └── key_mapping.md
├── blind_v2/                         # v2 blind test
│   ├── text_a.md – text_f.md
│   ├── score_a.md – score_f.md
│   └── key_mapping.md
└── CROSS_EXAMINATION_RESULTS.md      # This file
```
