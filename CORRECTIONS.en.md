# CORRECTIONS.md — hnvitalsigns

Base: HL7Norway/hnvitalsigns@7f3496b (master). User authorized implementation of all viable proposals.

## Implemented

1. **`LICENSE`** (new) — CC0 1.0 Universal, consistent with other HL7 Poland IGs already audited.
2. **`README.md`** (expanded) — purpose, technologies, versions, license, usage, contribution.
3. **`.gitignore`** (expanded) — ignores `.vs/`, `*.zip`, `node_modules/`, `package-lock.json`, `Thumbs.db`.
4. **Tracking removal: `.vs/`** — Visual Studio configuration files (`.vs\slnx.sqlite`, `.vs\*.suo`, `.vs\*.json`).
5. **Tracking and disk removal: `v0.3 – Kopi\`** — duplicated folder of `v0.3\`.
6. **Tracking and disk removal: `openehr.zip`, `v0.1.zip`, `v0.6.zip`** — unnecessary versioned binaries.

## Not implemented (maintainer decision / clinical review)
- REA-005: version tags (git tag) instead of v0.x folders on same branch.
- REA-007: CI/automated FHIR validation.
- REA-008: consistent lock files between versions.
- REA-009: draft status review of FHIR profiles (clinical domain).

## Validation
- `git status` confirms correct removals and additions.
- Not executed: FHIR/SUSHI build (not applicable).
