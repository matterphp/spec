---
id: ADR-0004
title: Raise the minimum PHP version only in a major release
status: proposed
created: 2026-11-23
decided:
depends: []
updates: []
obsoletes: []
---

# ADR-0004: Raise the minimum PHP version only in a major release

## Context

Matter is designed for modern PHP. Each PHP release adds language features, such as partial function application in
PHP 8.6. Matter's code can use only the features of its minimum PHP version.

The `php` constraint in a package's `composer.json` sets which PHP versions a project using it can run.

Raising the minimum PHP version stops a project still on the old version from upgrading Matter. Under semantic
versioning, that is a break in compatibility.

Development tools, such as code style fixers and code coverage drivers, often support a new PHP version weeks or
months after its release. Until they do, the monorepo's checks cannot run on that version.

## Decision

I will raise Matter's minimum PHP version only in a major release. Before 1.0, it can rise in any release. Matter
supports each newer PHP version once the tools the monorepo's checks depend on support it.

## Alternatives

No alternatives were weighed.

## Consequences

Easier:

- A project will be able to upgrade Matter within a major release without changing its PHP version.
- Before 1.0, Matter will be able to use a new PHP version's features as soon as the tools support it.

Harder:

- Within a major release, Matter's code will be limited to the features of its minimum PHP version.
- The monorepo's checks will need to run on every PHP version Matter supports.

Constrained:

- Raising the minimum PHP version in any package will need a major release of every package, because every package
  is released together, as [ADR-0002](0002-monorepo.md) records.
- A newer PHP version will not count as supported until the tools the monorepo's checks depend on support it.
