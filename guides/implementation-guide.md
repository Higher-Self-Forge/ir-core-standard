<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Implementation Guide — IR v1.0

This guide helps implementers build an IR v1.0 conformant system. It is written to be actionable for engineering teams and governance facilitators.

---

## 1. Prerequisites

### 1.1 Hardware (typical offline-first deployment)
- A local compute node (x86_64 or ARM64) with:
  - 16–64 GB RAM depending on model size
  - Local durable storage (SSD recommended)
  - Optional GPU/NPU if needed for inference
- Local network: Wi-Fi router or mesh node
- Power resilience: UPS or solar + battery where possible
- Secure physical storage for evidence backups (encrypted removable drives)

### 1.2 Software
- A JSON Schema validator supporting draft 2020-12
- A local database/store for artifacts (document store or relational DB)
- A sync mechanism (store-and-forward, opportunistic replication)
- Cryptography support (recommended): Ed25519 or other modern signature suite
- A policy enforcement layer (recommended for IR-Conformant+)

### 1.3 Governance
- Adopted Council Charter (see `templates/governance/Council_Charter_Template.md`)
- Named custodians and signed custodian declarations
- Decision register process
- FPIC consent workflow and materials

---

## 2. Dossier-aligned lifecycle (phase-by-phase)

> The “Dossier” concept here refers to an evidence bundle that supports audit and community review.

### Phase 0 — Initiation & scoping (Dossier: LVA-*)
**Goal:** Define why the system exists and what it will (and will not) do.

Deliverables:
- Draft purpose statement and initial scope
- Consent materials checklist draft (`templates/consent/Consent_Materials_Checklist.md`)
- Initial risk register (informative)

Pitfalls & mitigations:
- **Pitfall:** scope creep from “pilot” to “production” without consent.  
  **Mitigation:** define consent triggers early in the constitution.

### Phase 1 — Governance setup (Dossier: IR-GOV-*)
**Goal:** Establish legitimate decision-making authority.

Steps:
1. Customize and adopt the Council Charter template.
2. Assign custodians and collect signed declarations.
3. Initialize Decision Register and agree on decision ID format.

Evidence pointers:
- Charter PDF/MD, signed declarations, decision register snapshot.

### Phase 2 — Constitution & boundary definition (Dossier: IR-CONST-*, IR-BOUND-*)
**Goal:** Declare enforceable principles, boundaries, and consent triggers.

Steps:
1. Draft a Constitution Manifest (`schemas/constitution.schema.json`).
2. Create Boundary Cards (`schemas/boundary-card.schema.json`) for high-risk constraints.
3. Reference Boundary Cards from the Constitution to avoid duplication and drift.
4. Approve via Council decision and log in Decision Register.
5. (Recommended) Compile constitution into enforcement rules and compute `compiled_hash`.

Pitfalls & mitigations:
- **Pitfall:** boundaries exist only on paper.  
  **Mitigation:** IR-Conformant+ requires testable hooks and enforcement mechanisms.

### Phase 3 — Consent capture (Dossier: LVA-*)
**Goal:** Obtain FPIC for the defined scope.

Steps:
1. Run consent session(s) using FPIC record template (`templates/consent/FPIC_Record_Template.md`).
2. Generate machine-readable Consent Records (`schemas/consent-record.schema.json`).
3. Link evidence references (minutes, translations, recordings, hashes).
4. Ensure all enabled features map to active consent scope(s).

Pitfalls & mitigations:
- **Pitfall:** “consent once, forever” assumptions.  
  **Mitigation:** define expiry and triggers; build re-consent workflow.

### Phase 4 — Node deployment & artifact store (Dossier: IR-OPS-*)
**Goal:** Deploy offline-first infrastructure that can operate locally and sync safely.

Steps:
1. Implement an artifact store for:
   - Constitutions, boundary cards, consent records, decisions, audit entries
2. Implement Graph Node support (`schemas/graph-node.schema.json`) for linking artifacts and decisions.
3. Implement export bundles for audit and review (zip/tar with hashes).
4. If multiple audit streams exist, include a stream manifest (stream_id list, heads, genesis policy).

Offline-first recommendations:
- Use append-only logs locally; sync by exchanging batches with content-addressed identifiers.
- Make merges explicit and auditable (log conflicts as SYSTEM_EVENT).

### Phase 5 — Audit log (hash-chain) implementation (Dossier: IR-AUD-*)
**Goal:** Produce verifiable audit trails.

Steps:
1. Implement Audit Entry creation (`schemas/audit-entry.schema.json`).
2. Define canonical serialization rules for hashing (see `specification/hash-and-canonicalization.md`).
3. Chain entries using `prev_hash` within each stream and keep `sequence_number` monotonic per `stream_id`.
4. (Recommended) Sign critical events with W3C VC-style proofs.

Minimum events to record:
- GOVERNANCE_DECISION (link to decision ID)
- CONSENT_CHANGE (status transitions)
- CONSTITUTION_UPDATE (new manifest adopted)
- DATA_ACCESS (read/write/export operations)
- SECURITY_ALERT and KILL_SWITCH_ACTIVATION

### Phase 6 — Operations, reporting, and review (Dossier: IR-TRANS-*)
**Goal:** Keep the system accountable and legible.

Steps:
- Produce periodic transparency reports (monthly/quarterly)
- Hold review meetings per charter
- Refresh consent as needed
- Review boundary exceptions and renewals

---

## 3. Common pitfalls (and mitigations)

- **Unclear “NonCommercial” boundary in license usage:**  
  Mitigation: document acceptable use cases and keep commercial integrations separate from the standard artifacts.

- **Identity brittleness offline:**  
  Mitigation: support local principals with later DID binding; record identity changes in audit log.

- **Evidence loss (device failure):**  
  Mitigation: regular encrypted backups; printed summaries when needed; store hashes in multiple places.

- **Consent materials not accessible:**  
  Mitigation: multi-language artifacts, local interpretation, low-bandwidth formats.

---

## 4. Schema references

- Graph nodes: `schemas/graph-node.schema.json`
- Constitution manifests: `schemas/constitution.schema.json`
- Audit entries: `schemas/audit-entry.schema.json`
- Consent records: `schemas/consent-record.schema.json`
- Boundary cards: `schemas/boundary-card.schema.json`

---

## 5. Minimal conformance test plan (suggested)

1. Validate a sample artifact of each schema with a draft 2020-12 validator.
2. Create an audit chain of ≥ 10 entries and verify:
   - sequence continuity
   - prev_hash continuity
   - recomputed entry_hash matches
3. Enforce at least one boundary via a test hook (or documented process gate).
4. Demonstrate consent status enforcement by revoking a consent and blocking a feature.

See the conformance checklist: `specification/conformance/checklist.md`.
