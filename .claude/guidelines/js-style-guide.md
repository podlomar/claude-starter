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

## React

Combine related state into a single `useState` call instead of splitting values that change together. This especially applies to async loading state — `data`, `error`, and `isLoading` always transition together and must be modelled as one state object.

```ts
// ✅
const [form, setForm] = useState({ name: "", email: "" });

const [request, setRequest] = useState<
  | { status: "idle" }
  | { status: "loading" }
  | { status: "success"; data: User }
  | { status: "error"; error: string }
>({ status: "idle" });

// ❌
const [name, setName] = useState("");
const [email, setEmail] = useState("");

const [isLoading, setIsLoading] = useState(false);
const [data, setData] = useState<User | null>(null);
const [error, setError] = useState<string | null>(null);
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
