# Notamify for Muse Code

The hosted Notamify MCP server is available. This MIT-licensed skill/settings package uses your existing Notamify account.

Install this skills package with `muse skills install /absolute/path/to/notamify-muse/skills/notam-briefing --scope user`. Merge `settings-example.json` into your existing user settings at `~/.config/muse/settings.json`, preserving other settings, then run:

`muse mcp login notamify --scope notams:read --scope briefings:write`

Sign in to your existing Notamify Pro account, or an account with an existing API agreement, with API credits and start a new Muse session. MCP uses the existing credit balance with a temporary promotion; current rates are disclosed in your account and tool descriptions, and regular API rates apply when it ends. Skill installation/discovery, Notamify OAuth with both permissions, authenticated MCP startup and revocation were tested against the production server with the public Muse Code 1.4.3 CLI. Its model-driven tool test is pending because Meta's Google device login fails and the operator chose to defer it. That build does not expose plugin commands. The archive also includes a native plugin manifest for builds with plugin support. The hosted OAuth connection is in user settings. No tokens or API keys are distributed.

Setup and support: https://notamify.com/account#connections
