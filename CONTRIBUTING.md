# Contributing

Thanks for contributing to the framework specifications.

## Ways to contribute

### Fixes and clarifications

Small corrections and clarifications can go straight to PR.

### Proposals (RFCs)

Create an RFC for:

- new components/subsystems
- changes affecting public contracts
- architecture-level changes

### Decisions (ADRs)

ADRs are created when an RFC is accepted, and a decision must be recorded.

## Document structure rules

- Every component must have:
    - `contract.md` (public promises)
    - `design.md` (internal details and rationale)
- Contracts define SemVer boundaries.
- Design docs must not restate contract content except as links.

## Templates

Use the templates in `_templates/`:

- `_templates/component-contract.md`
- `_templates/component-design.md`
- `_templates/rfc.md`
- `_templates/adr.md`

## Naming conventions

- RFCs: `rfcs/0001-short-title.md`
- ADRs: `adrs/0001-short-title.md`
- Components: `components/<component>/contract.md`

## Contract rules (important)

A contract document MUST:

- use normative language: MUST / MUST NOT / SHOULD / MAY
- define behaviour and error surface
- avoid implementation details and algorithms
- list supported public types and extension points

A design document SHOULD:

- describe algorithms, lifecycle, caching, performance notes
- explain trade-offs and alternatives
- link to the contract for guarantees

## Pull request checklist

- [ ] Correct document type (contract vs design vs RFC vs ADR)
- [ ] Uses the correct template / headings
- [ ] Includes links to related RFCs/ADRs/components
- [ ] Contract changes clearly labelled as breaking / non-breaking
- [ ] Updates any relevant indexes (`components/README.md`, etc.)
