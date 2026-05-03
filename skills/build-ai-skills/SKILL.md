---
name: build-ai-skills
description: Design and build reusable AI Skills — focused, versioned, and composable prompt-based capabilities. Use when architecting AI systems, creating repeatable AI workflows, or when someone asks how to build reliable AI capabilities.
---

# Build AI Skills — Not Agents

Framework for building small, focused, composable AI capabilities. Based on Anthropic engineering talks (Barry Zhang & Mahesh Murag, AI Engineer Code Summit).

## Core Philosophy

**Don't build monolithic agents. Build Skills.**

- An **agent** is a large, complex system trying to do everything
- A **Skill** is a small, ultra-specific, reliable, improvable capability

Skills are more stable, easier to maintain, and scale better. Agents use Skills as tools — they're complementary, not competing.

## 3 Required Properties of a Production Skill

### 1. Evaluation
Concrete, measurable success criteria — defined before you ship:
- Accuracy: ≥ X%
- Format correctness: yes/no
- Latency: < X seconds
- Known failure cases: documented list

### 2. Versioning
Each Skill has a version so you can iterate safely without breaking dependents:
- Format: `v1.0 – YYYY-MM-DD`
- Every meaningful change = new version
- Keep a changelog

### 3. Composability
Skills chain together. Design each Skill to receive clean input and produce clean output:
- Research Skill → Writing Skill → Format Skill
- Define input/output contracts explicitly

## Evolution Mindset

```
Day 1:  Almost no Skills → model is "intelligent"
Day 5:  A few Skills     → model is "capable"
Day 30: Many Skills      → model is "extremely useful and reliable"
```

Start basic. Test. Improve. Combine. Never try to build the perfect Skill on day 1.

## Skill Builder Template

Copy and adapt:

```markdown
**Skill Name**: [Clear, specific name — e.g., "Swedish Accident Report Analyzer v2"]

**Objective** (one sentence):
What it does exactly and what the ideal output looks like.

**Version**: v1.0 – [date]

---

## Base Prompt

You are an expert [ultra-specific role] with 15 years of experience.
Your only mission is [objective in one sentence].

Instructions:
- Think step by step (Chain-of-Thought) before responding
- First, quote the relevant parts of the input
- Only answer with information you can extract or reason with high confidence
- If something is uncertain, say "UNCERTAINTY: [explanation]"
- Always use this exact output format:

[JSON or structured Markdown format]

Example input → output: [1–2 good examples]

---

## Evaluation Criteria

- Accuracy: ≥ 95%
- Exact format: yes/no
- Execution time: < X seconds
- Known failures: [list cases that failed and why]

## Version Log

- v1.0 – [date]: Initial version

## Composability

This Skill can be combined with: [list other Skills]
```

## How to Build a Skill (5-step loop)

1. Identify a repetitive task you do with any AI
2. Write a base prompt using the template above
3. Test on 3–5 real cases, including edge cases
4. Refine the prompt:
   - Add more examples (few-shot)
   - Add anti-hallucination rules
   - Add output verification step
   - Switch to ToT if the problem is branching
5. Add evaluation criteria + version tag → save to your Skill library

## Skill Library Structure

Maintain a folder per Skill:

```
skills/
  {skill-name}/
    SKILL.md          # prompt + metadata (this format)
    test-cases/       # inputs + expected outputs
    CHANGELOG.md      # version history
```

Every time you use the Skill:
- Log the result
- If it fails → create v1.X with the fix
- If it works very well → share it or compose it with another Skill

## Present Results to User

When advising on Skill design, always address:
1. Is the objective specific enough? (too broad = bad Skill)
2. What are the evaluation criteria?
3. Which existing Skills could this compose with?
4. What version are we on and what's planned for the next?

## Troubleshooting

- **Skill too broad**: split into two smaller Skills with one job each
- **Inconsistent output**: tighten the output format + add 2–3 examples
- **Hard to evaluate**: define binary metrics (format correct: yes/no) before subjective ones
- **Breaks when combined**: check input/output contract — add explicit schema definitions
