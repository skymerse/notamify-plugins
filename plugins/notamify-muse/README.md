# Notamify for Muse Code

Retrieve NOTAM source records, interpretations, affected infrastructure and airport or flight briefings in the Muse Code terminal client.

## Before you connect

Install [Muse Code](https://dev.meta.ai/docs/muse-code) and complete its [model sign-in and billing setup](https://dev.meta.ai/docs/muse-code/auth). You also need a Notamify account with an active Pro subscription or an existing API agreement and sufficient API credits. Muse model charges and Notamify API credits are separate.

## Install the briefing skill

From a new directory, run:

```sh
git clone https://github.com/skymerse/notamify-plugins.git
muse skills install ./notamify-plugins/plugins/notamify-muse/skills/notam-briefing --scope user
```

If you downloaded the [Muse ZIP](https://github.com/skymerse/notamify-plugins/releases/latest/download/notamify-muse-plugin.zip), extract it and pass the extracted `skills/notam-briefing` directory to the same installer.

## Configure and connect Notamify

Merge the following configuration into `~/.config/muse/settings.json` (or `$XDG_CONFIG_HOME/muse/settings.json` when set). Preserve your existing settings and any other entries in `mcpServers`:

```json
{
  "schema_version": 1,
  "mcpServers": {
    "notamify": {
      "type": "streamable-http",
      "url": "https://mcp.notamify.com/mcp",
      "startup_timeout_sec": 30,
      "tool_timeout_sec": 100
    }
  }
}
```

This configuration is also provided in [settings-example.json](settings-example.json). Sign in to Notamify:

```sh
muse mcp login notamify --scope notams:read --scope briefings:write
```

Complete Notamify sign-in in the browser and review the requested permissions. No Notamify API key is needed. For source queries without briefing generation, request only read access:

```sh
muse mcp login notamify --scope notams:read
```

Start a new Muse session after updating settings or permissions. This Notamify sign-in is separate from Muse's model sign-in.

## Try it

> Show EPWA NOTAMs for the next 24 hours. Include the original identifiers, validity periods and interpretations, and state whether the result is complete.

With briefing-generation permission, you can also ask:

> Prepare an airport briefing for EGLL for the next two hours, with the original NOTAM references.

Each new data operation uses your Notamify API credits. One prompt may trigger several operations. Current rates appear during consent, in tool descriptions and in [Account settings](https://notamify.com/account#connections). Briefing status checks and retries of an already accepted flight request are free.

Interpretations and generated briefings are informational. Check original notices, schedules and conditions against current official aviation sources before making operational decisions.

## Manage access

View or revoke the connection in [Notamify Account settings](https://notamify.com/account#connections). Revocation stops further requests; it does not remove information already saved in Muse conversations.

If Muse cannot access its model, check [Meta's authentication and billing instructions](https://dev.meta.ai/docs/muse-code/auth). If a Notamify operation reports insufficient credits or account access, check your Notamify subscription and API credit balance. If generation reports a missing permission, reconnect with both scopes above.

[Notamify connection manual](https://notamify.com/manual/reference/connected-apps) | [Muse MCP documentation](https://meta-models.github.io/muse-code-sdk/next/guides/extend/mcp-servers/) | [Support](mailto:hello@notamify.com)
