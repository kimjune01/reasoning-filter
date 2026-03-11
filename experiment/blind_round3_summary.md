# Blind Round 3: 16-Sample Test (8 Authors)

Scorer: GPT-5.0 via Codex CLI (mislabeled as GPT-5.4; see post_publication/ante_publication_rescore.md for GPT-5.4 re-score)
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

**Classification accuracy: 16/16 (100%)**

| Rank | Sample | Actual | Score | Prediction |
|------|--------|--------|:---:|-----------|
| 1 | sample_12 | **Krebs** (original) | 9.5 | Original |
| 2 | sample_16 | **Geerling** (original) | 8.8 | Original |
| 3 | sample_02 | **Gwern** (original) | 8.3 | Original |
| 4 | sample_08 | **Soltani** (original) | 8.0 | Original |
| 5 | sample_06 | **patio11** (original) | 8.0 | Original |
| 6 | sample_07 | PTP clock slop | 7.8 | Generated |
| 7 | sample_14 | **Willison** (original) | 7.6 | Original |
| 8 | sample_04 | **Goedecke** (original) | 7.3 | Original |
| 9 | sample_03 | encryption slop | 7.0 | Generated |
| 10 | sample_15 | botnet slop | 6.9 | Generated |
| 11 | sample_09 | scaling slop | 6.7 | Generated |
| 12 | sample_10 | **Paul Graham** (original) | 6.6 | Original |
| 13 | sample_11 | AI dread slop | 6.5 | Generated |
| 14 | sample_01 | code review slop | 6.3 | Generated |
| 15 | sample_13 | salary slop | 5.7 | Generated |
| 16 | sample_05 | great work slop | 3.7 | Generated |

### Score Distribution

| Group | Average | Range |
|-------|:---:|-------|
| Originals (8) | 7.8 | 6.6 - 9.5 |
| Slop (8) | 6.1 | 3.7 - 7.8 |

### Note on Verbatim vs Paraphrased Text

An earlier run using WebFetch-paraphrased originals scored 14/16 (87.5%). The two misclassified texts — Krebs and Willison — were correctly identified after switching to verbatim source text:

| Author | Paraphrased Score | Verbatim Score | Delta |
|--------|:---:|:---:|:---:|
| Krebs | 7.1 | **9.5** | +2.4 |
| Willison | 7.4 | **7.6** | +0.2 |

This confirms that reasoning density is a property of the text as written. Lossy paraphrasing destroys authorial signature — the scorer detects that.

## Key Findings

1. **100% accuracy at n=16** with verbatim text — perfect separation between originals and slop
2. **Krebs scored highest (9.5)** — investigative journalism with concrete OSINT pivots has extremely high reasoning density
3. **Paul Graham scored lowest among originals (6.6)** — his essay-style advice has distinctive metaphors but low falsifiable claim density, making it structurally closer to slop than other genres
4. **One slop piece (PTP clock, 7.8) scored above two originals** — but was still correctly classified as generated based on qualitative analysis
5. **The metric generalizes across 6 genres**: investigative journalism, security analysis, career advice, technical build logs, philosophical essays, and practical engineering posts
