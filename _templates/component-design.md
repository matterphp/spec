---
id: CMP-<COMPONENT>-DESIGN
title: <Component> Design
status: draft | proposed | accepted | implemented
last_updated: YYYY-MM-DD
owners:
  - @<handle>
related:
  contract: CMP-<COMPONENT>-CONTRACT
  adrs: [ ]
  rfcs: [ ]
---

# <Component> Design

## Purpose

Explain the internal goals and why the component exists.

## Relationship to contract

This document describes internal design only.

- Public guarantees are defined in: `./contract.md`
- This document MUST NOT introduce new public guarantees.

## High-level architecture

- Major responsibilities
- Boundaries (what it must not depend on)
- Collaboration with other components

## Runtime model

- Construction (when/how created)
- Scope (application vs request vs transient)
- Lifecycle notes (boot/shutdown if relevant)

## Internal model

Describe key internal types and responsibilities.

- `<InternalType>` — role
- `<InternalType>` — role

## Control flow

Step-by-step description of how the component operates.

### Happy path

1. ...
2. ...

### Edge cases

- ...
- ...

## Algorithms and data structures

Only include what matters to maintainers.

- ...
- ...

## Caching and performance

- hot paths
- expected complexity
- caching strategy
- constraints

## Security considerations

- untrusted input
- parsing
- filesystem/network
- denial-of-service concerns

## Trade-offs and rationale

- why this design
- what was deliberately not chosen

## Open questions

- [ ] ...
