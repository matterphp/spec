# Glossary

## Canonical Key

A **Canonical Key** is the normalised form used for internal identity across the framework
(lookup keys, registry keys, comparisons).

### Canonicalization algorithm

Implementations MUST:

1. Trim leading/trailing whitespace.
2. Convert to lowercase ASCII.
3. Replace runs of spaces and underscores with `-`.
4. Do not collapse repeated `-`.
5. Trim leading/trailing `-`.

Examples:

- `Content-Type` → `content-type`
- ` content_type ` → `content-type`
- `X  Request__Id` → `x-request--id`

Canonical Keys are used for identity, not presentation.

## Normalised Display Name

A **Normalised Display Name** is a human-friendly representation used when the original
formatting is unavailable.

Example (headers):

- `content-type` → `Content-Type`

Rules are component-specific and defined in the relevant contract.
