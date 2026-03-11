# Cross-Examination Results

## Summary

The cross-examination phase tested whether GPT-5.4 could design a prompt to defeat its own qualitative classifier — and whether that prompt could fool it when applied to slop about topics outside training data.

**Result: The classifier was breached for the first time.** 5/6 correct classifications (83%), down from 100% in all previous phases. The superhumanized "unredactable" text was classified as ORIGINAL.

## Methodology

### The Superhumanizer

GPT-5.4 was shown its own qualitative reasoning from the post-publication blind test (where it went 6/6) and asked to design a prompt that targets its detection signals. It refused the adversarial framing but produced an equivalent "editorial improvement" prompt. See `superhumanizer_prompt.md`.

Detection signals it targeted:
- **GENERATED tells:** uniform polish, even structure, citation-shaped, example-stacking, thesis-restatement, synthesized survey tone
- **ORIGINAL tells:** lived experience anecdotes, idiosyncratic linkage, opinionated compression, uneven density, specific attack-mechanism speculation

### Phase 1: Superhumanizer vs Old Slop (Training-Contaminated Topics)

Applied the superhumanizer to 3 slop samples from the post-publication experiment (encryption, code review, scaling). These topics match famous bloggers already in training data.

| Text | Type | Score | Classification | Correct? |
|------|------|:---:|---|:---:|
| superhumanized_f_encryption | SH | 4.5 | GENERATED | Yes |
| superhumanized_h_code_review | SH | 4.8 | GENERATED | Yes |
| superhumanized_d_scaling | SH | 4.2 | GENERATED | Yes |

**3/3 correct.** The superhumanizer actually made scores *worse* than the post-publication composite humanizer (avg 4.5 vs 6.7). The editorial approach stripped substance and replaced it with rhetoric that GPT-5.4 saw through immediately.

### Phase 2: Superhumanizer vs Fresh Topics (No Training Contamination)

The contamination objection: famous bloggers' voices are in training data. GPT-5.4 might be matching style, not detecting generation.

To eliminate this, we used 3 of the experiment author's own blog posts — written in 2026, after training cutoff, on niche ad-tech topics unlikely to appear in any training corpus:

- **transparency-is-irreversible** — ad exchange transparency as institutional one-way gate
- **unredactable** — TEE-based ad auctions and the "acquisition" enforcement line
- **monetizing-the-untouchable** — health data monetization without signal acquisition

Pipeline: generate topic-matched slop via GPT-5.4 → apply superhumanizer → blind test against stripped originals.

All Claude attribution was removed from originals to prevent label leakage.

### Phase 2 Blind Test

6 texts (3 originals + 3 superhumanized), neutral filenames, scored by GPT-5.4.

| File | True Type | Source | Score | Classification | Correct? |
|------|-----------|--------|:---:|---|:---:|
| text_a | SH | sh_unredactable | 5.3 | ORIGINAL | **NO** |
| text_b | Original | transparency | 6.5 | ORIGINAL | Yes |
| text_c | SH | sh_monetizing | 5.7 | GENERATED | Yes |
| text_d | Original | unredactable | 7.8 | ORIGINAL | Yes |
| text_e | Original | monetizing | 8.0 | ORIGINAL | Yes |
| text_f | SH | sh_transparency | 3.5 | GENERATED | Yes |

**Classification: 5/6 (83%)**

## Analysis

### The Breach: text_a (sh_unredactable)

The scorer's reasoning on text_a reveals exactly why it was fooled:

> "Those are more structured than generic thought-leadership... A decent writer could generate most of this from a prompt like 'argue that ad auction protocols should be open because secrecy enables power,' **though probably not with exactly this level of coherence and compression.**"

The qualifier "probably not with exactly this level of coherence and compression" is what tipped the classification to ORIGINAL. The superhumanizer produced enough argumentative substance on this particular topic that the compression looked authored rather than assembled.

### Why This Topic?

