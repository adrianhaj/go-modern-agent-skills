# Go Modern Agent Skills

AI agent skills are reusable instruction sets that extend coding assistants with domain-specific expertise, loaded on demand so they do not bloat context. This repository focuses on production-ready Go skills and review workflows for modern Go codebases.

> [!IMPORTANT]
> Built as a portable skills repository for cross-client use.
>
> The skills in this repo follow current best practices for `SKILL.md` structure, including YAML frontmatter, explicit trigger descriptions, and optional metadata such as author and version.

## How to use

**Install with [skills](https://skills.sh/) CLI** when your agent supports the Agent Skills format:

```bash
npx skills add https://github.com/adrianhaj/go-modern-agent-skills --skill '*'
# or a single skill:
npx skills add https://github.com/adrianhaj/go-modern-agent-skills --skill review-go-modern
```

<!-- prettier-ignore-start -->

<details>
<summary>Claude Code</summary>

```bash
git clone https://github.com/adrianhaj/go-modern-agent-skills.git ~/.claude/skills/go-modern-agent-skills
```

Use the skill by name in a prompt:

```text
Use the review-go-modern skill to review this diff.
```

</details>

<details>
<summary>Codex (OpenAI)</summary>

Clone into the cross-client discovery path:

```bash
git clone https://github.com/adrianhaj/go-modern-agent-skills.git ~/.agents/skills/go-modern-agent-skills
```

Codex auto-discovers skills from `~/.agents/skills/` and `.agents/skills/`.

</details>

<details>
<summary>Cursor</summary>

Copy skills into the cross-client discovery directory:

```bash
git clone https://github.com/adrianhaj/go-modern-agent-skills.git ~/.cursor/skills/go-modern-agent-skills
```

Cursor auto-discovers skills from `.agents/skills/` and `.cursor/skills/`.

</details>

<details>
<summary>Gemini CLI</summary>

```bash
gemini extensions install https://github.com/adrianhaj/go-modern-agent-skills
```

If your Gemini setup does not use extensions, clone the repository into the local skills directory used by your workflow.

</details>

<details>
<summary>Copilot</summary>

Copy skills into the cross-client discovery directory:

```bash
git clone https://github.com/adrianhaj/go-modern-agent-skills.git ~/.copilot/skills/go-modern-agent-skills
```

Copilot auto-discovers skills from `.copilot/skills/`.

</details>

<details>
<summary>OpenCode</summary>

Copy skills into the cross-client discovery directory:

```bash
git clone https://github.com/adrianhaj/go-modern-agent-skills.git ~/.agents/skills/go-modern-agent-skills
```

OpenCode auto-discovers skills from `.agents/skills/`, `.opencode/skills/`, and `.claude/skills/`.

</details>

<details>
<summary>Other agents</summary>

Most tools that support skill folders can consume this repository layout directly:

```text
skills/
  <skill-name>/
    SKILL.md
```

Each skill uses YAML frontmatter plus Markdown instructions, with optional metadata and linked reference files when needed.

</details>

<!-- prettier-ignore-end -->

## Skills

These skills are designed as focused, reusable units. Keep each skill small, explicit, and composable so multiple skills can coexist in one session.

- `name` and `description` in YAML frontmatter drive skill discovery
- optional metadata can document ownership, versioning, category, tags, and integration details
- extra depth can live in `references/`, `scripts/`, or `assets/` inside each skill directory

| Skill | Status | Description | Metadata |
| --- | --- | --- | --- |
| `review-go-modern` | ✅ | Reviews Go code in production Go 1.25-1.26 services, with emphasis on safety, concurrency, error handling, and modern idioms. | `author`, `version`, `category`, `tags`, `license` |

## Skill structure

Current best practices for repository layout:

```text
.
├── README.md
├── .gitignore
└── skills/
    └── review-go-modern/
        └── SKILL.md
```

Current best practices for skill frontmatter:

```yaml
---
name: skill-name
description: What it does and when to use it.
license: MIT
metadata:
  author: adrianhaj
  version: 1.0.0
  category: category-name
  tags:
    - tag-one
    - tag-two
---
```

## Tuning skill triggers

The `description` field is the main trigger surface, so keep it specific:

- say what the skill does
- say when it should be used
- include recognizable task phrases
- mention relevant languages, file types, or workflows when that improves triggering

If a skill becomes too broad, split it into narrower skills instead of making the description vague.

## Contributing

Recommended guidelines when adding more skills:

- use kebab-case for the folder name and `name`
- keep `SKILL.md` as the required entrypoint file
- add optional metadata when it improves maintainability
- keep the main instructions concise and move deeper material into `references/`
- add new skills to the table above

## License

This repository uses the existing [MIT License](./LICENSE).
