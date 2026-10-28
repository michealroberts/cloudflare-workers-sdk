---
"@cloudflare/workers-utils": patch
"wrangler": patch
"@cloudflare/vitest-plugin": patch
---

Detect duplicate `send_email` and `ratelimits` binding names during config validation

Config validation checks that every binding has a unique name, but `send_email` and `ratelimits` bindings were silently skipped because they identify themselves with `name` rather than `binding`. Two `send_email` bindings with the same name, or a `ratelimits` binding sharing a name with another binding such as a KV namespace, now produce the same "Bindings must have unique names" error as every other binding type.
