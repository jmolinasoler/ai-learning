# AI Learning — Agent Skills

Personal collection of AI Skills: reusable, versioned, and composable prompt-based capabilities.

## Skills

| Skill | Description |
|-------|-------------|
| [prompt-engineering](skills/prompt-engineering/SKILL.md) | CoT, ToT, hallucination prevention, iterative prompt refinement |
| [build-ai-skills](skills/build-ai-skills/SKILL.md) | Framework for building focused, versioned, composable AI capabilities |
| [basket-news](skills/basket-news/SKILL.md) | Research & synthesize information into high-density Markdown reports |

## Installation

**Spacebot** — drop the `skills/` folder contents into your agent's ingest directory:
```bash
cp -r skills/* ~/.spacebot/agents/main/workspace/ingest/
```

**Claude Code** — copy skills to your Claude skills directory:
```bash
cp -r skills/* ~/.claude/skills/
```

**claude.ai** — paste the relevant `SKILL.md` content into your project knowledge.

## Owner

Julio Molina — learning and building with AI tools.
