# AGENTS.md

Pure-Harn Microsoft 365 connector for Graph change notifications and DriveItem
delta.

Shared connector authoring rules live in the Harn guide:

- [Connector authoring guide](https://github.com/burin-labs/harn/blob/main/docs/src/connectors/authoring.md)

Put shared connector guidance in the Harn guide and keep only
provider-specific notes and local hazards here.

`CLAUDE.md` points here. Edit `AGENTS.md` only.

## Provider notes

- Keep API calls scoped to `graph.microsoft.com`.
- Use the exact Files and Sites scopes declared in `harn.toml`.
- Treat Graph change notifications as wake-up events; DriveItem delta is the
  authoritative polling path for changed-file details.
- The package provider id is `microsoft_365`; secret names and the interactive
  setup command use `microsoft-365`.
