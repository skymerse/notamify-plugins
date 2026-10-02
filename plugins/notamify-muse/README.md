# Notamify for Muse Code

Install this skills package with `muse skills install /absolute/path/to/notamify-muse/skills/notam-briefing --scope user`. Merge `settings-example.json` into your existing user settings at `~/.config/muse/settings.json`, preserving other settings, then run:

`muse mcp login notamify --scope notams:read --scope briefings:write`

Sign in to your existing Notamify account with API credits and start a new Muse session. This skill installation and OAuth discovery were tested with the public Muse Code 1.4.2 CLI. That build does not expose plugin commands. The archive also includes a native plugin manifest for builds with plugin support. The hosted OAuth connection is in user settings. No tokens or API keys are distributed.

Setup and support: https://mcp.notamify.com/integrations/
