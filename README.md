# MyCP

**MyCP - My (M)CP Service**: an MCP (Model Context Protocol) service built on .NET / C#.

## Overview

MyCP is an **orchestrator only**: the service exposes the MCP interface over JSON-RPC/stdio,
discovers and registers tools, maps MCP arguments to tool parameters, handles errors and writes
structured logs. The actual capabilities are provided by **pluggable MCP tools** — **PowerShell
scripts/modules** first, .NET modules later. In Phase 1 the host is started and monitored from the
command line.

## Roadmap

| Phase | Content |
|-------|---------|
| 1 | Console host, started and monitored from the command line; MCP over stdio; structured logging; PowerShell tools |
| 2 | The same host wrapped as a **Windows Service** |
| 3 | Additional **.NET tool modules** |

## For contributors and AI agents

All architecture decisions, the prescribed repository layout, coding conventions and the
PowerShell tool contract are documented in **[AGENTS.md](AGENTS.md)** — the single source of truth.
GitHub Copilot (`.github/copilot-instructions.md`), Claude (`CLAUDE.md`) and JetBrains Junie
(`.junie/guidelines.md`) all point to that file. Code formatting and style are governed by
`.editorconfig`.

## License

See [LICENSE](LICENSE).
