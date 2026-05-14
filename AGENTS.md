# Agents

Practices and conventions for creating and maintaining skills in this repository.

## Skill structure

Each skill lives in its own directory under `skills/`:

```
skills/<name>/SKILL.md
```

- The directory name **must** match the `name` field in the YAML frontmatter.
- Each skill is a single `SKILL.md` file containing frontmatter + markdown instructions.

## Frontmatter

Every `SKILL.md` starts with YAML frontmatter:

```yaml
---
name: <skill-name>
description: <one-paragraph description including trigger phrases>
---
```

- `name` — lowercase identifier, matches the directory name.
- `description` — explains what the skill does and lists trigger phrases (e.g., "Use when the user asks to …").

## Writing style

- **Sentence case for all headings** — capitalise only the first word and proper nouns (e.g., `## What not to do`, not `## What Not To Do`).
- Be direct and imperative — these are instructions for an LLM agent, not documentation for humans.
- Keep sections short and scannable; prefer bullets and tables over paragraphs.

## Skill body guidelines

1. **Opening line** — one sentence summarising the skill's purpose.
2. **Core rules / principles** — numbered or bulleted list of key behaviours.
3. **Workflow** — step-by-step instructions if the skill has a multi-step process.
4. **Reference material** — tables, examples, or lookup data the agent needs.
5. **What not to do** — explicit anti-patterns to avoid.
6. **Exit condition** — describe when the skill should deactivate (e.g., "Return to normal when the user says 'stop'").

## Trigger phrases

Include enough activation phrases in the `description` field that the skill is selected for relevant user requests. Aim for 5–8 diverse phrases covering synonyms and colloquial variants.

## README

When adding a new skill, add a corresponding entry to the root `README.md` under the **Skills** section:

```markdown
- [name](skills/name/SKILL.md) — Short description.
```
