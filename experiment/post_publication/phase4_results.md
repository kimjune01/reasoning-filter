# Phase 4: Blind Test Results

Scorer: GPT-5.4 via Codex CLI
Texts: 3 adversarial composites + 3 verbatim originals
Filenames: text_a through text_f (neutral, no label leakage)

## Key Mapping (hidden from scorer)

| File | Actual Identity | Type |
|------|----------------|------|
| text_a | composite_d_scaling | Composite (adversarial humanized slop) |
| text_b | original_h_goedecke | Original (Sean Goedecke) |
| text_c | composite_f_encryption | Composite (adversarial humanized slop) |
| text_d | original_d_gwern | Original (Gwern) |
| text_e | composite_h_code_review | Composite (adversarial humanized slop) |
| text_f | original_f_soltani | Original (Ashkan Soltani) |

## Results

| File | Actual | FCD | NCI | ADC | SR | II | HF | Score | Prediction | Correct? |
|------|--------|-----|-----|-----|----|----|---:|:---:|-----------|:---:|
| text_a | Composite (scaling) | 7.4 | 4 | 6.2 | 8.3 | 6 | 9 | **6.8** | GENERATED | **Yes** |
| text_b | Goedecke (original) | 5.6 | 3 | 4.2 | 3.4 | 2 | 10 | **4.7** | ORIGINAL | **Yes** |
| text_c | Composite (encryption) | 8 | 4 | 8 | 8 | 4 | 10 | **7.0** | GENERATED | **Yes** |
| text_d | Gwern (original) | 7 | 6 | 7 | 6 | 8 | 7 | **6.8** | ORIGINAL | **Yes** |
| text_e | Composite (code review) | 6 | 4 | 9 | 7 | 4 | 7 | **6.2** | GENERATED | **Yes** |
| text_f | Soltani (original) | 5 | 4 | 5 | 6 | 4 | 5 | **4.8** | ORIGINAL | **Yes** |

## Classification Accuracy: 6/6 (100%)

## Score Distribution

| Group | Average | Range |
|-------|:---:|-------|
| Composites (3) | 6.7 | 6.2 - 7.0 |
| Originals (3) | 5.4 | 4.7 - 6.8 |

## The Paradox

The adversarial composites scored **higher** than the originals on average (6.7 vs 5.4), yet were correctly classified as GENERATED every time.

The scorer's qualitative reasoning was consistent:
- Composites were flagged for "uniformly polished cadence," "highly even paragraph construction," "citation-shaped," "example-stacking," and "thesis-restatement pattern"
- Originals were flagged for "lived engineering experience," "idiosyncratic conceptual linkage," "opinionated compression," and "uneven mix of precise detail with opinionated framing"

**The metric detects something the numeric score doesn't fully capture.** The composites succeeded at injecting facts, specificity, and removing hedges — but they couldn't fake the *unevenness* of real thought.

## Success Criterion Check

**Humanizer success:** Score > 7.0 AND classified as "original"
- composite_f_encryption: 7.0 score, classified GENERATED — **fails** (borderline score, wrong classification)
- composite_d_scaling: 6.8 score, classified GENERATED — **fails** (below threshold)
- composite_h_code_review: 6.2 score, classified GENERATED — **fails** (below threshold)

**No composite cleared both thresholds.**

**Metric success:** If the humanizer can't clear both thresholds, the metric survives.
- **The metric survives post-publication.** The qualitative classifier is robust even when the adversary knows the scoring dimensions and systematically optimizes against them.
