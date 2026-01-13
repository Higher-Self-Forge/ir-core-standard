<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Qori Labs — Laboratorio de Tecnología de Interés Público

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Contributing

Thanks for helping improve the **IR v1.0 Core Standard**. This repository is a public, normative standard intended to be implementable by third parties and legible to communities.

## Ways to contribute
- **Report issues**: unclear language, missing definitions, schema ambiguities, or implementation pitfalls.
- **Propose changes**: open an issue with a concrete proposal and rationale.
- **Submit pull requests**: targeted fixes, additional examples, clarifications, or new templates/guidance.
- **Interoperability feedback**: share test vectors, validation cases, and conformance evidence patterns.

## Normative vs informative changes
- **Normative** changes affect conformance, schemas, or MUST/SHOULD requirements.
- **Informative** changes clarify text, add examples, or improve readability.

If your proposal affects conformance:
1. Update relevant schema(s) in `schemas/`
2. Update the conformance checklist in `specification/conformance/checklist.md`
3. Add an entry to `CHANGELOG.md`
4. Include migration notes in your PR description

## Pull request workflow
1. Fork the repository.
2. Create a topic branch: `feat/<name>` or `fix/<name>`.
3. Make changes with clear commits.
4. Ensure:
   - JSON is valid (schemas validate under draft 2020-12)
   - Examples are realistic and consistent with the spec
   - Links are relative when pointing within the repo
5. Open a PR describing:
   - **What** changed
   - **Why** it changed
   - Conformance impact (if any)
   - Backwards compatibility notes

## Design principles for IR artifacts
- **Community sovereignty first**: governance and consent are first-class artifacts.
- **Offline-first operation**: artifacts must be serializable, portable, and sync-friendly.
- **Auditability**: events that matter should be attestable (hashes/proofs) and exportable.
- **Interoperability**: follow established patterns (e.g., W3C VC-style proofs) where helpful.

## Licensing and attribution
By contributing, you agree that your contributions are licensed under the repository license: **CC BY-NC-SA 4.0**.

## Security and responsible disclosure
If you find a security vulnerability in a reference implementation or deployment guidance, do **not** open a public issue. Instead, contact Qori Labs via the organization channels referenced in `README.md`.
