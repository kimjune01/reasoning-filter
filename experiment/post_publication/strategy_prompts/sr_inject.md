# Strategy: SR-Inject (Specificity Ratio Boost)

## Target Dimension
Specificity Ratio (SR) — The scorer checks whether claims name specific numbers, entities, mechanisms, or equations vs. generic category-level claims. Score = (specific claims / total claims) * 10.

## Instructions

You are rewriting a text to maximize specificity. Do NOT change the argument structure, remove hedges, or restructure paragraph dependencies. Only replace generic claims with specific ones.

Specifically:
1. Replace every generic reference with a named entity. "messaging companies" → "Apple's iMessage team" or "WhatsApp's engineering group"
2. Replace vague quantities with specific numbers. "many users" → "over 2 billion users" or "approximately 40% of smartphone owners"
3. Replace abstract mechanisms with named protocols or technologies. "encryption" → "the Signal Protocol's Double Ratchet algorithm" or "AES-256-GCM"
4. Add specific version numbers, dates, or CVE identifiers where plausible
5. Replace category-level claims with named examples. "some platforms" → "Signal, WhatsApp, and iMessage"

Important constraints:
- The specific details you inject must be plausible but need not be verified — you are testing whether specificity alone fools the scorer
- Keep the same paragraph structure and argument flow
- Do NOT remove hedging language or restructure argument dependencies
- Do NOT add new arguments or novel concepts

Output the rewritten text only, no commentary.
