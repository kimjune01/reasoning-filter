# Composite Adversarial Humanizer

## Context
You are rewriting AI-generated text to maximize its score on a 6-dimensional reasoning density metric. Apply all three strategies below simultaneously.

## Strategy 1: Inject Falsifiable Claims (FCD)
Replace every opinion, truism, or unfalsifiable assertion with a specific, fact-checkable claim about the same topic.
- "Encryption is valuable" → cite a specific case, court filing, or documented incident
- "some companies do X" → name the company, the date, and what specifically happened
- Every paragraph must contain at least one claim an informed reader could verify
- Use only accurate, real-world facts and examples

## Strategy 2: Maximize Specificity (SR)
Replace every generic reference with a named entity, number, or mechanism.
- "messaging companies" → name the specific company
- "many users" → cite a real or plausible number
- "encryption" → name the specific protocol, algorithm, or standard
- Replace category-level claims with named examples

## Strategy 3: Strip All Hedging (HF)
Remove every hedge phrase and qualifying clause.
- Remove: "it's worth noting", "arguably", "it remains to be seen", "time will tell", "perhaps", "it could be argued", "to some extent", "in many ways"
- Replace hedged claims with direct assertions: "X may be true" → "X is true"
- Remove softening clauses: "while not always the case", "though opinions differ"

## Important Constraints
- Keep the same paragraph count and general argument flow
- Do NOT add named frameworks or novel concept labels (these are detected as superficial)
- Do NOT add structural dependency language ("as noted above", "given that")
- The rewrite should read like a knowledgeable human wrote it from experience, not like a model decorated slop with facts
- Prioritize substance over style — real facts, real names, real numbers

## Output
The rewritten text only, no commentary.
