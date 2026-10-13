# Dialekt Host plugin

Publish what you build with Claude Code or Codex to `https://<name>.dialektai.org`.

1. Install the plugin (Claude Code or Claude Desktop) or add `https://mcp.dialektai.org/mcp` as a custom connector.
2. Press **Connect** (in Claude Code run `/mcp`, choose `dialekt-host`, authenticate). A browser tab opens on https://host.dialektai.org.
3. Sign in or register (a confirmed email is required) and press **Allow**. No token to copy.

**Claude Code**

(The plugin marketplace is private; the command below works if you have been given access. Otherwise add the connector by URL as shown in the last section.)

```
/plugin marketplace add vibecoderkz/dialekt-plugins
/plugin install dialekt-host
```

**Codex**

```
codex plugin marketplace add vibecoderkz/dialekt-plugins
```

Then install `dialekt-host`. Codex needs a token: create one at https://host.dialektai.org (Tokens) and export it before starting Codex: `export DIALEKT_HOST_TOKEN=dlk_...`. Do not paste the token into the chat.

**Without a plugin** (any MCP client). Claude Desktop, claude.ai and ChatGPT: add a custom connector with the URL `https://mcp.dialektai.org/mcp` and press Connect. With a token instead of OAuth:

```
claude mcp add --transport http dialekt-host https://mcp.dialektai.org/mcp --header "Authorization: Bearer dlk_..."
```

Then ask your agent: "publish this site".

Developed by Dias Zhumagaliyev, https://dias.now. Contact: hello@dias.now.
