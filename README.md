<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Qori Labs — Laboratorio de Tecnología de Interés Público

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# IR v1.0 Estándar Núcleo — Infraestructura de IA soberana y offline-first
# IR v1.0 Core Standard — Sovereign Offline-First AI Infrastructure

[![Version](https://img.shields.io/badge/version-v1.0.0-placeholder.svg)](#)
[![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-blue.svg)](LICENSE)
[![Conformance](https://img.shields.io/badge/conformance-IR--Conformant%20%7C%20IR--Conformant%2B-placeholder.svg)](specification/conformance/checklist.md)

**IR v1.0** define un estándar práctico y auditable para desplegar **infraestructura de IA soberana y offline-first** en comunidades con conectividad intermitente—centrado en expectativas de gobernanza de datos indígenas (Principios CARE, prácticas alineadas con OCAP®) y controles de integridad verificables.

**IR v1.0** defines a practical, auditable standard for deploying **sovereign, offline-first AI infrastructure** in communities with intermittent connectivity—centering Indigenous data governance expectations (CARE Principles, OCAP®-aligned practices) and verifiable integrity controls.

Este repositorio es la **referencia autorizada** para implementadores. Contiene:
- **Esquemas JSON normativos** para las estructuras de datos principales
- **Plantillas de gobernanza y consentimiento** adecuadas para despliegues liderados por la comunidad
- **Guías de implementación y auditoría** con requisitos de conformidad

This repository is the **authoritative reference** for implementers. It contains:
- **Normative JSON Schemas** for core data structures
- **Governance and consent templates** suitable for community-led deployments
- **Implementation and audit guides** with conformance requirements

> Licencia: **Creative Commons BY-NC-SA 4.0** (ver `LICENSE`).

> License: **Creative Commons BY-NC-SA 4.0** (see `LICENSE`).

---

## ¿Qué es IR v1.0?

IR (Inteligencia Recíproca) es un marco abierto para construir y operar **sistemas de IA gobernados por la comunidad** que:
- Funcionan **con prioridad offline** (sincronización store-and-forward, operación local resiliente)
- Proveen **gobernanza verificable** (registros de decisiones, custodia y trazas de auditoría)
- Implementan **controles de soberanía de datos** (consentimiento, límites y reglas exigibles)
- Producen **integridad auditable** (cadenas hash, firmas/pruebas y compilación reproducible de constituciones)

IR v1.0 está diseñado para ser implementable por terceros y seguir siendo **legible para la comunidad**: los artefactos de gobernanza son de primera clase, no un complemento.

## What is IR v1.0?

IR (Inteligencia Recíproca) is an open framework for building and operating **community-governed AI systems** that:
- Work **offline first** (store-and-forward sync, resilient local operation)
- Provide **verifiable governance** (decision records, custodianship, and audit trails)
- Implement **data sovereignty controls** (consent, boundaries, and enforceable rules)
- Produce **auditable integrity** (hash-chains, signatures/proofs, and reproducible compilation of constitutions)

IR v1.0 is designed to be implementable by third parties while remaining **community-legible**: the governance artifacts are first-class, not an afterthought.

---

## Quick links

### Normative specification & conformance
- IR v1.0 Standard Summary: `specification/IR-v1.0-Standard-Summary.md`
- Conformance checklist: `specification/conformance/checklist.md`
- Implementation guide: `guides/implementation-guide.md`
- Auditor guide: `guides/auditor-guide.md`

### Core schemas (JSON Schema draft 2020-12)
- Graph Node: `schemas/graph-node.schema.json`
- Constitution Manifest: `schemas/constitution.schema.json`
- Audit Entry (hash-chain): `schemas/audit-entry.schema.json`
- Consent Record (FPIC): `schemas/consent-record.schema.json`
- Boundary Card: `schemas/boundary-card.schema.json`

### Governance & consent templates
- Council Charter: `templates/governance/Council_Charter_Template.md`
- Decision Register (CSV): `templates/governance/Decision_Register_Template.csv`
- Custodian Declaration: `templates/governance/Custodian_Declaration_Template.md`
- FPIC Record template: `templates/consent/FPIC_Record_Template.md`
- Consent Materials Checklist: `templates/consent/Consent_Materials_Checklist.md`
- Value Return Agreement (VRA): `templates/vra/VRA_Template.md`

---

## Conformance levels

IR v1.0 defines two practical conformance levels:

### IR-Conformant (minimum)
An implementation is **IR-Conformant** if it:
- Produces valid artifacts matching all **required** schemas (audit entries, consent records, constitutions, boundary cards, graph nodes)
- Implements a minimum governance baseline (council charter + decision register + named custodians)
- Maintains a verifiable audit log (hash-chained entries) and supports evidence export for review

### IR-Conformant+ (extended)
An implementation is **IR-Conformant+** if it additionally:
- Implements cryptographic proofs/signatures for constitution compilation and critical audit events
- Provides automated conformance reporting (machine-readable checklist evidence)
- Enforces boundary cards and consent triggers in runtime controls with testable hooks
- Supports multi-locale documentation and community-accessible transparency reports

See the checklist: `specification/conformance/checklist.md`.

---

## Repository structure

- `schemas/` — Normative JSON Schemas for IR v1.0 data objects  
- `templates/` — Community governance, consent, and partnership templates  
- `specification/` — Standard summary + conformance requirements  
- `guides/` — Implementation and audit guides  
- `CHANGELOG.md` — Release history  
- `CONTRIBUTING.md` — How to contribute proposals and patches  

---

## Citation (academic / institutional)

If you cite this standard in a paper, policy, or procurement document, use:

> Qori Labs. (2026). *IR v1.0 Core Standard — Sovereign Offline-First AI Infrastructure* (Version 1.0.0). IR Core Standard repository. Licensed CC BY-NC-SA 4.0.

Suggested BibTeX:

```bibtex
@misc{ir_core_standard_v1_2026,
  title        = {IR v1.0 Core Standard — Sovereign Offline-First AI Infrastructure},
  author       = {{Qori Labs}},
  year         = {2026},
  version      = {1.0.0},
  howpublished = {IR Core Standard repository},
  note         = {Licensed under CC BY-NC-SA 4.0}
}
```

---

## Governance of this repository

This repository follows a public standards workflow:
- Issues and PRs are used to propose changes.
- Normative changes should update `CHANGELOG.md` and conformance requirements.
- Schema changes must be backwards-compatible within v1.0 unless explicitly versioned.

See `CONTRIBUTING.md`.

---

## Organization

Maintained by **Qori Labs — Laboratorio de Tecnología de Interés Público**.  
Qori Labs organization: https://github.com/qori-labs
# ir-core-standard
# ir-core-standard-
