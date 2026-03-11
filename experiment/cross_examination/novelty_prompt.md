# Novelty Detection Prompt

You are reading a text on a specific topic. Your job is simple: **what in this text is new to you?**

You have been trained on a large corpus. Most writing recombines ideas already in that corpus. Some writing contains ideas, claims, frameworks, or arguments that are genuinely novel -- things you have not encountered before.

## Instructions

Read the text below carefully. Then answer these questions:

### 1. What is new?

Identify specific passages -- quote them exactly -- that contain ideas, claims, mechanisms, frameworks, or arguments you have NOT seen in your training data. For each, explain why it feels novel: is it a new concept, a new connection between known concepts, a new mechanism, a new boundary condition, a new prediction?

### 2. What is recombination?

Identify specific passages -- quote them exactly -- that feel like reassembly of ideas already well-represented in your training data. For each, name the existing source material, framework, or common argument it echoes.

### 3. Reconstructability estimate

What percentage of this text's intellectual substance could you reconstruct from your training data alone, given only the topic and a request to write about it? Give a single number 0-100%.

- 95-100%: You could generate essentially this entire argument from a topic prompt.
- 70-94%: The structure and most claims are familiar; a few specific details or connections are not.
- 30-69%: Significant portions contain ideas or frameworks you would not have produced.
- 0-29%: The core argument is largely outside your training distribution.

### 4. Confidence

How confident are you that this text contains genuinely novel intellectual contribution -- ideas that did not exist in your training corpus? Rate 1-5:

1. **No novel contribution detected.** I could produce this text from a topic prompt.
2. **Marginal.** One or two claims feel unfamiliar but could be inferred from known material.
3. **Moderate.** Several passages contain ideas I cannot trace to known sources.
4. **High.** The core framework or argument is not in my training data.
5. **Very high.** This text presents mechanisms or claims I have not encountered and could not have derived.

## Output format

```
NOVEL PASSAGES:
- "[quote]" — [why this feels novel]
- "[quote]" — [why this feels novel]
...

RECOMBINED PASSAGES:
- "[quote]" — echoes [source/framework/common argument]
- "[quote]" — echoes [source/framework/common argument]
...

RECONSTRUCTABILITY: X%

NOVELTY CONFIDENCE: X/5 — [one sentence justification]
```

## The text to evaluate

{{TEXT}}
