# Coding Guide

Rules below are **not** enforced by the linter or compiler and must be followed manually.

## Comments

Default to no comments. Only add one when the **why** is non-obvious — a hidden constraint, a workaround for a specific bug, or behaviour that would surprise a reader. Well-named identifiers make the what self-evident; comments explain what they cannot.

```ts
// ✅
// must run before the router mounts or redirects fire before auth is ready
await authStore.init();

// ❌ — restates what the code already says
// initialize the auth store
await authStore.init();
```