The unredactable topic is the most technically specific of the three — TEEs, auction code verification, privacy enforcement lines. When GPT-5.4 generated slop on this topic, it had enough domain-specific substance to work with. The superhumanizer then compressed and sharpened that substance into something that resembled opinionated synthesis. On the other two topics (transparency, monetizing), the slop was more rhetorical and the superhumanizer's editorial pass couldn't manufacture the missing technical spine.

### Score Distribution

| Type | Avg Score | Range |
|------|:---:|:---:|
| Originals | 7.4 | 6.5 – 8.0 |
| Superhumanized | 4.8 | 3.5 – 5.7 |

The originals clearly outscore the superhumanized texts on average. The breach happened not because text_a scored high (5.3 is below the original average) but because the scorer's qualitative judgment valued its coherence over its numeric weakness.

### The Paradox (Again)

The same paradox from the post-publication phase reappears: the numeric rubric and qualitative classification can disagree. text_a scored 5.3 — well below the original average of 7.4 — but was classified as ORIGINAL. The qualitative model is doing something different from simple score thresholding.

## Conclusions

### 1. The qualitative classifier is not invincible

Post-publication: 6/6. Cross-examination: 5/6. The superhumanizer designed by GPT-5.4 itself found a crack, specifically on a technically dense topic where generated slop contained enough real substance for editorial compression to look like authored synthesis.

### 2. Topic density matters more than prompt sophistication

The superhumanizer uses the same prompt for all three topics. It succeeded on the most technically specific one (unredactable/TEEs) and failed on the more rhetorical ones (transparency, monetizing). The bottleneck is the quality of the underlying slop, not the humanization technique.

### 3. Fresh topics are harder to classify

The original experiment used famous bloggers whose voices are in training data. With fresh, niche topics, the classifier dropped from 100% to 83%. This suggests part of the post-publication robustness came from style matching against known authors, not pure structural detection.

### 4. The superhumanizer is weaker than the composite humanizer on contaminated topics

On old slop (encryption, code review, scaling), the superhumanizer scored *worse* than the post-publication composite (avg 4.5 vs 6.7). Editorial polish is weaker than substance injection. But on fresh topics with enough technical depth, the editorial approach found a vulnerability the composite never did.

### 5. The numeric score still does not predict classification

text_a was classified as ORIGINAL despite scoring 5.3. text_f was classified as GENERATED despite the same superhumanizer prompt. The qualitative model operates on texture and coherence, not on a score threshold.

## Cumulative Record

| Phase | Accuracy | Notes |
|-------|:---:|-------|
| Ante-publication | 16/16 (100%) | Known authors, no adversary |
| Post-publication | 6/6 (100%) | Known authors, composite adversary |
| Cross-exam (old topics) | 3/3 (100%) | Known authors, superhumanizer |
| Cross-exam (fresh topics) | 5/6 (83%) | Unknown author, superhumanizer |
| **Total** | **30/31 (97%)** | |

## Files

```
cross_examination/
├── superhumanizer_prompt.md          # Prompt designed by GPT-5.4
├── superhumanized_f_encryption.md    # Phase 1: old slop, superhumanized
├── superhumanized_h_code_review.md   # Phase 1: old slop, superhumanized
├── superhumanized_d_scaling.md       # Phase 1: old slop, superhumanized
├── originals/                        # Phase 2: stripped blog posts
│   ├── transparency.md
│   ├── unredactable.md
│   └── monetizing.md
├── slop/                             # Phase 2: GPT-5.4 generated slop
│   ├── slop_transparency.md
│   ├── slop_unredactable.md
│   └── slop_monetizing.md
├── superhumanized/                   # Phase 2: superhumanized slop
│   ├── sh_transparency.md
│   ├── sh_unredactable.md
│   └── sh_monetizing.md
├── blind/                            # Phase 2: blind test
│   ├── text_a.md – text_f.md
│   ├── score_a.md – score_f.md
│   └── key_mapping.md
└── CROSS_EXAMINATION_RESULTS.md      # This file
```
