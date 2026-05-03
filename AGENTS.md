# AGENTS.md

This file provides guidance to AI agents (Claude Code, Spacebot, Cursor, etc.) working with this repository.

## Repository Overview

A personal collection of AI Skills — reusable, versioned, and composable prompt-based capabilities focused on prompt engineering, AI system design, and research synthesis.

## Skill Directory

| Skill | Trigger |
|-------|---------|
| `skills/prompt-engineering` | Writing, reviewing, or optimizing prompts; tasks requiring CoT/ToT reasoning |
| `skills/build-ai-skills` | Designing AI workflows, building reusable AI capabilities, architecting AI systems |
| `skills/basket-news` | Researching a topic, synthesizing news, producing structured knowledge documents |

## Creating a New Skill

### Directory Structure

```
skills/
  {skill-name}/         # kebab-case
    SKILL.md            # Required: skill definition with frontmatter
```

### SKILL.md Format

```markdown
---
name: {skill-name}
description: {One sentence. Include trigger phrases so the agent knows when to activate.}
---

# {Skill Title}

{Brief description}

## How It Works
{Numbered workflow}

## Usage
{When to trigger, parameters}

## Output Format
{Example output}

## Present Results to User
{How to format the response}

## Troubleshooting
{Common issues and fixes}
```

### Best Practices

- **Keep SKILL.md under 500 lines** — move reference material to separate files if needed
- **Write specific descriptions** — the description is what the agent uses to decide when to activate the skill
- **One job per Skill** — if the objective takes two sentences, split it into two Skills
- **Always define evaluation criteria** — what does success look like?
- **Version every meaningful change** — format: `v1.0 – YYYY-MM-DD`
