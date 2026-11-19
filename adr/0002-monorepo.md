---
id: ADR-0002
title: Develop Matter's packages in one monorepo and release them together
status: accepted
created: 2026-11-18
decided: 2026-11-19
depends: []
updates: []
obsoletes: []
---

# ADR-0002: Develop Matter's packages in one monorepo and release them together

## Context

A project using Matter may need only part of it, and Composer installs whole packages. Packagist publishes a package
from a repository with its `composer.json` at the root, so a package that can be installed on its own needs a
repository of its own.

A change to Matter often spans several packages at once, such as an interface in one and its uses in others. Spread
across separate repositories, that change becomes several commits, pull requests and releases that have to land
together.

When packages are versioned independently, the combinations of sibling versions each package has to work with grow
with every release.

When packages are installed together, as they are in a monorepo, they share one autoloader. A package can use another
package it never declared, such as a sibling or a library a sibling requires, and still work there, then fail when
installed on its own.

## Decision

I will keep Matter's packages in one monorepo, each in a directory of its own. A `matter/framework` package installs
them together, so a project can require all of Matter at once. Each package that is published is split out to a
repository of its own and published from there: the monorepo is the source of each package's code, and the split
repositories only mirror it. Matter's packages are released together, at one version number. Each package declares
every other package it uses in its own `composer.json`, such as a sibling or a third-party library, and a package
that uses one it has not declared fails automated checks.

## Alternatives

**A repository per package.** Each package would be developed in its own repository, with no monorepo. I rejected
this because the packages will often be developed together, and a change across several of them would have to be
coordinated across as many repositories.

**A single package.** Matter would be one `matter/framework` package, with nothing split out. I rejected this because
there are projects where I want only some of the packages.

**An independent version for each package.** Each package would be released on its own, at its own version. I
rejected this because the combinations of versions to support would grow until they were next to impossible to
manage.

## Consequences

Easier:

- Work across several packages will be one change, in one pull request, with every package tested together.
- A project will be able to install only the packages it needs.
- Each version number will identify one set of packages released and tested together.

Harder:

- Every package will get a new release whenever Matter does, even if it has not changed.
- A contribution made to a split repository will have to be moved to the monorepo before it can be accepted.
- The monorepo will need tooling of its own to keep `matter/framework` in step with the other packages, split the
  packages out and release them together.

Constrained:

- Every package will need to work when installed with only the packages it declares.
- A change that needs a new major version in one package will give every package a new major version.
