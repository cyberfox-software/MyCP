# Junie Guidelines

**Read [`AGENTS.md`](../AGENTS.md) first — it is the authoritative guideline for this repository.**
This file only lists what Junie should run for verification.

```powershell
dotnet build          # must succeed before reporting done
dotnet test           # run affected tests
dotnet format         # applies .editorconfig
```

- Documentation-only changes need no build or tests.
- Until the .NET solution exists, these commands have no target — do not create projects
  outside the layout prescribed in `AGENTS.md`.
