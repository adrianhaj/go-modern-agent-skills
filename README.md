# Go Modern Agent Skills

Basic cross-client repository for reusable agent skills focused on modern Go development.

Author: `adrianhaj`  
Version: `1.0.0`

## Overview

This repository follows the portable skill layout used by repositories such as [`samber/cc-skills-golang`](https://github.com/samber/cc-skills-golang):

- each skill lives in `skills/<skill-name>/SKILL.md`
- each skill uses simple YAML frontmatter
- repository-level metadata stays in the README

For the first skill, the source was `/Users/adrian/.claude/skills/review-go-modern/SKILL.md`.

## Repository Layout

```text
.
├── README.md
├── .gitignore
└── skills/
    └── review-go-modern/
        └── SKILL.md
```

## Skill Metadata

For portability across agents, the skill frontmatter is intentionally limited to:

- `name`
- `description`

Best-practice note: while fields such as `author` or `version` can be useful for humans, they are not part of the common minimal format used by the reference repository. To avoid relying on client-specific parsing, this repository keeps those values at repository level instead of embedding them into every skill.

## Installation And Use

### Claude Code

Clone into a discoverable skills path:

```bash
git clone https://github.com/<your-account>/go-modern-agent-skills.git ~/.claude/skills/go-modern-agent-skills
```

Then reference or invoke the skill by name when reviewing Go changes:

```text
Use the review-go-modern skill to review this diff.
```

### Codex

Clone into a discoverable skills path:

```bash
git clone https://github.com/<your-account>/go-modern-agent-skills.git ~/.agents/skills/go-modern-agent-skills
```

Codex-compatible tools commonly discover skills from `~/.agents/skills/` or workspace `.agents/skills/`.

### Cursor

```bash
git clone https://github.com/<your-account>/go-modern-agent-skills.git ~/.cursor/skills/go-modern-agent-skills
```

### Gemini CLI

If your setup supports extension-style skill repositories:

```bash
gemini extensions install https://github.com/<your-account>/go-modern-agent-skills
```

If not, clone it into your local skills directory used by your Gemini workflow.

### OpenCode

```bash
git clone https://github.com/<your-account>/go-modern-agent-skills.git ~/.agents/skills/go-modern-agent-skills
```

OpenCode commonly discovers skills from `.agents/skills/`, `.opencode/skills/`, and `.claude/skills/`.

### Copilot And Other Agents

Many agent tools can consume the same repository shape when cloned into their local skills directory. The portable assumption is:

1. clone the repository into the tool's configured skills folder
2. keep skills under `skills/<name>/SKILL.md`
3. reference the skill by its `name` frontmatter

## Skills

### `review-go-modern`

Reviews Go code for:

- correctness and safety
- concurrency issues
- performance risks
- modern Go 1.25-1.26 idioms

Path: `skills/review-go-modern/SKILL.md`

## Adding More Skills

To add new skills, follow the same pattern:

1. create `skills/<skill-name>/SKILL.md`
2. include `name` and `description` frontmatter
3. keep the content procedural and specific
4. add the new skill to this README catalog

## License

This repository uses the existing project license in `LICENSE`.
