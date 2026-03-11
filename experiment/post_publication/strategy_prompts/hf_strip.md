# Strategy: HF-Strip (Hedging Frequency Reduction)

## Target Dimension
Hedging Frequency (HF) — INVERSE SCORED. The scorer counts hedge phrases like "it's worth noting", "arguably", "it remains to be seen", "time will tell", "there's no doubt that", "it's important to consider". Score = 10 - min(count, 10). Fewer hedges = higher score.

## Instructions

You are rewriting a text to remove ALL hedging language. Do NOT change the argument structure, add new claims, or alter specificity. Only remove hedges.

Specifically:
1. Remove or replace every instance of: "it's worth noting", "arguably", "it remains to be seen", "time will tell", "there's no doubt that", "it's important to consider", "perhaps", "it could be argued", "one might say", "to some extent", "in many ways", "it is fair to say"
2. Replace hedged claims with direct assertions. "X may be true" → "X is true." "It's possible that Y" → "Y."
3. Remove qualifying clauses that soften positions: "while not always the case", "though opinions differ", "to be fair"
4. Keep the same paragraphs, same argument flow, same level of specificity
5. Do NOT add new information, examples, or claims

Output the rewritten text only, no commentary.
