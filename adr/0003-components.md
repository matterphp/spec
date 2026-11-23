---
id: ADR-0003
title: Call Matter's reusable parts components
status: proposed
created: 2026-11-23
decided:
depends: [ADR-0002]
updates: []
obsoletes: []
---

# ADR-0003: Call Matter's reusable parts components

## Context

Matter is made of packages that a project can install separately, as [ADR-0002](0002-monorepo.md) records.

Not every package is a reusable part of Matter. A package can, for example, wrap a third-party library, hold only
interfaces, or connect the parts into a framework. The word "package" covers all of these, and the record has no word
for the reusable parts alone.

## Decision

I will call each reusable part of Matter a [component](../GLOSSARY.md#component), such as routing or HTTP
messages. A component is a package that a project can use on its own. Every component is a package, but not every
package is a component.

## Alternatives

**One word for every package.** The record would call every package a package, with no separate term. I rejected
this because it is important to tell a reusable component apart from a wrapper or any other package.

## Consequences

Easier:

- A document will be able to name Matter's reusable parts in one word, apart from wrappers and other packages.
- A reader will know from the word alone that a component can be used on its own.

Harder:

- Each new package will need a judgement on whether it is a component.

Constrained:

- A package will be called a component only if a project can use it on its own.
- "Package" will still mean any package, components included.
