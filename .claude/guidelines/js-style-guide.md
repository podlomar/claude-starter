# JavaScript Style Guide

## Functions

Use arrow functions instead of the `function` keyword.

```ts
// ✅
const greet = (name: string): string => `Hello, ${name}`;

// ❌
function greet(name: string): string {
  return `Hello, ${name}`;
}
```

All functions must have an explicit return type annotation.

```ts
// ✅
const getUser = (id: number): User => { ... }

// ❌
const getUser = (id: number) => { ... }
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
