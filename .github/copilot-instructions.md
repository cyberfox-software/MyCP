# GitHub Copilot Instructions

**Read [`AGENTS.md`](../AGENTS.md) first — it is the authoritative guideline for this repository.**
Everything about architecture, tech stack, folder layout, conventions and agent rules lives there.
This file adds only Copilot-specific hints.

- Mixed repository: **C# / .NET 8** host in `src/`, **PowerShell 7+** tools in `tools/`.
  Suggest code in the language that matches the target folder.
- Formatting and style come from `.editorconfig` — do not propose alternative formatting.
- Never suggest `Console.WriteLine` or `Write-Host`: stdout is the MCP transport.
- New tools = new folder under `tools/` with `tool.json` + entry-point script, kept in sync.
- Keep business logic in PowerShell tools, not in the host.
