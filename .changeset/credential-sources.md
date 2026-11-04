---
'@ex-machina/opencode-anthropic-auth': minor
---

Take a chosen credential's token from a credential source another plugin registers, when OpenCode's store does not keep that credential. A plugin registers a source for the `anthropic` integration in the process-wide registry at `globalThis[Symbol.for('opencode.credential-sources')]`; a request placed on one of its credentials goes out on the token the source resolves, and this plugin never refreshes that token. A source's failure refuses the credential until the `retryAt` it names, and a 401 tells the source which token was rejected so it can refresh it.
