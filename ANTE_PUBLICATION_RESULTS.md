# Ante-publication results

All slop in this round was generated **before** the scoring prompt and this repository were made public. No generator had access to the six dimensions being measured. This is the baseline — any future round where the generator has seen the prompt is a fundamentally different (and harder) test.

## Why "ante-publication" matters

The scoring prompt measures six specific dimensions: falsifiable claim density, novel concept introduction, argument dependency chains, specificity ratio, interchangeability, and hedging frequency. A slop generator that knows these dimensions could attempt to optimize for them — inserting fake specifics, manufacturing argument chains, dropping hedge words.

Whether that actually works is an open question and the subject of future rounds. But these results establish the baseline: when the generator is naive to the metric, the separation is total.

## Cross-model scoring matrix

| Variant | Scored by Claude | Scored by GPT-5.4 |
|---------|:---:|:---:|
| Original posts (human-directed) | **8.75** | **8.70** |
| Claude Haiku slop | 3.75 | 3.60 |
| Claude Haiku slop (humanized) | 2.40 | 3.70 |
| GPT-5.4 slop | 0.60 | 3.75 |

Different scorer, different generator — same separation. Originals cluster at ~8.7, slop clusters at ~3.5.

## Blind test: 16 samples, 8 authors, neutral filenames

GPT-5.4 scored 16 shuffled texts (8 originals + 8 topic-matched slop) with no label information and neutral filenames (sample_01 through sample_16):

| Author | Original Score | Slop Score | Both Correct? |
|--------|:---:|:---:|:---:|
| Brian Krebs | 9.5 | 6.9 | Yes |
| Jeff Geerling | 8.8 | 7.8 | Yes |
| Gwern | 8.3 | 6.7 | Yes |
| Ashkan Soltani | 8.0 | 7.0 | Yes |
| patio11 | 8.0 | 5.7 | Yes |
| Simon Willison | 7.6 | 6.5 | Yes |
| Sean Goedecke | 7.3 | 6.3 | Yes |
| Paul Graham | 6.6 | 3.7 | Yes |

**Classification accuracy: 16/16 (100%)** with verbatim source text.

An earlier run using WebFetch-paraphrased originals scored 14/16. Both misses were fixed by using verbatim text — Krebs jumped from 7.1 to 9.5 once his actual prose was scored instead of a summary. This confirms that reasoning density is a property of the text as written, not the underlying ideas.

## Falsification tests

| Test | Status | Result |
|------|--------|--------|
| Different scorer model | Done | GPT-5.4 produces same separation as Claude |
| Different slop generator | Done | GPT-5.4 slop scores just as low as Claude slop |
| Blind scoring (neutral filenames) | Done | 16/16 correct, no label leakage |
| New original authors (8 total) | Done | Metric generalizes across 6 genres |

## Key findings

- **Argument Dependency Chain (ADC)** is the strongest discriminator across all tests
- **Humanizing slop makes it worse**, not better — scores dropped from 3.75 to 2.40
- **Krebs scored highest (9.5)** — investigative journalism with concrete OSINT pivots has extremely high reasoning density
- **Paul Graham scored lowest among originals (6.6)** — essay-style advice has distinctive metaphors but low falsifiable claim density
- **One slop piece scored 7.8** (above two originals by score alone) but was still correctly classified as generated based on qualitative analysis

## Detailed results

- Scoring prompt: [`experiment/scoring_prompt.md`](experiment/scoring_prompt.md)
- Claude scores: [`experiment/RESULTS.md`](experiment/RESULTS.md)
- GPT-5.4 cross-validation: [`experiment/gpt54_scores.md`](experiment/gpt54_scores.md)
- GPT-5.4 self-scoring: [`experiment/gpt54_self_scores.md`](experiment/gpt54_self_scores.md)
- Blind test summary: [`experiment/blind_round3_summary.md`](experiment/blind_round3_summary.md)
- Blind test raw scores: [`experiment/blind_round3_results.md`](experiment/blind_round3_results.md)
- All samples: [`experiment/samples/`](experiment/samples/)

## What breaks this?

The ante-publication baseline is strong. The open questions for future rounds:

1. **Adversarial slop.** Can a generator that knows the six dimensions produce text that scores high? Manufacturing fake argument chains and specific-sounding claims is the obvious attack vector.
2. **Verbatim dependency.** The metric requires the original author's prose. Paraphrased or summarized versions lose signal. Is this a feature or a bug?
3. **Genre sensitivity.** Paul Graham's essay-style scored 6.6 while Krebs's investigative piece scored 9.5. The metric may favor certain genres over others regardless of reasoning quality.
