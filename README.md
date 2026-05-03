# AI Learning Knowledge Base

Personal knowledge base about AI, prompt engineering, and building AI-powered systems.

## Owner

Julio Molina — learning and building with AI tools, focused on practical applications for teams.

## What this knowledge base contains

### Prompt Engineering (`wisdom prompting.md`)

Deep notes on advanced prompting techniques for large language models:

- **Chain-of-Thought (CoT)**: Guide models to reason step-by-step before answering. Dramatically improves accuracy on complex tasks. Key trigger phrase: "Let's think step by step."
- **Tree-of-Thoughts (ToT)**: Extension of CoT that explores multiple reasoning branches in parallel, evaluates them, and backtracks when needed. Best for non-linear, planning-heavy problems.
- **Hallucination prevention**: Force the model to quote source material first, answer only when very confident, and explicitly say "I don't know" when unsure.
- **Iterative prompt refinement**: Start simple, add role/context, explicit output format, reasoning instructions, safeguards, then test on edge cases.
- Source: Anthropic's official prompt engineering workshop (free, ~24 min, from Claude's creators).

### Building AI Skills (`Creating skills.md`)

Framework for building reusable, reliable AI capabilities — based on Anthropic engineering talks:

- **Core philosophy**: Don't build monolithic agents. Build small, focused, composable Skills.
- **3 required properties of production Skills**:
  - **Evaluation**: concrete success metrics (accuracy %, format correctness, latency)
  - **Versioning**: each skill has a version (e.g., v1.0 – 2025-10-11) to iterate safely
  - **Composability**: skills chain together (research skill + writing skill + format skill)
- **Evolution mindset**: Day 1 = basic skill → Day 5 = capable → Day 30 = highly reliable
- **Skill Builder template**: included in the file — ready to copy and adapt

### Skill Library (`skills/`)

Ready-to-use prompt templates for specific tasks:

- `basket_news.md` — Markdown Research & Synthesis Agent: crawls, analyzes, and synthesizes information into high-density Markdown reports. Supports Surface/Technical/Investigative depth levels.

## How to use this knowledge

These files are intended to be ingested by Spacebot so the agent can recall:

- Prompting best practices and techniques when helping with AI tasks
- The Skills framework when advising on AI system design
- Ready-made skill prompts when specific capabilities are needed
