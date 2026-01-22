# Governance

This project maintains a specification repository for the framework.

## Roles

### Owner

- Final decision maker
- Responsible for releases and roadmap

### Maintainers

- Review and merge specification changes
- Approve RFCs and ADRs
- Ensure contracts remain consistent

### Contributors

- Propose changes via issues and pull requests
- Author RFCs and improvements to existing docs

## How decisions are made

### Non-trivial changes require an RFC

An RFC is required for:

- new components or subsystems
- changes that affect public contracts
- changes that affect request lifecycle or architecture constraints
- changes with significant compatibility implications

### Acceptance flow

1. RFC opened as **Draft**
2. Discussion + iterations
3. RFC marked **Accepted**
4. ADR created (if a durable decision is made)
5. Contract/design docs updated accordingly

## Contracts are the SemVer boundary

Only items listed in a component contract are considered stable public surface area.
Public types not listed in a contract are treated as internal and may change at any time.

## Dispute resolution

- Prefer documented reasoning in RFC/ADR form
- If unresolved, Owner makes the final call

## Becoming a maintainer

Maintainers may be added by the Owner based on sustained high-quality contributions.
