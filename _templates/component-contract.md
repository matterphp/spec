---
id: CMP-<COMPONENT>-CONTRACT
title: <Component> Contract
status: draft | proposed | accepted | implemented
last_updated: YYYY-MM-DD
owners:
  - @<handle>
related:
  adrs: []
  rfcs: []
---

# <Component> Contract

## Purpose
What this component provides to framework users.

## Scope
### In scope
- ...

### Out of scope
- ...

## Stability tiers
This contract defines the **Stable API** for this component.

- **Stable**: documented here and subject to SemVer
- **Experimental**: explicitly marked as such (may change in minor versions)
- **Internal**: not listed here (may change at any time)

## Terminology
Reference any global terms from `docs/glossary.md`.

- Canonical Key: see `docs/glossary.md#canonical-key`
- ...

## Public surface area

### Types
List the supported public types. Avoid listing internal concrete implementations unless intended.

- `<TypeOrInterfaceName>`
- `<TypeOrInterfaceName>`

### Construction and access
How users obtain instances (DI container, factories, `new`, etc).

- ...

## Behaviour guarantees

Use normative language:

- MUST
- MUST NOT
- SHOULD
- MAY

### Core rules
- ...
- ...

### Error model
Document what errors can occur and how they surface.

- Errors MAY be represented as:
    - exceptions
    - result objects
    - error values
- The following errors are part of the contract:
    - `<ExceptionOrErrorName>` — when/why
    - `<ExceptionOrErrorName>` — when/why

### Configuration surface
If configurable, specify keys, defaults, and validation rules.

- `<key>`: `<type>` (default: `<value>`)
- `<key>`: `<type>` (default: `<value>`)

### Extensibility points
List supported extension mechanisms.

- `<ExtensionPoint>` MUST ...
- `<ExtensionPoint>` SHOULD ...
- `<ExtensionPoint>` MUST NOT ...

## Compatibility notes
- Adding new public types/methods/config keys is **non-breaking** (minor).
- Removing or changing behaviour/signatures described here is **breaking** (major).
- Anything not documented here is **internal** and has no compatibility guarantees.

## Examples (optional)
Keep examples short and illustrative. Link to a dedicated examples doc if needed.

```php
// example
```
