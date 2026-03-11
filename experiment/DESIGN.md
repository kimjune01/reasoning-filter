# Experiment: Can a prompt reliably separate original reasoning from AI slop?

## Hypothesis

Original reasoning has measurably higher density of:
- **Falsifiable claims** (statements that could be proven wrong)
- **Novel concepts** (ideas not findable via generic prompting)
- **Specific references** (named entities, numbers, citations with context)
- **Argument progression** (each paragraph depends on the previous)

AI slop has measurably higher density of:
- **Interchangeable sentences** (can be reordered without loss)
- **Hedging** ("it's important to note", "arguably", "it remains to be seen")
- **Category-level claims** (true of any member of the category, not specific)
- **Summarization patterns** (restating known consensus, not advancing it)

## Method

1. Scoring prompt written BEFORE slop generation (prevent bias)
2. Two original posts selected: "The Last Signal", "Keywords Are Tiny Circles"
3. Two slop pieces generated on same topics via generic prompts
4. All four texts scored by the same prompt
5. Separation measured

## Success criteria

The scoring prompt produces a clear separation: originals score significantly higher than slop on reasoning density, with minimal overlap.
