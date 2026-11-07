# REVERSE ENGINEERING REPORT — HL7Norway/hnvitalsigns

## Original repository
- Name: hnvitalsigns
- URL: https://github.com/HL7Norway/hnvitalsigns
- Type: Implementation Guide / FHIR R4 profiles for vital signs (vitalparametre), Helse Nord region (Norway)
- Branch: master
- Base: 7f3496b Har oppdatert profilene etter møte DIPS HN 28/1

## Audit date
2026-11-07

## Tools used
- Git v2.49.0
- PowerShell 5.1
- gh (GitHub CLI), authenticated as admeduardovieira
- Kilo Code (static analysis of XML/JSON/.adl/.oet files)

## Identified architecture
Repository of FHIR R4 definitions for vital signs of Helse Nord (Norway).
Contains StructureDefinitions, ValueSets, Extensions, openEHR archetypes (.adl) and
templates (.oet). Organized by sequential versions (v0.1 to v0.8) + Messaging folder
+ openehr folder. No executable code; clinical/data definitions only.

## Technologies and dependencies
FHIR R4 (4.0.0), openEHR archetypes/templates, simplifier.core.r4, hl7.fhir.no.basis
(dependencies listed in v0.6/package.json and v0.6/fhirpkg.lock.json).

## Maintenance status
- Last commit: 7f3496b (September/October 2023, Norwegian messages)
- 4 Issues (2 open: #3 Composition search, #4 Uttrekk Q/QR; 2 closed)
- 0 PRs in history
- No automated tests, CI, lint or FHIR/SUSHI validation
- Multiple versions (v0.1–v0.8) kept on same branch without tagging

## Investigation limitations
- Not executable code project; no environment to validate FHIR build
- SUSHI/releaselabel does not apply (no sushi-config.yaml in root)
- Second repo of the round (innrapportering-helseregister) could not be cloned
  (network/directory ghost on all paths tested); exists on GitHub API

---

## Problems found (hnvitalsigns)

| ID | Sev | Status | Location | Problem | Fix applied |
|---|---|---|---|---|---|
| REA-001 | P3 | CONFIRMED | Repository root | Missing LICENSE file; use/redistribution rights undetermined | Added LICENSE (CC0 1.0 Universal) |
| REA-002 | P3 | CONFIRMED | README.md | Minimal README (1 line); no usage, build, contribution or version instructions | README expanded with purpose, technologies, versions, license, usage |
| REA-003 | P2 | CONFIRMED | .vs\** | Visual Studio configuration files (.vs\slnx.sqlite, .vs\*.suo, .vs\*.json) versioned | .vs/ added to .gitignore and removed from tracking |
| REA-004 | P2 | CONFIRMED | v0.3 – Kopi\ | Duplicated folder ("Kopi" = copy) of v0.3\ with identical content | Folder v0.3 – Kopi\ removed from tracking and disk |
| REA-005 | P2 | CONFIRMED | v0.1\ a v0.8\ | Eight versions on same branch without tagging/release clear | Not fixed (requires maintainer decision on versioning strategy) |
| REA-006 | P3 | CONFIRMED | Repository root | Versioned .zip binaries (openehr.zip, v0.1.zip, v0.6.zip) | .zip added to .gitignore and removed from tracking and disk |
| REA-007 | P3 | CONFIRMED | Repository | No automated tests, CI or FHIR/SUSHI validation | Not fixed (requires CI decision; no impact on FHIR profiles) |
| REA-008 | P3 | PROBABLE | v0.3\fhirpkg.lock.json, v0.6\fhirpkg.lock.json | Lock files present only in some versions, not consistent | Not fixed |
| REA-009 | P3 | HYPOTHESIS | Various FHIR XML | Many profiles with <status value="draft" />; no indication which are ready | Not fixed (requires clinical domain review) |
| REA-010 | P3 | CONFIRMED | .gitignore | .gitignore covers only macOS/AFP; does not ignore .vs/, *.zip, node_modules/ | .gitignore expanded (.vs/, *.zip, node_modules/, package-lock.json) |

## Recurring problems
- Issues #3 (Composition search, 2020-10-30) and #4 (Uttrekk Q/QR, 2020-12-11) still open; not resolved.
- 0 PRs in history — no record of community corrections.

## Undocumented errors (new from audit)
REA-001 to REA-010 have no visible public record.

## Changes implemented (Phase 2)
1. LICENSE (new): CC0 1.0 Universal.
2. README.md (expanded): purpose, technologies, versions, license, usage, contribution.
3. .gitignore (expanded): ignores .vs/, *.zip, node_modules/, package-lock.json, Thumbs.db.
4. Tracking removal: .vs/ folder (Visual Studio files).
5. Tracking and disk removal: duplicated v0.3 – Kopi\ folder.
6. Tracking and disk removal: openehr.zip, v0.1.zip, v0.6.zip.

## Changes NOT implemented (require maintainer decision or clinical review)
- REA-005: version tags (git tag) instead of v0.x folders on same branch.
- REA-007: CI/automated FHIR validation.
- REA-008: consistent lock files between versions.
- REA-009: draft status review of FHIR profiles (clinical domain).

## Validation performed
- Static check: git status shows correct removals and additions.
- Not executed: FHIR/SUSHI build (not applicable; no environment).

## Remaining risks
- Versioning strategy (v0.x folders vs tags) not resolved.
- Profiles with draft status may not be ready for production.

## Recommendations for future audits
- Define versioning policy (semantic tags).
- Add basic CI for FHIR XML well-formedness validation.
- Review which profiles can leave draft status.
