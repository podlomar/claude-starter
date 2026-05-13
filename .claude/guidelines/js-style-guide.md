# JavaScript Style Guide

Tooling configs: [biome.json](../../templates/biome.json) · [tsconfig.json](../../templates/tsconfig.json)

Rules below are **not** enforced by the linter or compiler and must be followed manually.

## Functions

Always use arrow functions instead of function declarations or expressions.

```ts
// ✅
const getUser = (id: number): User => { ... }

// ❌
function getUser(id: number): User { ... }
const getUser = function(id: number): User { ... }
```

All functions must have an explicit return type annotation.

```ts
// ✅
const getUser = (id: number): User => { ... }

// ❌
const getUser = (id: number) => { ... }
```

No explicit `return undefined` — use a bare `return` or omit it entirely.

```ts
// ✅
const validate = (x: string): void => { if (!x) return; }

// ❌
const validate = (x: string): void => { if (!x) return undefined; }
```

## Async

When calling a function that returns a promise without awaiting it, use `void` to make the intent explicit.

```ts
// ✅
void analytics.track("page_view");

// ❌
analytics.track("page_view");
```

## Boolean expressions

No implicit boolean coercion. Always use explicit comparisons.

```ts
// ✅
if (value !== null && value !== undefined) { ... }
if (list.length > 0) { ... }
if (isActive === true) { ... }

// ❌
if (value) { ... }
if (list.length) { ... }
if (isActive) { ... }
```

## Linting suppressions

Do not disable linting rules without an explanation comment.

```ts
// ✅
// biome-ignore lint/suspicious/noExplicitAny: third-party callback has no type definition
const handler = (data: any) => { ... }

// ❌
// biome-ignore lint/suspicious/noExplicitAny
const handler = (data: any) => { ... }
```

Use `@ts-expect-error` instead of `@ts-ignore`, always with an explanation.

```ts
// ✅
// @ts-expect-error: missing type in outdated library definition
foo.bar();

// ❌
// @ts-ignore
foo.bar();
```
