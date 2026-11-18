---
id: ADR-0001
title: Use third-party packages only where there is little choice
status: proposed
created: 2026-11-18
decided:
depends: []
updates: []
obsoletes: []
---

# ADR-0001: Use third-party packages only where there is little choice

## Context

Every package listed in a Matter package's `require` is installed in every project that uses it. Its releases,
breaking changes and security fixes become Matter's to follow, and its design choices show through wherever Matter
exposes it.

Some problems are central to what a framework does, such as parsing HTTP messages. Others sit at its edge, where the
work is mostly breadth, such as supporting many storage backends, and an established library already covers them
well.

Development tooling, listed in `require-dev`, is never installed in a project that uses Matter.

## Decision

I will keep third-party packages out of Matter's `require` unless there is not really a choice. Anything central to
what a framework does, Matter implements itself. A third-party package is used only for a problem at the framework's
edge that an established, widely used library already solves, where writing Matter's own would only repeat it. PHP
extensions are outside this rule, as are packages that hold only shared interfaces for integration and
interoperability, such as the PSR interface packages. So are packages in `require-dev`.

## Alternatives

**No third-party packages at all.** Matter would implement everything itself, including filesystem access across
storage backends. I rejected this because some libraries, such as Flysystem, are an industry standard, and rebuilding
one with any parity would take considerable effort and still leave Matter's version lacking.

## Consequences

Easier:

- Projects using Matter will install few packages alongside it, and Matter will have few upstream releases, breaking
  changes and security advisories to follow.
- Everything central to the framework will be Matter's own design, never limited by a library's choices.
- Matter's code will integrate with other code through shared interface packages, without depending on any
  implementation.

Harder:

- Matter will implement and maintain everything central itself, such as HTTP parsing, rather than reuse an existing
  implementation.
- Deciding whether a problem is central or at the edge will be a judgement made for each new dependency.

Constrained:

- Every third-party package in a `require` will need to be for a problem at the framework's edge, solved by an
  established, widely used library.
- Allowing an interface package will not adopt the standard it defines. Adopting one is a separate decision.
