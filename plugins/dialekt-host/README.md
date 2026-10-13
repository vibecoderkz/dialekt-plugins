# Dialekt Host plugin

Publish what you build with Claude Code or Codex to `https://<name>.dialektai.org`.

1. Create an account at https://host.dialektai.org and confirm your email.
2. In **Tokens** create a token (starts with `dlk_`). It is shown once.
3. Install the plugin and paste the token when asked.

**Claude Code**

(The plugin marketplace is private; the command below works if you have been given access. Otherwise use the single command in the last section or in the Dialekt Host panel.)

```
/plugin marketplace add vibecoderkz/dialekt-plugins
/plugin install dialekt-host
```

Claude Code asks for the token and keeps it in secure storage. Do not paste the token into the chat.

**Codex**

```
codex plugin marketplace add vibecoderkz/dialekt-plugins
```

Then install `dialekt-host` and export the token before starting Codex: `export DIALEKT_HOST_TOKEN=dlk_...`

**Without a plugin** (any MCP client):

```
claude mcp add --transport http dialekt-host https://mcp.dialektai.org/mcp --header "Authorization: Bearer dlk_..."
```

Then ask your agent: "publish this site".

Developed by Dias Zhumagaliyev, https://dias.now. Contact: hello@dias.now.
