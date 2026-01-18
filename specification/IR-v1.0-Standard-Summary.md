<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# IR v1.0 Standard Summary (Normative Overview)

This document provides a concise overview of the **IR v1.0 Core Standard** and the normative artifacts in this repository.

> Note: Normative requirements are expressed with **MUST**, **SHOULD**, and **MAY** as in IETF conventions.

---

## 1. Scope

IR v1.0 specifies a minimal, interoperable set of data structures and governance artifacts for deploying **sovereign, offline-first AI infrastructure** in contexts where:
- Connectivity is intermittent or constrained
- Community governance and consent are required for legitimacy
- System behavior must be auditable and reviewable over time

IR v1.0 does **not** prescribe:
- A specific AI model architecture
- A specific database engine or networking protocol
- A specific identity provider or DID method

Instead, IR v1.0 defines **portable artifacts** and **conformance requirements** that implementations can satisfy using local choices.

---

## 2. Normative artifact types

### 2.1 Graph Nodes
A **Graph Node** is a general-purpose structure for representing entities, events, decisions, artifacts, and relations in a deployment knowledge graph.

Schema: `schemas/graph-node.schema.json`

Note: Graph Node `id` MUST be a UUID. Other artifact identifiers MAY be URI/URN as allowed by their schemas.

### 2.2 Constitution Manifests
A **Constitution Manifest** declares enforceable principles and boundaries that constrain system behavior and governance decision-making, including consent triggers.

Schema: `schemas/constitution.schema.json`

Boundary content SHOULD be maintained in Boundary Cards and referenced from the Constitution to avoid drift.

### 2.3 Boundary Cards
A **Boundary Card** is an ethical/legal/cultural/technical constraint expressed as a machine-readable object suitable for enforcement hooks and human review.

Schema: `schemas/boundary-card.schema.json`

Boundary Cards are the source of truth; Constitutions should reference them rather than duplicate content.

### 2.4 Consent Records (FPIC)
A **Consent Record** documents Free, Prior, and Informed Consent for a defined scope, with status transitions and evidence references. Consent records SHOULD include alignment notes to CARE Principles.

Schema: `schemas/consent-record.schema.json`

### 2.5 Audit Entries (Hash-Chain)
An **Audit Entry** is an append-only event record designed to be hash-chained. Implementations MUST preserve chain integrity and SHOULD support cryptographic attestation for high-impact events.

Schema: `schemas/audit-entry.schema.json`

Sequence numbers and `prev_hash` are interpreted within a stream; deployments may operate multiple streams.

---

## 3. Governance artifacts (templates)

IR v1.0 provides normative-aligned templates:
- Council Charter (roles, quorum, decision process)
- Decision Register (CSV log of decisions)
- Custodian Declaration (commitments and responsibilities)
- FPIC record template (community-legible consent capture)
- Value Return Agreement (partnership + benefit sharing)

Templates are found under `templates/`.

---

## 4. Conformance

Implementations MUST declare one of:
- **IR-Conformant** (minimum) — baseline governance, schema validity, exportable evidence
- **IR-Conformant+** (extended) — stronger cryptographic verification, automated reporting, runtime enforcement hooks

See: `specification/conformance/checklist.md`

Hashing & canonicalization: `specification/hash-and-canonicalization.md`

---

## 5. Interoperability notes

IR v1.0 adopts established patterns when helpful:
- **W3C Verifiable Credentials-style proofs** for signatures/attestations in constitution artifacts
- **Hash-chain integrity** patterns for audit entries
- **Human-legible governance** templates aligned to community decision-making processes

---

## 6. Versioning and change control

- Schema `$id` values are versioned under `/schemas/v1.0/` in their `$id` URLs; repository files live in `schemas/*.schema.json`.
- Backwards incompatible changes MUST increment the major version and update `$id` paths accordingly.
- Normative requirement changes MUST be reflected in the conformance checklist.

---

## 7. License and stewardship

This standard is licensed under CC BY-NC-SA 4.0.

Owner/Rights Holder: Higher Self Forge Ltd (UK).  
Research & field lab: Qori Labs (Peru).

For commercial licensing inquiries or dual-licensing options, please contact Higher Self Forge Ltd.
