<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Qori Labs — Laboratorio de Tecnología de Interés Público

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Conformance Checklist — IR v1.0

This checklist defines normative conformance requirements for **IR-Conformant** and **IR-Conformant+** implementations.

**How to use**
- Tick the checkbox when the requirement is satisfied.
- Populate the evidence field with a file path, URI, or content-addressed hash to an export bundle artifact.
- Requirement IDs map to Dossier-style categories (e.g., `LVA-*`, `IR-GOV-*`, `IR-AUD-*`).

> Note: The `| Evidence:` delimiter is used as a consistent “evidence column” even though this is a task list.

---

## IR-Conformant (minimum)

- [ ] **IR-SCHEMA-001:** System MUST produce artifacts that validate against the normative JSON Schemas in `schemas/`. | Evidence: {{EVIDENCE_IR-SCHEMA-001}}
- [ ] **IR-GOV-001:** Deployment MUST have an adopted Council Charter (based on `Council_Charter_Template.md`) with named decision body and quorum rules. | Evidence: {{EVIDENCE_IR-GOV-001}}
- [ ] **IR-GOV-002:** Deployment MUST maintain a Decision Register (CSV) with traceable decision IDs and outcomes. | Evidence: {{EVIDENCE_IR-GOV-002}}
- [ ] **IR-GOV-003:** Deployment MUST identify at least one Custodian and maintain signed Custodian Declarations. | Evidence: {{EVIDENCE_IR-GOV-003}}
- [ ] **LVA-001:** Deployment MUST have an auditable consent baseline: at least one Consent Record (FPIC) covering all enabled features and data categories. | Evidence: {{EVIDENCE_LVA-001}}
- [ ] **LVA-002:** Consent status transitions (active/revoked/expired/superseded) MUST be recorded and MUST affect enforcement (no processing outside active consent scope). | Evidence: {{EVIDENCE_LVA-002}}
- [ ] **IR-CONST-001:** Deployment MUST have a Constitution Manifest that declares principles, boundaries, and consent triggers. | Evidence: {{EVIDENCE_IR-CONST-001}}
- [ ] **IR-BOUND-001:** Deployment MUST have at least one Boundary Card linked to the Constitution or Decision Register. | Evidence: {{EVIDENCE_IR-BOUND-001}}
- [ ] **IR-AUD-001:** System MUST record events as hash-chained Audit Entries and MUST preserve ordering by `sequence_number`. | Evidence: {{EVIDENCE_IR-AUD-001}}
- [ ] **IR-AUD-002:** Audit evidence export MUST include the full audit chain and validation instructions sufficient to recompute hashes and verify continuity. | Evidence: {{EVIDENCE_IR-AUD-002}}
- [ ] **IR-OPS-001:** System MUST support offline-first operation: artifacts MUST be serializable, locally durable, and sync-safe (store-and-forward acceptable). | Evidence: {{EVIDENCE_IR-OPS-001}}
- [ ] **IR-SEC-001:** System MUST provide a documented incident reporting pathway and MUST record SECURITY_ALERT events in the audit log. | Evidence: {{EVIDENCE_IR-SEC-001}}

---

## IR-Conformant+ (extended)

- [ ] **IR-CRYPTO-001:** Constitution manifests SHOULD include `compiled_hash` and MUST include at least one verifiable proof/signature when published externally. | Evidence: {{EVIDENCE_IR-CRYPTO-001}}
- [ ] **IR-CRYPTO-002:** SECURITY_ALERT and KILL_SWITCH_ACTIVATION audit entries MUST include at least one verifiable signature/proof over `entry_hash`. | Evidence: {{EVIDENCE_IR-CRYPTO-002}}
- [ ] **IR-AUD-003:** System SHOULD provide a machine-readable conformance report mapping requirements to evidence pointers. | Evidence: {{EVIDENCE_IR-AUD-003}}
- [ ] **IR-BOUND-002:** Boundary Cards MUST be enforced via runtime or process controls with testable hooks (e.g., policy engine rules and unit/integration tests). | Evidence: {{EVIDENCE_IR-BOUND-002}}
- [ ] **LVA-003:** Consent triggers MUST be implemented such that enabling a new feature or expanding scope blocks operation until a new consent decision is recorded. | Evidence: {{EVIDENCE_LVA-003}}
- [ ] **IR-GOV-004:** Conflicts of interest MUST be declared and logged; recusals MUST be recorded for relevant decisions. | Evidence: {{EVIDENCE_IR-GOV-004}}
- [ ] **IR-TRANS-001:** System SHOULD produce periodic transparency reports consumable by community members (multi-locale recommended). | Evidence: {{EVIDENCE_IR-TRANS-001}}
- [ ] **IR-RES-001:** Deployment SHOULD document resilience practices (backup/restore, disaster recovery, and offline queue management). | Evidence: {{EVIDENCE_IR-RES-001}}
