# Notamify for Muse Code

Install this skills package with `muse plugins install /absolute/path/to/notamify-muse`. Merge `settings-example.json` into your existing user settings at `~/.config/muse/settings.json`, preserving other settings, then run:

`muse mcp login notamify --scope notams:read --scope briefings:write`

Sign in to your existing Notamify account with API credits and start a new Muse session. This native package declares only the briefing skill: Muse's current plugin runtime does not support remote MCP servers. The hosted OAuth connection is in user settings. No tokens or API keys are distributed.

Setup and support: https://mcp.notamify.com/integrations/
