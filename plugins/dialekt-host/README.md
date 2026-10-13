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

Then install `dialekt-host`. The Codex build needs a token (OAuth is not supported there yet): create one at https://host.dialektai.org (Tokens) and export `DIALEKT_HOST_TOKEN=dlk_...` before starting Codex. Do not paste the token into the chat.

**Without a plugin** (any MCP client). Claude Desktop, claude.ai and ChatGPT: add a custom connector with the URL `https://mcp.dialektai.org/mcp` and press Connect. With a token instead of OAuth:

```
claude mcp add --transport http dialekt-host https://mcp.dialektai.org/mcp --header "Authorization: Bearer dlk_..."
```

Then ask your agent: "publish this site".

## What it does and what data it sends

The plugin adds one remote MCP server, `https://mcp.dialektai.org/mcp`, and one skill (`deploy-app`). It runs no local code and starts no local processes.

When you ask your agent to publish, it sends the following to Dialekt Host and nothing else:

- the files of the site you chose to publish (HTML, CSS, JS, images), either inline or as an archive uploaded to a one-time URL;
- the project name and the actions you ask for (create, deploy, stop, resume, delete, status);
- an access token issued after you press **Allow** (OAuth 2.1, one hour, refreshable; revocable in the dashboard).

Dialekt Host stores your email, hashes of tokens and sessions, the published files and an activity log. Everything you publish is public at `https://<name>.dialektai.org`. The plugin does not read your other files, your environment or your conversation; the agent decides what to upload when you ask it to publish. Deleting a project needs a separate permission that you grant on the consent page.

- Privacy Policy: https://host.dialektai.org/en/privacy
- Terms of Service: https://host.dialektai.org/en/terms
- Report a site: https://host.dialektai.org/report
- Support: hello@dias.now

License: proprietary, see [LICENSE](LICENSE).

Developed by Dias Zhumagaliyev, https://dias.now. Contact: hello@dias.now.
