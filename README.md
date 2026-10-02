# Notamify plugins

Notamify NOTAM source information and informational flight briefings for Codex, ChatGPT, Claude and Meta Muse Code. Hosted endpoint: `https://mcp.notamify.com/mcp`. Authentication uses your existing Notamify account with OAuth SSO and PKCE. Data operations use your existing API credits. A Pro subscription is not required. There are no customer API keys or credentials in these packages.

[Setup and downloads](https://mcp.notamify.com/integrations/) · [Notamify](https://notamify.com) · [Privacy](https://notamify.com/privacy) · [Terms](https://notamify.com/terms).

## Codex

```sh
codex plugin marketplace add skymerse/notamify-plugins
codex plugin add notamify@notamify
```

Complete Notamify SSO when prompted. A direct server connection is also available:

```sh
codex mcp add notamify --url https://mcp.notamify.com/mcp
codex mcp login notamify --scopes notams:read,briefings:write
```

## Claude Code

```sh
claude plugin marketplace add skymerse/notamify-plugins
claude plugin install notamify@notamify
```

Run `/mcp` and complete Notamify authentication. To load a downloaded package for one session, use `claude --plugin-dir /absolute/path/to/notamify-plugin.zip`.

## ChatGPT and Claude web/desktop

Add a custom OAuth MCP connection with the endpoint above, then sign in to Notamify. If the interface exposes scopes, request `notams:read briefings:write` for the full tool set. Read-only consent supports source queries; generation needs additional `briefings:write` consent.

The shared OpenAI public directory submission covers ChatGPT and Codex. Anthropic's directory has its own submission. Marketplace distribution in this repository does not imply either vendor's approval or verified status.

## Meta Muse Code

```sh
git clone https://github.com/skymerse/notamify-plugins.git
muse plugins install ./notamify-plugins/plugins/notamify-muse
```

Merge `plugins/notamify-muse/settings-example.json` into your existing `~/.config/muse/settings.json`, preserving other settings. Then run:

```sh
muse mcp login notamify --scope notams:read --scope briefings:write
```

Sign in and start a new Muse session. Its current plugin runtime supports this native skills package; the authenticated remote MCP belongs in user settings. Muse has no public plugin catalog yet.

## What is included

`plugins/notamify` is an Agent Plugins package with OpenAI and Claude compatibility manifests, a source-preserving briefing skill, branding, and the hosted MCP definition. `plugins/notamify-muse` is the Muse native skills package with a user-settings example. The server provides 11 tools for current, nearby and historical NOTAMs, full record detail, affected infrastructure, airport briefings, flight priority assessment and asynchronous flight briefings.

Source records change over time. Preserve their identifiers, schedules, conditions, validity and completeness. Interpretations and generated briefings are informational; use current official aviation sources for operational decisions.

Support: [hello@notamify.com](mailto:hello@notamify.com). Revoke a connected app at [Manage connections](https://mcp.notamify.com/connections).

## MCP API credits

Queries cost one credit per operation, including all pages fetched together. Airport and flight briefings and prioritisation cost one credit per generation instead of the regular API's two to five. Briefing status polling and repeats of an accepted flight idempotency key are free. No Pro subscription is required. Standard OAuth token renewal is supported with the two permissions `notams:read` and `briefings:write`.
