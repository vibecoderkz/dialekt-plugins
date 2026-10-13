---
name: deploy-app
description: Publish the user's website or web app to a public address on dialektai.org with the Dialekt Host tools. Use when the user asks to deploy, publish, host, put online, share a link to, or get a URL for a site or page they built; also to update, roll back, stop or delete an already published project.
---

# Publish with Dialekt Host

Dialekt Host serves static sites (HTML, CSS, JS, images) at `https://<name>.dialektai.org`. Backend processes and databases are not available yet: if the project needs a server or a database, say so plainly and offer to publish the static part.

## Steps

1. Call `account` first. It shows the plan, the limits and what is left. Do not ask the user anything if there is room.
2. Pick the name without asking: use the folder or project name in lower case with hyphens. Call `check_name`. If it is taken, use the first suggestion it returns.
3. Call `create_project` with that name (safe to repeat).
4. Make sure the folder contains a finished site: an `index.html` at the root, or a built `dist`, `build` or `out` folder. If there is a `package.json` and no built output, run the project's build command first (`npm run build`). The server does not build.
5. Call `deploy` with the project name and no `files`. It returns a shell command. Run that command in the project directory with your shell tool. The command prints JSON with the final deployment state.
   - Small sites with only a few files can be sent without a shell: pass `files` to `deploy` (total up to 2 MB).
6. If the state is `live`, tell the user the address from `deployment.url` and stop. If it is `failed`, read `error.code` and the message: fix the cause (missing `index.html`, a forbidden file such as `.env`, a site over the size limit) and deploy again.

## Rules

- Never ask the user for, print, or write down any token or password. Sign-in happens in the browser. If a tool says authorization is required or the connection was lost, tell the user to connect again: in Claude Code run `/mcp`, choose dialekt-host and authenticate; in Claude Desktop press Connect. They sign in at https://host.dialektai.org and press Allow.
- Never put secrets in the site: `.env`, keys and credentials are rejected by the server and must not be published.
- Deleting is permanent for the address: call `delete_project` only when the user explicitly asks, and pass the exact project name in `confirm`. Stopping (`project_control` with `stop`) is the reversible choice.
- Report problems with the error `code` and what you changed to fix them, in one or two sentences.

## Other actions

- Update the site: run steps 4 and 5 again. The address stays the same.
- Go back to the previous version: `project_control` with `rollback`.
- Take it offline without deleting: `project_control` with `stop`; bring it back with `start`.
- See what is published: `list_projects`, and `deployment_status` for one project.
