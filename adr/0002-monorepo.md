---
id: ADR-0002
title: Develop every package in one monorepo, split into read-only repositories
status: proposed
created: 2026-11-18
decided:
depends: []
updates: []
obsoletes: []
---

# ADR-0002: Develop every package in one monorepo, split into read-only repositories

## Context

Matter is made of many packages under the `matter` vendor, so a project can install only the ones it needs.
Packagist publishes a package from a repository with its `composer.json` at the root, so each package needs a
repository of its own to be installed on its own.

A change to Matter often spans several packages at once, such as an interface in one and its uses in others. Spread
across separate repositories, that change becomes several commits, pull requests and releases that have to land
together.

When packages are versioned independently, each one has to state which versions of its siblings it works with, and
the combinations to support grow with every release.

Inside a single repository, every package shares one autoloader. A package can use a sibling it never declared and
still work there, then fail when installed on its own.

## Decision

I will keep every Matter package in one repository, each in its own directory under `packages/`. The repository root
is the `matter/framework` package, which replaces every other package, so requiring it installs all of Matter. Each
package is split out to a read-only repository of its own under the `matterphp` GitHub organisation and published
from there, and changes are only ever made in the monorepo. Every package is released together, at one version
number. Each package declares every sibling it uses in its own `composer.json`, and a package that uses a sibling it
hasn't declared fails the monorepo's checks.

## Alternatives

**A repository per package.** Each package would be developed in its own repository, with no monorepo. I rejected
this because the packages will often be developed together, and a change across several of them would have to be
coordinated across as many repositories.

**A single package.** Matter would be one `matter/framework` package, with nothing split out. I rejected this because
there are projects where I want only some of the packages.

**An independent version for each package.** Each package would be released on its own, at its own version. I
rejected this because keeping track of which versions of each package work together would become next to impossible
to manage.

## Consequences

Easier:

- A change across several packages will be one commit and one pull request, with every package tested together.
- A project will be able to install only the packages it needs, or all of Matter through `matter/framework`.
- Each version number will identify one set of packages that are known to work together.
- A package that uses a sibling it hasn't declared will be caught before it is released.

Harder:

- Every package will get a new release whenever Matter does, even if it hasn't changed.
- Contributions will have to go to the monorepo, because the split repositories will not accept them.
- The monorepo will need tooling of its own to merge each package's `composer.json` into the root, split the packages
  out and release them together.

Constrained:

- Every package will need to work when installed on its own, with its `composer.json` declaring every sibling it
  uses.
- A change that needs a new major version in one package will give every package a new major version.
- Every package will live under `packages/`, and none will be developed anywhere else.
