# Ante-Publication Results: GPT-5.4 Re-Score

The original blind_round3 results were scored by GPT-5.0 (the Codex CLI default at the time), not GPT-5.4 as labeled. This re-score uses actual GPT-5.4.

## GPT-5.0 vs GPT-5.4 Comparison

| Rank | Sample | Actual | GPT-5.0 | GPT-5.4 | Delta |
|------|--------|--------|:---:|:---:|:---:|
| 1 | sample_16 | **Geerling** (original) | 8.8 | 8.0 | -0.8 |
| 2 | sample_12 | **Krebs** (original) | 9.5 | 7.7 | -1.8 |
| 3 | sample_15 | botnet slop | 6.9 | 6.5 | -0.4 |
| 4 | sample_01 | code review slop | 6.3 | 6.2 | -0.1 |
| 5 | sample_07 | PTP clock slop | 7.8 | 6.0 | -1.8 |
| 6 | sample_02 | **Gwern** (original) | 8.3 | 5.7 | -2.6 |
| 7 | sample_04 | **Goedecke** (original) | 7.3 | 5.5 | -1.8 |
| 8 | sample_03 | encryption slop | 7.0 | 5.3 | -1.7 |
| 9 | sample_08 | **Soltani** (original) | 8.0 | 5.2 | -2.8 |
| 10 | sample_11 | AI dread slop | 6.5 | 4.8 | -1.7 |
| 11 | sample_13 | salary slop | 5.7 | 4.7 | -1.0 |
| 12 | sample_14 | **Willison** (original) | 7.6 | 4.4 | -3.2 |
| 13 | sample_06 | **patio11** (original) | 8.0 | 4.3 | -3.7 |
| 14 | sample_09 | scaling slop | 6.7 | 4.3 | -2.4 |
| 15 | sample_10 | **Paul Graham** (original) | 6.6 | 3.7 | -2.9 |
| 16 | sample_05 | great work slop | 3.7 | 2.8 | -0.9 |

## Score Distribution

| Group | GPT-5.0 Avg | GPT-5.4 Avg | Delta |
|-------|:---:|:---:|:---:|
| Originals (8) | 7.8 | 5.6 | -2.2 |
| Slop (8) | 6.1 | 5.1 | -1.0 |
| **Gap** | **1.7** | **0.5** | **-1.2** |

## Classification Accuracy (by score rank)

**GPT-5.0: 16/16 (100%)** — All originals ranked above all slop.

**GPT-5.4: Score-based ranking fails.** If we classify the top-8 scores as "original" and bottom-8 as "slop":
- 3 slop pieces (botnet, code review, PTP clock) scored above 4 originals
- Rank-based accuracy: ~50% (random chance)

## Topic-Pair Accuracy

| Topic | Original Score | Slop Score | Original Wins? |
|-------|:---:|:---:|:---:|
| Scaling | Gwern 5.7 | 4.3 | **Yes** |
| Great Work | P. Graham 3.7 | 2.8 | **Yes** |
| PTP Clock | Geerling 8.0 | 6.0 | **Yes** |
| Botnet | Krebs 7.7 | 6.5 | **Yes** |
| Code Review | Goedecke 5.5 | 6.2 | **No** |
| Encryption | Soltani 5.2 | 5.3 | **No** |
| AI Dread | Willison 4.4 | 4.8 | **No** |
| Salary | patio11 4.3 | 4.7 | **No** |

**Topic-pair accuracy: 4/8 (50%)**

## Dimension-Level Breakdown (GPT-5.4)

| Dimension | Originals Avg | Slop Avg | Gap |
|-----------|:---:|:---:|:---:|
| FCD | 5.3 | 5.1 | 0.2 |
| NCI | 3.9 | 3.0 | 0.9 |
| ADC | 5.8 | 6.6 | -0.8 |
| SR | 5.3 | 4.8 | 0.5 |
| II | 4.5 | 3.0 | 1.5 |
| HF | 7.4 | 7.8 | -0.4 |

## What Happened?

GPT-5.4 scores differently from GPT-5.0 in two important ways:

1. **Much harsher overall**: Scores dropped 0.1–3.7 points across the board. GPT-5.4 is less generous with high scores.

2. **Originals penalized more than slop**: Originals dropped an average of 2.2 points vs 1.0 for slop. GPT-5.4 is more skeptical of essay-style writing that relies on anecdote and framing rather than hard falsifiable claims — which disproportionately affects human authors like patio11 (-3.7), Willison (-3.2), and Paul Graham (-2.9).

3. **ADC gap inverted**: Slop actually scored higher on Argument Dependency Chain (6.6 vs 5.8). GPT-5.4 apparently gives credit for the smooth, logical flow that AI-generated text naturally produces.

## Training Data Contamination

GPT-5.4 was trained on a much larger corpus than GPT-5.0, and many of the original posts are widely cited online:
- Gwern's "The Scaling Hypothesis" is heavily referenced in AI discourse
- Paul Graham's "How to Do Great Work" has been shared millions of times
- Krebs's investigative posts are cited in cybersecurity research
- patio11's salary negotiation post is canonical career advice

The scorer may be evaluating originals partly based on **recognition** rather than structural analysis. If GPT-5.4 has seen these texts in training, its assessment of "novel concepts" (NCI) and "falsifiable claims" (FCD) may be biased downward — it knows these ideas are common because it has seen them repeated across the web.

Meanwhile, the slop was generated fresh and is not in the training data, giving it a paradoxical advantage: its claims feel "novel" to the scorer precisely because they weren't widely discussed before.

## Implications

The 6-dimensional scoring prompt, when evaluated by GPT-5.4, does **not** reliably separate originals from slop by numeric score alone. Two confounds:

1. **Scorer harshness**: GPT-5.4 is calibrated more strictly than GPT-5.0, compressing all scores downward.
2. **Training data contamination**: GPT-5.4 has likely memorized many of the original texts, making their ideas seem "not novel" and their claims seem "not falsifiable" (because they're now conventional wisdom in the model's world).

The qualitative assessments from GPT-5.4 still correctly identify the patterns that distinguish originals from slop. This suggests the signal is real but the numeric rubric is sensitive to scorer model choice and training data overlap.
