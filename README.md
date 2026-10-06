# Notamify plugins

Use Notamify NOTAM coverage, interpretations and flight briefings in Codex, ChatGPT, Claude and Meta Muse Code.

Connect with your existing Notamify account. An active Pro subscription or an existing API agreement is required. Usage is charged to your API credit balance.

[Setup guide](https://notamify.com/manual/reference/connected-apps) | [Manage connections](https://notamify.com/account#connections) | [Downloads](https://github.com/skymerse/notamify-plugins/releases/latest)

## Codex

```sh
codex plugin marketplace add skymerse/notamify-plugins
codex plugin add notamify@notamify
codex mcp login notamify --scopes notams:read,briefings:write
```

## Claude Code

```sh
claude plugin marketplace add skymerse/notamify-plugins
claude plugin install notamify@notamify
```

Run `/mcp` and sign in to Notamify.

## ChatGPT and Claude

Add `https://mcp.notamify.com/mcp` as a remote MCP connector, choose OAuth and sign in to Notamify. Claude users can also connect through the [Notamify directory listing](https://claude.ai/directory/notamify).

## Meta Muse Code

```sh
git clone https://github.com/skymerse/notamify-plugins.git
muse skills install ./notamify-plugins/plugins/notamify-muse/skills/notam-briefing --scope user
```

Merge `plugins/notamify-muse/settings-example.json` into `~/.config/muse/settings.json`, preserving your other settings. Then connect and start a new Muse session:

```sh
muse mcp login notamify --scope notams:read --scope briefings:write
```

## Usage

The temporary MCP promotion charges one API credit per query operation, including pages fetched together, or per generation. Status checks and retries of accepted flight requests are free. One prompt may trigger multiple operations. Current rates appear in your [account](https://notamify.com/account#connections).

Manage connections and revoke access in [Account settings](https://notamify.com/account#connections).

Interpretations and generated briefings are informational. Verify operational decisions against current official aviation sources.

## License and support

Connector packages are licensed under MIT: [Notamify](plugins/notamify/LICENSE) and [Muse integration](plugins/notamify-muse/LICENSE). Notamify data and the hosted service are covered by the [Terms](https://notamify.com/terms) and [Privacy policy](https://notamify.com/privacy).

Contact [hello@notamify.com](mailto:hello@notamify.com).
