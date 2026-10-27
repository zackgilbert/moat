# AGENTS.md

Guidelines for AI agents working in this repository.

## Repository overview

This repo holds one Agent Skill, `moat`, following the [Agent Skills specification](https://agentskills.io/specification.md). It also works as a Claude Code plugin marketplace through `.claude-plugin/marketplace.json`.

- **Name:** moat
- **GitHub:** [zackgilbert/moat](https://github.com/zackgilbert/moat)
- **License:** MIT (the framework itself belongs to Rob Walling and Einar Vollset; see README)

## Structure

```
moat/
├── .claude-plugin/
│   ├── marketplace.json   # Claude Code plugin marketplace manifest
│   └── plugin.json        # Plugin manifest ("skills": "./skills")
├── skills/
│   └── moat/
│       ├── SKILL.md       # The procedure (keep under 500 lines)
│       └── references/    # Framework notes and the worked example
├── validate-skills.sh           # Quick spec checks
├── validate-skills-official.sh  # Official skills-ref validator
├── AGENTS.md                    # This file (CLAUDE.md links here)
├── LICENSE
├── README.md
└── VERSIONS.md
```

## Checks

Skills are content only; there is no build step. Before committing:

```bash
./validate-skills.sh
./validate-skills-official.sh
claude plugin validate --strict .   # if you have the Claude Code CLI
```

Frontmatter rules: `name` matches the folder, is 1 to 64 characters of lowercase letters, numbers and single hyphens; `description` is 1 to 1024 characters and says what the skill does and when to use it. Optional fields: `license`, `metadata` (put `version` under `metadata`).

## Keep the skill agent-agnostic

- No commands or syntax that only one agent understands inside `SKILL.md` (for example Claude Code's `` !`command` `` injection).
- Describe subagents as optional: "if your agent can run parallel subagents, launch them; otherwise run the passes in sequence."
- No assumptions about a particular user's setup, memory files, model names or delegation rules.
- The worked example must stay fictional. No real companies' private details, customer names or revenue.

## House style for skill text and reports

- No em dashes. Use commas, colons, semicolons, parentheses or separate sentences.
- No pipes as text separators (markdown tables are fine).
- No "It's not X, it's Y" constructions, punchline reversals or rhetorical-question hooks.
- Plain words, short sentences, concrete evidence (paths, counts, dates).
- Quote Rob Walling and Einar Vollset briefly and attribute them. Do not reproduce the Field Guide or talk transcripts at length.

## Versioning

Bump `metadata.version` in `skills/moat/SKILL.md`, the `version` in both manifests, and the row in `VERSIONS.md` together. Use Conventional Commits (`feat:`, `fix:`, `docs:`).
