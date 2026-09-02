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

<!-- BEGIN HARN SHARED AGENT CONTRACT: managed by harn-bump-fleet -->

## Ecosystem working agreement

- Pursue the ambitious product outcome; make the seams boring with small typed
  interfaces, explicit invariants, and deterministic projections.
- Give each behavior one semantic owner. Generate or parity-test other surfaces
  instead of maintaining competing implementations.
- Work autonomously inside approved scope. Pause for destructive, production,
  high-spend, ambiguous, or authority-expanding actions—not routine reversible work.
- Treat stop, wait, stand down, and pivot as control events for long-lived work.
- Match evidence to the claim: exercise the canonical user path, state the
  falsifier, verify liveness and recovery, and record residual blind spots.
- "Ship" means landed on main with required deploy and post-merge checks complete.

<!-- END HARN SHARED AGENT CONTRACT -->

## Pull request titles

Use `[Area] Sentence case summary`, for example
`[connector] Verify the webhook signature before parsing the payload`. The
summary starts with a capital letter and does not end with a period. See
[CONTRIBUTING.md](CONTRIBUTING.md) for scope rules and the files this
repository does not accept hand edits to.
