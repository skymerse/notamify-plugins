# Notamify for Muse Code

Use Notamify NOTAMs and flight briefings in Muse Code with your existing Notamify account and API credits.

Install the skill:

```sh
muse skills install /absolute/path/to/notamify-muse/skills/notam-briefing --scope user
```

Merge `settings-example.json` into `~/.config/muse/settings.json`, preserving your other settings. Then connect:

```sh
muse mcp login notamify --scope notams:read --scope briefings:write
```

Sign in and start a new Muse session. Requires Notamify Pro or an existing API agreement. Current API credit rates appear in your account.

[Setup guide](https://notamify.com/manual/reference/connected-apps) | [Manage connections](https://notamify.com/account#connections) | [Support](mailto:hello@notamify.com)
