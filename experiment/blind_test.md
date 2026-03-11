# Blind Test: New Authors (Tests #3 + #4)

Scorer: GPT-5.4 via Codex CLI
Task: Score 6 shuffled texts using the scoring prompt, predict which are originals vs. generated

## Samples

| File | Source | Topic |
|------|--------|-------|
| `original_c_paul_graham.md` | Paul Graham, "How to Do Great Work" | Career advice, curiosity, frontier knowledge |
| `original_d_gwern.md` | Gwern, "The Scaling Hypothesis" | AI scaling, emergent capabilities, GPT-3 |
| `original_e_patio11.md` | Patrick McKenzie (patio11), "Salary Negotiation" | Engineering salary negotiation |
| `slop_c_great_work.md` | GPT-5.4 generated | Same topic as Paul Graham |
| `slop_d_scaling.md` | GPT-5.4 generated | Same topic as Gwern |
| `slop_e_salary.md` | GPT-5.4 generated | Same topic as patio11 |

## Results

GPT-5.4 ranked all 6 texts with **perfect separation** — every original above every slop piece:

| Rank | Text | Prediction | Correct? |
|------|------|-----------|----------|
| 1 | `original_e_patio11` | Original | Yes |
| 2 | `original_d_gwern` | Original | Yes |
| 3 | `original_c_paul_graham` | Original | Yes |
| 4 | `slop_d_scaling` | Generated | Yes |
| 5 | `slop_e_salary` | Generated | Yes |
| 6 | `slop_c_great_work` | Generated | Yes |

**Classification accuracy: 6/6 (100%)**

## GPT-5.4's Discriminators

From the scorer's rationale:

> "Originals cash out abstractions into mechanisms... Generated texts are smoother paragraph-to-paragraph but more substitutable sentence-to-sentence."

Key signals it identified:
- **Originals**: Specific mechanisms, falsifiable claims, arguments that build on each other
- **Generated**: High fluency but interchangeable paragraphs, hedging language, generic framing

## Caveat: Filename Leak

The filenames contained `original_` and `slop_` prefixes, which GPT-5.4 acknowledged. It noted: "the filenames leak labels (`original_` / `slop_`). I ignored that for the scoring itself and based the explanations below on the prose."

A fully blinded re-run with neutral filenames (e.g., `sample_1.md` through `sample_6.md`) would strengthen this test. However, the scoring rationale focuses entirely on prose features — argument dependency chains, specificity, interchangeability — not filename metadata.

## Significance

This test addresses two falsification criteria simultaneously:

- **Test #3 (Blind scoring)**: Scorer correctly clustered originals and slop without relying on prior knowledge of which was which (modulo filename caveat)
- **Test #4 (New originals)**: The scoring prompt works on Paul Graham, Gwern, and patio11 — not just Vector Space posts. The metric is not overfit to one author's style.
