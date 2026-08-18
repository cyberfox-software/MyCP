---
sessionId: session-260818-174725-1g62
---

# Requirements

### Overview & Goals
Make **English the single project-wide documentation language**. Currently `README.md` mixes a German section (`## Kurzbeschreibung (DE)`) with an English one (`## Summary (EN)`). The German content must be translated/merged into one coherent English description, and the language rule must be recorded in `AGENTS.md` so agents keep it that way.

### Scope
**In Scope**
- Translate `README.md` fully to English and remove the DE/EN split (no `(DE)` / `(EN)` suffixes).
- Add an explicit "documentation language is English" rule to `AGENTS.md` (Coding Conventions + Rules for AI Agents).

**Out of Scope**
- Any code or project scaffolding.
- Changing `.editorconfig`, `CLAUDE.md`, `.github/copilot-instructions.md`, `.junie/guidelines.md` (already English).

### Functional Requirements
- `README.md` contains no German text; content and meaning of the former German section is preserved in English.
- Structure: title, one-paragraph project description, Roadmap table, "For contributors and AI agents", License.
- The roadmap and phase wording stays consistent with `AGENTS.md`.
- `AGENTS.md` states that all documentation, comments, commit messages and identifiers are written in English.
- Files comply with `.editorconfig`: UTF-8, CRLF, final newline (`*.md` keeps trailing whitespace).

# Technical Design

### Current Implementation
- `README.md` (38 lines): `# MyCP`, German tagline line, `## Kurzbeschreibung (DE)` (4 lines of German), `## Summary (EN)`, `## Roadmap` table, `## For contributors and AI agents`, `## License`.
- `AGENTS.md` (202 lines): canonical guidelines; the *Coding Conventions* section currently mentions English only implicitly ("comment sparingly and in English"); no global language rule.
- Pointer files (`CLAUDE.md`, `.github/copilot-instructions.md`, `.junie/guidelines.md`) are already fully English — no changes needed.

### Key Decisions
1. **Merge instead of duplicate.** The German and English sections overlap heavily; keep one English description rather than a translated German section plus a summary.
2. **Record the rule in `AGENTS.md`.** Without a normative rule, future agents may reintroduce German. Added as a one-line convention plus a `Don't` entry.
3. **Keep `README.md` short.** No new sections; structure stays as-is minus the language split.

### Proposed Changes
**`README.md`** (modified)
- Replace the German tagline with: `**MyCP - My (M)CP Service**: an MCP (Model Context Protocol) service built on .NET / C#.`
- Replace `## Kurzbeschreibung (DE)` + `## Summary (EN)` with a single `## Overview` section merging both: orchestrator-only responsibility (MCP interface over JSON-RPC/stdio, tool discovery/registration, parameter mapping, error handling, structured logging), pluggable tools with PowerShell scripts/modules first and .NET modules later, Phase 1 started and monitored from the command line.
- Keep the Roadmap table, contributors/AI-agents section and License section unchanged.

**`AGENTS.md`** (modified)
- *Coding Conventions*: add "All documentation, code comments, commit messages, identifiers and log messages are written in **English**."
- *Rules for AI Agents / Don't*: add "Don't write documentation or comments in any language other than English."

### File Structure
```
.
├── AGENTS.md   # modified: English-only language rule
└── README.md   # modified: fully English, DE/EN split removed
```

### Risks
- Losing nuance from the German text — mitigated by merging both sections rather than dropping one.
- Line-ending drift when rewriting Markdown — verify CRLF and final newline after editing.

# Testing

### Validation Approach
Documentation-only change: verified by reading the resulting files, no build or tests.

### Key Scenarios
- `README.md` contains no German words (`Kurzbeschreibung`, `Dienst`, `eingehängt`) and no `(DE)`/`(EN)` markers.
- All information from the former German section is present in English.
- `AGENTS.md` contains the English-language rule in both the conventions and the do/don't list.

### Edge Cases
- Roadmap phase descriptions remain identical in wording between `README.md` and `AGENTS.md`.
- Both files keep UTF-8 encoding, CRLF line endings and a final newline.

# Delivery Steps

### ✓ Step 1: Translate README.md into a single English overview
`README.md` is fully English with one merged overview section.

- Replace the German tagline under `# MyCP` with an English one-liner.
- Merge `## Kurzbeschreibung (DE)` and `## Summary (EN)` into one `## Overview` section in English, preserving all facts (orchestrator-only scope, MCP interface over stdio, tool registration, parameter mapping, error handling, logging, PowerShell-tools-first, CLI start/monitoring in Phase 1).
- Keep the Roadmap table, "For contributors and AI agents" and "License" sections, ensuring wording matches `AGENTS.md`.
- Verify UTF-8, CRLF and final newline per `.editorconfig`.

### ✓ Step 2: Record the English-only language rule in AGENTS.md
`AGENTS.md` makes English the mandatory documentation language for all agents.

- Add a bullet to *Coding Conventions*: all documentation, comments, commit messages, identifiers and log messages in English.
- Add a matching entry to the *Rules for AI Agents* `Don't` list forbidding non-English documentation/comments.
- Keep the document within its ~150-250 line target and change nothing else.