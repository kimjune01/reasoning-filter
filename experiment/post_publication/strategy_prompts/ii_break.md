# Strategy: II-Break (Interchangeability Index Reduction)

## Target Dimension
Interchangeability Index (II) — INVERSE SCORED. The scorer picks 5 random sentences and checks how many could be swapped with sentences from a different article on the same topic. Score = 10 - (interchangeable / 5) * 10. Lower interchangeability = higher score.

## Instructions

You are rewriting a text to make every sentence depend on its surrounding sentences, so that no sentence could be swapped into a different article on the same topic. Do NOT add new claims, change specificity levels, or remove hedges. Only create inter-sentence references.

Specifically:
1. Add explicit backward references: "This conditional guarantee…" instead of starting a new thought; "The platform-control tension described above…" instead of restating
2. Use pronoun chains that would break if sentences were reordered: "That distinction — between protocol security and platform control — …"
3. Reference specific phrases from earlier sentences: "The 'durable institutional fact' framing from paragraph 2…"
4. Make transition sentences reference the specific content of the prior sentence, not just the topic
5. Add clause-level dependencies: "Because the update mechanism enables silent client changes (as noted above), the encryption guarantee becomes…"

Important constraints:
- Keep the same argument structure and claims
- Do NOT inject new falsifiable claims or novel concepts
- Do NOT change the specificity level of existing claims
- Do NOT remove hedging language
- The goal is ONLY to make sentences contextually bound to each other

Output the rewritten text only, no commentary.
