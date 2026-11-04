---
'@ex-machina/opencode-anthropic-auth': minor
---

Let another plugin choose the Anthropic login for each request, and report each login's quota. A plugin that sets the `x-opencode-credential-id` request header in `model.request` sends that request on the named connection of the `anthropic` integration; the header never reaches Anthropic, and an id that is not a connection fails the request instead of falling back to another login. Every response's unified rate-limit headers are read into a quota reading per login, served over the `credential-quota.anthropic` RPC (`reading`, `usage`, and a `reading` event) together with why and until when a login is refused (plan limit, rate limit, unauthorized, sign-in needed). Requests now carry Claude Code's per-model beta set and a stable `x-claude-code-session-id` per OpenCode session.
