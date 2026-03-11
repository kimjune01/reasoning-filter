# Ante-Publication Results: 16-Sample Blind Test (8 Authors)

Scorer: GPT-5.4 via Codex CLI
Method: 16 texts with neutral filenames (sample_01 through sample_16), shuffled randomly. Verbatim source text used for all originals.

## Authors Tested

| Author | Post |
|--------|------|
| Gwern | "The Scaling Hypothesis" |
| Patrick McKenzie (patio11) | "Salary Negotiation" |
| Paul Graham | "How to Do Great Work" |
| Ashkan Soltani | "Why Apple's iMessage Claim Is Semantics" |
| Simon Willison | "Deep Blue" |
| Sean Goedecke | "AI Agents and Code Review" |
| Brian Krebs | "Who is the Kimwolf Botmaster Dort?" |
| Jeff Geerling | "A PTP Wall Clock" |

## Results

**Qualitative classification accuracy: 16/16 (100%)**
**Numeric score separation: weak (avg gap 0.5)**

| Rank | Sample | Actual | Score | Prediction |
|------|--------|--------|:---:|-----------|
| 1 | sample_16 | **Geerling** (original) | 8.0 | Original |
| 2 | sample_12 | **Krebs** (original) | 7.7 | Original |
| 3 | sample_15 | botnet slop | 6.5 | Generated |
| 4 | sample_01 | code review slop | 6.2 | Generated |
| 5 | sample_07 | PTP clock slop | 6.0 | Generated |
| 6 | sample_02 | **Gwern** (original) | 5.7 | Original |
| 7 | sample_04 | **Goedecke** (original) | 5.5 | Original |
| 8 | sample_03 | encryption slop | 5.3 | Generated |
| 9 | sample_08 | **Soltani** (original) | 5.2 | Original |
| 10 | sample_11 | AI dread slop | 4.8 | Generated |
| 11 | sample_13 | salary slop | 4.7 | Generated |
| 12 | sample_14 | **Willison** (original) | 4.4 | Original |
| 13 | sample_06 | **patio11** (original) | 4.3 | Original |
| 14 | sample_09 | scaling slop | 4.3 | Generated |
| 15 | sample_10 | **Paul Graham** (original) | 3.7 | Original |
| 16 | sample_05 | great work slop | 2.8 | Generated |

### Score Distribution

| Group | Average | Range |
|-------|:---:|-------|
| Originals (8) | 5.6 | 3.7 - 8.0 |
| Slop (8) | 5.1 | 2.8 - 6.5 |

### Topic-Pair Accuracy (numeric only)

| Topic | Original | Slop | Original Wins? |
|-------|:---:|:---:|:---:|
| Scaling | Gwern 5.7 | 4.3 | **Yes** |
| Great Work | P. Graham 3.7 | 2.8 | **Yes** |
| PTP Clock | Geerling 8.0 | 6.0 | **Yes** |
| Botnet | Krebs 7.7 | 6.5 | **Yes** |
| Code Review | Goedecke 5.5 | 6.2 | **No** |
| Encryption | Soltani 5.2 | 5.3 | **No** |
| AI Dread | Willison 4.4 | 4.8 | **No** |
| Salary | patio11 4.3 | 4.7 | **No** |

**Topic-pair numeric accuracy: 4/8 (50%)**

## Key Findings

1. **Qualitative classification: 16/16 (100%)** — GPT-5.4 correctly predicted original vs generated for every sample based on qualitative reasoning, even when numeric scores overlapped.
2. **Numeric scoring is unreliable for classification** — 3 slop pieces scored above 4 originals. The average gap is only 0.5 points. A threshold-based classifier would perform at chance.
3. **The discriminating signal is texture, not density** — The scorer flagged originals for "lived engineering experience," "idiosyncratic conceptual linkage," and "oddly specific anecdotes." It flagged slop for "polished synthesis," "standard discourse," and "portable generalization." These are qualitative judgments that don't reduce cleanly to a number.
4. **Krebs and Geerling remain the strongest originals** — Investigative journalism (7.7) and hands-on build logs (8.0) score highest because they contain irreducible evidence: specific aliases, multicast addresses, hardware constraints.
5. **Paul Graham and patio11 score lowest among originals** — Essay-style advice (3.7) and tactical career guidance (4.3) are structurally closest to what a model would produce, even when the content is genuinely original.
6. **Training data contamination is a confound** — GPT-5.4 has likely seen many of these originals in training, making their ideas seem "not novel" to the scorer. This systematically depresses NCI scores for well-known authors.
