# Matter Specification

This repository contains the specifications for the framework: contracts, design documents,
architecture notes, and decision records (RFCs/ADRs). It is the source of truth for
framework behaviour and public compatibility guarantees.

## What belongs here

- Component **contracts** (public, SemVer-governed)
- Component **design** docs (internal implementation guidance)
- Architecture docs (cross-cutting constraints)
- RFCs (proposals) and ADRs (decisions)

## What does not belong here

- Implementation code
- Benchmark results (unless they affect design decisions)
- Long tutorials (keep examples minimal and contract-driven)

## Repository structure

- `docs/` — meta documents (glossary, compatibility policy, writing conventions)
- `architecture/` — system-level behaviours and constraints
- `components/` — per-component contracts and designs
- `rfcs/` — change proposals
- `adrs/` — accepted decisions
- `_templates/` — document templates

## Document types and their purpose

### Contract

Defines what framework users can depend on. Anything in a contract is part of the
supported public surface and follows SemVer rules.

### Design

Explains how something works internally and why. Design docs may change without being
a breaking change unless the contract changes.

### RFC

A proposal for a new component or a significant change. RFCs become ADRs when accepted.

### ADR

A record of a decision that the rest of the specs and implementation rely on.

## Compatibility / SemVer policy (high-level)

- Breaking changes to any **contract** requirement = **major**
- Backwards-compatible additions to the contract = **minor**
- Internal changes (design-only) = **minor/patch** depending on impact

Full rules: `docs/release-and-compatibility.md`

## Start here

- Overview: `docs/overview.md`
- Principles: `docs/principles.md`
- Glossary: `docs/glossary.md`
- Architecture index: `architecture/README.md`
- Components index: `components/README.md`
