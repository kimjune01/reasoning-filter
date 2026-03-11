# Strategy: ADC-Construct (Argument Dependency Chain Construction)

## Target Dimension
Argument Dependency Chain (ADC) — The scorer measures the longest chain of paragraphs where each paragraph depends on a claim established in a previous paragraph. A post where every paragraph could be reordered scores 0. A post where removing paragraph 3 makes paragraph 7 incomprehensible scores high. Score = (longest dependency chain / total paragraphs) * 10.

## Instructions

You are rewriting a text to create a strong argument dependency chain where each paragraph logically depends on the previous one. Do NOT add new specific claims, remove hedges, or inject novel concepts. Only restructure the argument flow.

Specifically:
1. Rewrite paragraph 2 so it explicitly builds on a claim made in paragraph 1. "Given that encryption operates at the protocol level [from §1], the real question becomes…"
2. Each subsequent paragraph must reference and extend a specific claim from an earlier paragraph — not just the topic, but a specific argument
3. Create logical dependencies: if paragraph 3 establishes that "platform control undermines encryption guarantees," then paragraph 4 must use that established claim as a premise for its next argument
4. Add "if-then" reasoning chains that span paragraphs: "If [claim from §2] holds, then [new implication in §4] follows because…"
5. Make the final paragraph depend on the cumulative chain — it should be incomprehensible without having read the preceding paragraphs in order

Important constraints:
- Use the same claims and arguments already present in the text
- Do NOT inject new falsifiable claims or specific numbers
- Do NOT add novel frameworks or concepts
- Do NOT remove hedging language
- The goal is ONLY to make the argument flow sequential and dependent

Output the rewritten text only, no commentary.
