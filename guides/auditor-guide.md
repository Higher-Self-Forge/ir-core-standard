<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Auditor Guide — IR v1.0

This guide supports independent or community auditors in assessing IR v1.0 conformance. It assumes access to an evidence export bundle containing artifacts and logs.

---

## 1. Audit objectives
- Verify governance legitimacy (charter, custodians, decision process)
- Verify consent and boundaries exist and are enforced
- Verify integrity controls (hash-chain continuity, signatures if applicable)
- Verify evidence is exportable and reviewable offline

---

## 2. Evidence bundle contents (recommended)
An implementation SHOULD export a bundle including:
- Constitution manifest(s) + compiled hash notes
- Boundary cards and references
- Consent records + evidence references
- Decision register and meeting minutes
- Full audit log stream(s) with hashing procedure notes
- Audit stream manifest describing stream_ids and heads
- Hash manifest of bundle files (content-addressing recommended)
- Canonicalization method used (see `specification/hash-and-canonicalization.md`)

### 2.1 Key terminology
- **Hash-Chain:** a sequence of audit entries where each `entry_hash` incorporates the prior `prev_hash`, enabling integrity checks and tamper detection.
- **White Room:** an isolated, clean verification environment used to recompute hashes and validate evidence bundles without contamination from the audited system.

---

## 3. Conformance assessment procedure

### Step 1 — Identify claimed conformance level
- Locate the implementer’s conformance statement or report.
- Determine whether the claim is **IR-Conformant** or **IR-Conformant+**.

### Step 2 — Validate schemas
Use a JSON Schema validator (draft 2020-12) to validate:
- `schemas/constitution.schema.json` artifacts
- `schemas/boundary-card.schema.json` artifacts
- `schemas/consent-record.schema.json` artifacts
- `schemas/audit-entry.schema.json` artifacts
- `schemas/graph-node.schema.json` artifacts (if used)

### Step 3 — Governance review
- Confirm Council Charter exists and is adopted (signature evidence).
- Confirm custodians are identified and declarations exist.
- Cross-check Decision Register entries with corresponding audit entries (GOVERNANCE_DECISION).

### Step 4 — Consent review (FPIC)
- Confirm each enabled feature/data category maps to an **active** Consent Record scope.
- Confirm consent triggers in the constitution align to operations:
  - introducing new datasets/features should produce CONSENT_CHANGE or GOVERNANCE_DECISION events
- Review evidence refs (minutes, translations, photos) for completeness and accessibility.

### Step 5 — Boundary review
- Confirm boundary cards exist for high-risk constraints.
- Confirm enforcement mechanisms are documented.
- For IR-Conformant+, require test hooks or policy rules evidence.

### Step 6 — Audit log integrity
- Verify `sequence_number` increments by 1 within each `stream_id`.
- Verify `prev_hash` equals prior `entry_hash` within each stream.
- Recompute `entry_hash` using the documented canonicalization method (see `specification/hash-and-canonicalization.md`).
- For IR-Conformant+:
  - Verify signatures on SECURITY_ALERT and KILL_SWITCH_ACTIVATION entries.

### Step 7 — Kill switch and incident handling
- Confirm kill switch authority is documented in charter.
- Confirm any activation is logged as `KILL_SWITCH_ACTIVATION` with evidence.
- Confirm reinstatement decisions and reviews are recorded.

---

## 4. Sampling and interviews (recommended)
- Sample decisions across the deployment timeline and validate traceability.
- Interview custodians about:
  - offline-first sync procedures
  - incident response steps
  - how consent updates are handled
- Interview community representatives about:
  - accessibility of consent materials
  - perceived benefit and transparency

---

## 5. Reporting
Audit reports SHOULD include:
- Conformance level determination
- Checklist with evidence pointers
- Nonconformities and remediation recommendations
- Any risks requiring urgent attention
