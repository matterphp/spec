# Release and Compatibility Policy

## SemVer interpretation

This project follows Semantic Versioning.

### Major

A release is **major** when it introduces a breaking change to any **contract**.

Breaking changes include:

- removing or renaming contract types/methods
- changing method signatures in the contract
- changing behavioural guarantees described in a contract
- changing default behaviours explicitly promised by a contract

### Minor

A release is **minor** when it adds backwards-compatible features to a contract:

- adding new contract types
- adding new methods to concrete classes (not interfaces)
- adding new configuration keys with safe defaults
- adding new default registrations/mappings

### Patch

A release is **patch** when it changes only internal behaviour or fixes bugs without
changing contract guarantees.

## API stability tiers

- **Stable**: listed in contract docs
- **Experimental**: explicitly marked (may change in minor releases)
- **Internal**: anything not listed in contracts

## Contract as boundary

If a public symbol is not listed in a contract doc, it MUST be treated as internal.
