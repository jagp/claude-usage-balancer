# todo.md

Informal project scratchpad. Keep high-signal.

## Now
- Shape the usage-balancer MVP: a queue for deferred commands, a scheduler that
  runs them against spare usage, and a model-routing policy (route each command to
  the least-capable model that can do it well).

## Later
- Swap the vendored project-scoped dev-strap hooks for the plugin form once
  `feature/plugin-conversion-phase1` merges (global, opt-in via the omnilog marker).
