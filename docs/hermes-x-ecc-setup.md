# Hermes x ECC Setup

Hermes is the operator shell. ECC is the reusable system behind it.

This is the public, sanitized topology for using Hermes as the front door, ECC as the reusable workflow substrate, and Codex as a coding/build agent exposed to Hermes through MCP.

## Roles

- Hermes: operator shell, CLI, TUI, messaging gateway, cron surface, and orchestration front door.
- ECC: reusable skills, agents, commands, hooks, MCP templates, migration utilities, and launch collateral.
- Codex: repo editing, implementation, tests, commits, build/debug work, and other coding tasks callable from Hermes through MCP.
- Private/local MCPs: host context, provider context, RAG, data, browser, finance, media, and workspace-specific extensions selected by the operator.

ECC is a reusable workflow substrate, not a competing broad behavior plugin for Codex.

## Architecture

```text
Telegram / CLI / TUI
        ->
      Hermes
        ->
 Codex MCP + ECC skills/hooks/MCPs + Solthera/private MCPs
        ->
 GitHub / Drive / browser / research APIs / media / finance tools
```

Public Solthera MCP references are examples of local operator extensions, not ECC public defaults.

## Public Repo Boundary

The public ECC repo can ship:

- reusable skills
- agents
- commands
- hooks
- MCP templates
- migration and audit utilities
- launch collateral

The public repo must not include:

- private secrets
- live tokens
- personal data
- raw `~/.hermes` exports
- private workspace memory

## Public Workspace Map

Use these paths as the reproducible public shape without exporting private state:

- `~/.hermes/config.yaml`: model routing, MCP registrations, plugin settings, and operator preferences.
- `~/.hermes/skills/ecc-imports/`: ECC skills copied or adapted for Hermes-native use.
- `skills/hermes-generated/`: reusable workflow patterns distilled from Hermes sessions.
- `~/.hermes/plugins/`: local Hermes plugins and bridge glue.
- `~/.hermes/cron/jobs.json`: scheduled jobs with explicit prompts, cadence, and delivery channels.
- `~/.hermes/workspace/`: operator artifacts, working notes, reports, and generated outputs.

## Local Auth Stays Local

Configure these per operator and keep them out of the public repo:

- Google OAuth
- distribution credentials
- Stripe keys
- browser credentials
- CRM/project credentials
- health exports

## Bring-Up Order

1. Audit the legacy Hermes workspace.
2. Plan and scaffold migration artifacts.
3. Install ECC.
4. Install Hermes.
5. Register selected MCPs.
6. Authenticate Google, GitHub, and distribution channels.
7. Start with a small cron surface.
8. Add heavier workflows later.

## Notes For Private Operators

Use private MCPs for local host facts, environment selection, CPU policy, safety policy, repo maps, MCP maps, RAG, DuckDB, LanceDB, artifacts, and source/provider tools.

Do not expose broker execution, paper order submission, live trading, raw browser credentials, or broad distribution tools by default. Add those only under an explicit operator approval policy.
