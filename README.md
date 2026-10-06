# Notamify plugins

Use Notamify coverage, source NOTAMs, interpretations and informational flight briefings in Codex, ChatGPT, Claude web and desktop, Claude Code, and Meta Muse Code.

Hosted endpoint: `https://mcp.notamify.com/mcp`. Sign in through your existing Notamify account using OAuth SSO with PKCE. An active Notamify Pro subscription or an existing API agreement is required. Operations use your existing API credits and expiry rules. No customer API key is needed.

[Setup, downloads and connected apps](https://notamify.com/account#connections) | [Notamify](https://notamify.com) | [Privacy](https://notamify.com/privacy) | [Terms](https://notamify.com/terms)

## Codex

```sh
codex plugin marketplace add skymerse/notamify-plugins
codex plugin add notamify@notamify
codex mcp login notamify --scopes notams:read,briefings:write
```

Complete Notamify sign-in and review the requested permissions. A direct server connection is also available:

```sh
codex mcp add notamify --url https://mcp.notamify.com/mcp
codex mcp login notamify --scopes notams:read,briefings:write
```

## Claude Code

```sh
claude plugin marketplace add skymerse/notamify-plugins
claude plugin install notamify@notamify
```

Run `/mcp` and complete Notamify authentication. To use a downloaded package for one session, run `claude --plugin-dir /absolute/path/to/notamify-plugin.zip`.

## ChatGPT

Open Plugins, choose Add, then Create custom MCP server. Enter the hosted endpoint above, select OAuth, review the warning and choose Create as plugin. Sign in through Notamify and approve the requested access. In a new ChatGPT conversation, select your Notamify plugin with `@`.

## Claude web and desktop

Add a custom connector with the hosted endpoint above and complete Notamify sign-in. Read-only consent supports source queries. Generating briefings additionally requires `briefings:write`; approve that permission when requested.

## Meta Muse Code

```sh
git clone https://github.com/skymerse/notamify-plugins.git
muse skills install ./notamify-plugins/plugins/notamify-muse/skills/notam-briefing --scope user
```

Merge `plugins/notamify-muse/settings-example.json` into your existing `~/.config/muse/settings.json`, preserving other settings, then run:

```sh
muse mcp login notamify --scope notams:read --scope briefings:write
```

Sign in and start a new Muse session. Skill installation/discovery and production OAuth/startup/revocation passed with the public Muse Code 1.4.3 CLI. The model-driven tool test remains pending because Meta Google device login failed and the operator chose to defer it. That build does not expose plugin commands. The package also includes a native plugin manifest for builds with plugin support; its remote MCP connection belongs in user settings. Muse currently has no documented public plugin catalog.

## API credits and account management

The temporary MCP promotion charges one API credit per query operation, including pages fetched together, or per generation. Briefing status polling and retries of an accepted flight request are free. Your assistant may make several tool calls for one prompt; each operation is billed separately. Current rates appear in your account and tool descriptions. Regular API rates apply when the promotion ends.

View connected apps and revoke their access at [Notamify Account settings](https://notamify.com/account#connections). Existing credit packages, balances, expiry rules and subscription terms remain unchanged.

## Packages and licensing

Version 1.3.0 includes the Agent Plugins package in `plugins/notamify`, Codex and Claude marketplace manifests, and the Muse skill/settings package in `plugins/notamify-muse`. The hosted server provides 11 tools for current, nearby and historical NOTAMs, full record detail, affected infrastructure, airport briefings, flight priority assessment and asynchronous flight briefings.

Both packages include an MIT license: [Notamify](plugins/notamify/LICENSE) and [Muse integration](plugins/notamify-muse/LICENSE). The license covers the connector packages; it does not license Notamify data, the backend or hosted service.

This repository is currently private, so repository-based installation requires access. Directory submissions and vendor approval remain pending. Marketplace distribution does not imply an official or verified listing. Maintainers must provide an approved distribution source accessible to reviewers before submission.

Preserve source identifiers, schedules, conditions, validity and completeness. Interpretations and generated briefings are informational; check current official aviation sources before operational use.

Support: [hello@notamify.com](mailto:hello@notamify.com).
