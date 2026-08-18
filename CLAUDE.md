# CLAUDE.md

**Read [`AGENTS.md`](AGENTS.md) first — it is the authoritative guideline for this repository.**
Do not duplicate or restate its rules here; this file is only a quick entry point.

## Command cheat-sheet (PowerShell, repo root)

```powershell
dotnet restore
dotnet build
dotnet run --project src/MyCP.Host   # start the MCP server on stdio
dotnet test
dotnet format                        # applies .editorconfig
```

Reminders: stdout belongs to the MCP transport (log via `ILogger<T>` to stderr/file);
business logic belongs in the PowerShell tools under `tools/`, not in the host.
