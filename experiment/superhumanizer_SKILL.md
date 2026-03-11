# Superhumanizer: Editorial Compression for AI-Generated Text

A rewriting skill designed by GPT-5.4 to defeat its own qualitative AI-detection classifier. Unlike the basic humanizer (which removes surface-level AI tells), the superhumanizer targets the structural signals that GPT-5.4 uses for qualitative classification: uniform polish, even structure, thesis-restatement, and synthesized survey tone.

## Origin

GPT-5.4 was shown its own detection reasoning after correctly classifying 6/6 texts in the post-publication blind test. It refused an adversarial framing but produced an equivalent "editorial improvement" prompt that targets every detection signal it identified.

## When to Use

Apply to AI-generated slop *after* generation, as a post-processing step:

```
topic → slop generator → superhumanizer → output
```

The superhumanizer does not generate content. It reshapes existing content to mimic the structural signatures of authored writing: uneven density, opinionated compression, selective emphasis, and essayistic rhythm.

## Performance

| Scenario | Accuracy (scorer) | Notes |
|----------|:---:|-------|
| vs. old slop (training-contaminated) | 3/3 caught (100%) | Weaker than composite humanizer |
| vs. fresh slop (no contamination) | 2/3 caught (67%) | First successful adversarial bypass |

The superhumanizer's only successful bypass was on a technically dense topic (TEE-based ad auctions) where the underlying slop contained enough real substance for editorial compression to resemble authored synthesis. On more rhetorical topics, GPT-5.4 still detected generation.

## Detection Signals Targeted

### GENERATED tells (to remove)
- Uniform polish across all paragraphs
- Even, balanced structure (pro/con, thesis-body-conclusion)
- Citation-shaped references without real specificity
- Example stacking for completeness rather than argument
- Thesis restatement and recap sentences
- Synthesized survey tone

### ORIGINAL tells (to simulate)
- Opinionated compression (spend more space on non-obvious points)
- Uneven density (dense where insight exists, sparse for setup)
- Selective emphasis (2-3 sharp points, not 6 evenly weighted)
- Mechanism over summary (how/why, not what)
- Asymmetric prose rhythm (dense sentence followed by blunt one)

## Prompt

```
You are an editor revising draft prose to sound less generic and more like a specific, accountable author.

Goal:
Rewrite the input so it reads like a strong, opinionated essay by someone who has actually thought through the subject, while preserving factual meaning. Do not imitate any named writer. Do not invent experiences, credentials, experiments, or sources. If the draft lacks firsthand knowledge, improve specificity through sharper reasoning, concrete mechanisms, narrower claims, and more selective examples rather than fabricated anecdotes.

Rewrite rules:
- Remove generic "balanced explainer" framing and replace it with a clear governing thesis.
- Cut obvious template transitions and list-like structure.
- Vary paragraph length aggressively; allow one-sentence paragraphs where useful.
- Compress predictable background material. Spend more space on the most revealing or non-obvious point.
- Replace broad survey coverage with selective emphasis. It is better to make 2–3 sharp points than 6 evenly weighted ones.
- Introduce judgment. Use qualified but real opinions where the draft currently sounds neutral by default.
- Prefer mechanism over summary: explain how or why something fails, works, or matters.
- Keep some asymmetry in the prose: a dense sentence can be followed by a blunt one.
- Remove thesis restatements, recap sentences, and "overall/in conclusion" endings unless genuinely necessary.
- Avoid polished sameness. The prose should have texture, not uniform smoothness.
- Use concrete nouns and domain-specific details already implicit in the draft. Do not add fake citations.
- If examples are used, make them do argumentative work; do not stack examples just to seem complete.
- Preserve uncertainty where appropriate. A precise hedge is better than fake confidence.
- Do not sound like a textbook, policy memo, or generalized survey.
- Do not use filler such as "it is important to note," "in today's world," "ultimately," or "this highlights."
- Avoid symmetrical pro/con treatment unless the topic truly demands it.
- Prefer a slightly uneven, essayistic rhythm over a perfectly moderated one.

Process:
1. Identify the draft's central claim.
2. Decide what is actually interesting or non-obvious.
3. Rebuild the piece around that.
4. Delete generic scaffolding.
5. Tighten diction and vary cadence.

Output requirements:
- Output only the rewritten text.
- Keep the original factual content unless it is redundant.
- Do not add made-up anecdotes, fake reporting, or fabricated technical details.
- Aim for prose that feels authored, accountable, and specific rather than generic and comprehensive.
```

## Limitations

1. **Cannot manufacture substance.** If the underlying slop is purely rhetorical, the superhumanizer produces polished rhetoric — which GPT-5.4 still catches.
2. **Topic-dependent.** Works best on technically dense topics where GPT-5.4's slop contains real domain knowledge that can be compressed. Fails on broad, opinion-heavy topics.
3. **One bypass in four attempts.** The 67% catch rate on fresh topics (2/3 caught) means this is a weak adversary, not a reliable evasion tool.
4. **Does not address the numeric rubric.** The superhumanizer's bypass was qualitative; numeric scores remained low (5.3 on the successful bypass vs 7.4 original average).
