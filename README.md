# AI Learning — Agent Skills

Personal collection of AI Skills: reusable, versioned, and composable prompt-based capabilities for prompt engineering, AI system design, and research synthesis.

## Skills

| Skill | Triggers when… |
|-------|----------------|
| [prompt-engineering](skills/prompt-engineering/SKILL.md) | Writing, reviewing, or optimizing prompts; tasks requiring CoT/ToT reasoning or hallucination prevention |
| [build-ai-skills](skills/build-ai-skills/SKILL.md) | Designing AI workflows, building reusable AI capabilities, architecting AI systems |
| [basket-news](skills/basket-news/SKILL.md) | Researching a topic, synthesizing news, or producing a structured knowledge document |

## Repository Structure

```
AGENTS.md                        ← guidance for AI agents working with this repo
README.md                        ← this file
LICENSE                          ← MIT
skills/
  prompt-engineering/
    SKILL.md                     ← CoT, ToT, hallucination prevention, iterative refinement
  build-ai-skills/
    SKILL.md                     ← Skills philosophy, 3 required properties, builder template
  basket-news/
    SKILL.md                     ← Research & synthesis agent for Markdown reports
```

## Installation

**Spacebot** — drop the `skills/` folder into your agent's ingest directory:
```bash
cp -r skills/* ~/.spacebot/agents/main/workspace/ingest/
```

**Claude Code** — copy skills to your Claude skills directory:
```bash
cp -r skills/* ~/.claude/skills/
```

**claude.ai** — paste the relevant `SKILL.md` content into your project knowledge.

## License

MIT — see [LICENSE](LICENSE).

## Author

Julio Molina — learning and building with AI tools.
