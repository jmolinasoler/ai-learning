---
name: prompt-engineering
description: Apply advanced prompting techniques to improve AI output quality. Use when writing, reviewing, or optimizing prompts — especially for complex reasoning, document analysis, or tasks where accuracy and structure matter.
---

# Prompt Engineering Techniques

Systematic, iterative approach to building prompts that produce accurate, structured, and reliable AI outputs. Based on Anthropic's official prompt engineering workshop.

## How It Works

Apply the technique that matches the task complexity:

1. **Simple tasks** — Direct prompt with role + format instructions
2. **Multi-step reasoning** — Chain-of-Thought (CoT)
3. **Complex/branching problems** — Tree-of-Thoughts (ToT)
4. **Any task** — Always iterate: test → analyze output → refine

## Core Principles

- **Prompt engineering is a skill**: systematic improvement through testing, evaluation, and iteration — not magic
- **Treat the model like a literal colleague**: crystal-clear instructions, explicit context, quality-control mechanisms
- **Most users leave 80% of capability on the table** by using basic prompts

## Iterative Prompt Building (the fundamental loop)

Start minimal, add layers one at a time:

```
v1: State the task
v2: Add role/persona
v3: Add explicit output format
v4: Add reasoning instructions (CoT)
v5: Add safeguards (hallucination prevention)
v6: Test on edge cases → refine
```

## Chain-of-Thought (CoT) Prompting

Force the model to reason step-by-step before answering. Dramatically improves accuracy on non-trivial tasks.

**Zero-Shot CoT** (no examples needed):
```
[Your question here]
Let's think step by step.
```

**Few-Shot CoT** (with examples):
```
Q: Roger has 5 tennis balls. He buys 2 cans of 3 balls each. Total?
A: Roger starts with 5. 2 × 3 = 6 more. Total: 5 + 6 = 11 balls.

Q: [your question]
A: [model reasons step by step]
```

**When to use CoT:** math, logic puzzles, analysis, planning, debugging, any multi-step task.
**Skip for:** simple factual queries (wastes tokens, no benefit).

## Tree-of-Thoughts (ToT) Prompting

Extends CoT by exploring multiple reasoning branches in parallel, evaluating each, and backtracking from dead ends. Use for non-linear, high-uncertainty problems.

**Basic ToT prompt:**
```
Solve using Tree of Thoughts reasoning.

Problem: [question]

Step 1: Generate 3 different first approaches. For each, explain why it might work.
Step 2: Score each approach 1–10 for promise. Explain scoring.
Step 3: Expand the best approach into 2–3 next steps.
Repeat evaluation for 2–3 levels, then give the final solution with full reasoning.
```

**Expert simulation variant** (simple, effective):
```
Imagine three different experts answering this. Each writes 1 step of thinking,
shares it with the group, they discuss and vote on the best next step.
Continue until solved.
```

**CoT vs ToT:**
| | CoT | ToT |
|---|---|---|
| Structure | Linear | Tree (branching) |
| Error handling | One wrong step derails everything | Can backtrack |
| Cost | Low | Higher (more tokens) |
| Best for | Sequential logic | Planning, puzzles, ambiguous problems |

## Hallucination Prevention Toolkit

Apply these in combination:

```
- "Only answer if you are very confident."
- "If you don't know, say 'I don't know' and explain why."
- "First, quote the relevant parts of the source material. Then answer based only on those quotes."
- "Think step by step before answering."
- "At the end, double-check your reasoning and confirm it satisfies all conditions."
```

## Document / Image Analysis Pattern

For extracting structured data from messy real-world documents:

```
You are an expert data extraction agent.

Instructions:
1. Describe what the document/image shows
2. Extract the requested data with high precision
3. Flag any uncertain or ambiguous values as UNCERTAIN: [explanation]
4. Follow this exact output format: [specify format]
5. Ignore irrelevant noise
6. Only include data you can extract with high confidence
```

## Extended Thinking vs. Classic CoT

- **Classic CoT**: explicit step-by-step instructions in the prompt
- **Extended thinking** (Claude-native): allocates extra compute for deeper internal reasoning — best for complex analysis where you want the model to explore broadly before responding

## Present Results to User

When applying these techniques, report:
- Which technique was applied and why
- Key decision points in the reasoning chain
- Any uncertainties flagged during the process

## Troubleshooting

- **Output too verbose**: add "Be concise. Maximum information per sentence."
- **Hallucinating facts**: add the hallucination prevention toolkit above
- **Inconsistent format**: add 1–2 exact output examples in the prompt (few-shot)
- **Wrong reasoning path**: switch from CoT to ToT to explore alternatives
