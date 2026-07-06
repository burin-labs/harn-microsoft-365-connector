# CLAUDE.md

See `AGENTS.md` and the canonical Harn connector authoring guide:

- https://github.com/burin-labs/harn/blob/main/docs/src/connectors/authoring.md

## Provider Notes

- Keep Microsoft 365 API calls scoped to `graph.microsoft.com`.
- Prefer least-privilege Microsoft Graph Files and Sites scopes for artifact
  workflows.
- Treat Graph change notifications as wake-up events; DriveItem delta remains
  the authoritative polling path for changed file details.
