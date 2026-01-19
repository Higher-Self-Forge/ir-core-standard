<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Lista de conformidad — IR v1.0

Esta lista define requisitos normativos de conformidad para implementaciones **IR-Conformant** e **IR-Conformant+**.

> Traducción informativa del estándar IR. La sección normativa en inglés comienza más abajo.

**Cómo usarla**
- Marque la casilla cuando el requisito se cumpla.
- Complete el campo de evidencia con una ruta de archivo, URI o hash direccionado por contenido de un artefacto en el paquete de exportación.
- Los IDs de requisitos mapean a categorías tipo Dossier (p. ej., `LVA-*`, `IR-GOV-*`, `IR-AUD-*`).

> Nota: El delimitador `| Evidence:` se usa como una “columna de evidencia” consistente aunque sea una lista de tareas.

---

## IR-Conformant (mínimo)

- [ ] **IR-SCHEMA-001:** El sistema DEBE producir artefactos que validen contra los esquemas JSON normativos en `schemas/`. | Evidence: {{EVIDENCE_IR-SCHEMA-001}}
- [ ] **IR-GOV-001:** El despliegue DEBE contar con una Carta del Consejo adoptada (basada en `Council_Charter_Template.md`) con órgano decisorio nombrado y reglas de quórum. | Evidence: {{EVIDENCE_IR-GOV-001}}
- [ ] **IR-GOV-002:** El despliegue DEBE mantener un Registro de Decisiones (CSV) con IDs de decisión trazables y resultados. | Evidence: {{EVIDENCE_IR-GOV-002}}
- [ ] **IR-GOV-003:** El despliegue DEBE identificar al menos un Custodio y mantener Declaraciones de Custodia firmadas. | Evidence: {{EVIDENCE_IR-GOV-003}}
- [ ] **LVA-001:** El despliegue DEBE tener una línea base de consentimiento auditable: al menos un Registro de Consentimiento (FPIC) que cubra todas las funciones habilitadas y categorías de datos. | Evidence: {{EVIDENCE_LVA-001}}
- [ ] **LVA-002:** Las transiciones de estado de consentimiento (activo/revocado/vencido/sustituido) DEBEN registrarse y DEBEN afectar el cumplimiento (sin procesamiento fuera del alcance de consentimiento activo). | Evidence: {{EVIDENCE_LVA-002}}
- [ ] **IR-CONST-001:** El despliegue DEBE tener un Manifiesto de Constitución que declare principios, límites y disparadores de consentimiento. | Evidence: {{EVIDENCE_IR-CONST-001}}
- [ ] **IR-BOUND-001:** El despliegue DEBE tener al menos una Boundary Card vinculada a la Constitución o al Registro de Decisiones. | Evidence: {{EVIDENCE_IR-BOUND-001}}
- [ ] **IR-AUD-001:** El sistema DEBE registrar eventos como Audit Entries encadenadas por hash y DEBE preservar el orden por `sequence_number`. | Evidence: {{EVIDENCE_IR-AUD-001}}
- [ ] **IR-AUD-002:** La exportación de evidencia de auditoría DEBE incluir la cadena completa de auditoría e instrucciones de validación suficientes para recomputar hashes y verificar continuidad. | Evidence: {{EVIDENCE_IR-AUD-002}}
- [ ] **IR-OPS-001:** El sistema DEBE soportar operación *Offline-First*: los artefactos DEBEN ser serializables, durables localmente y seguros para sincronización (store-and-forward aceptable). | Evidence: {{EVIDENCE_IR-OPS-001}}
- [ ] **IR-SEC-001:** El sistema DEBE proveer una vía documentada de reporte de incidentes y DEBE registrar eventos SECURITY_ALERT en el registro de auditoría. | Evidence: {{EVIDENCE_IR-SEC-001}}

---

## IR-Conformant+ (extendido)

Nota (informativa): Para validación automática adicional de eventos críticos, ver `specification/conformance/ir-conformant-plus-assertions.schema.json`.

- [ ] **IR-CRYPTO-001:** Los manifiestos de constitución DEBERÍAN incluir `compiled_hash` y DEBEN incluir al menos una prueba/firma verificable cuando se publiquen externamente. | Evidence: {{EVIDENCE_IR-CRYPTO-001}}
- [ ] **IR-CRYPTO-002:** Las entradas de auditoría SECURITY_ALERT y KILL_SWITCH_ACTIVATION DEBEN incluir al menos una firma/prueba verificable sobre `entry_hash`. | Evidence: {{EVIDENCE_IR-CRYPTO-002}}
- [ ] **IR-AUD-003:** El sistema DEBERÍA proporcionar un reporte de conformidad legible por máquina que mapee requisitos a referencias de evidencia. | Evidence: {{EVIDENCE_IR-AUD-003}}
- [ ] **IR-BOUND-002:** Las Boundary Cards DEBEN aplicarse mediante controles de ejecución o de proceso con hooks testeables (p. ej., reglas de motor de políticas y pruebas unitarias/de integración). | Evidence: {{EVIDENCE_IR-BOUND-002}}
- [ ] **LVA-003:** Los disparadores de consentimiento DEBEN implementarse de modo que habilitar una nueva función o ampliar el alcance bloquee la operación hasta que se registre una nueva decisión de consentimiento. | Evidence: {{EVIDENCE_LVA-003}}
- [ ] **IR-GOV-004:** Los conflictos de interés DEBEN declararse y registrarse; las recusaciones DEBEN registrarse para decisiones relevantes. | Evidence: {{EVIDENCE_IR-GOV-004}}
- [ ] **IR-TRANS-001:** El sistema DEBERÍA producir reportes periódicos de transparencia consumibles por miembros de la comunidad (multi-locale recomendado). | Evidence: {{EVIDENCE_IR-TRANS-001}}
- [ ] **IR-RES-001:** El despliegue DEBERÍA documentar prácticas de resiliencia (backup/restore, recuperación ante desastres y gestión de colas offline). | Evidence: {{EVIDENCE_IR-RES-001}}

---

**Normative section begins here (English).**

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

Note (informative): For additional machine-checkable assertions on critical events, see `specification/conformance/ir-conformant-plus-assertions.schema.json`.

- [ ] **IR-CRYPTO-001:** Constitution manifests SHOULD include `compiled_hash` and MUST include at least one verifiable proof/signature when published externally. | Evidence: {{EVIDENCE_IR-CRYPTO-001}}
- [ ] **IR-CRYPTO-002:** SECURITY_ALERT and KILL_SWITCH_ACTIVATION audit entries MUST include at least one verifiable signature/proof over `entry_hash`. | Evidence: {{EVIDENCE_IR-CRYPTO-002}}
- [ ] **IR-AUD-003:** System SHOULD provide a machine-readable conformance report mapping requirements to evidence pointers. | Evidence: {{EVIDENCE_IR-AUD-003}}
- [ ] **IR-BOUND-002:** Boundary Cards MUST be enforced via runtime or process controls with testable hooks (e.g., policy engine rules and unit/integration tests). | Evidence: {{EVIDENCE_IR-BOUND-002}}
- [ ] **LVA-003:** Consent triggers MUST be implemented such that enabling a new feature or expanding scope blocks operation until a new consent decision is recorded. | Evidence: {{EVIDENCE_LVA-003}}
- [ ] **IR-GOV-004:** Conflicts of interest MUST be declared and logged; recusals MUST be recorded for relevant decisions. | Evidence: {{EVIDENCE_IR-GOV-004}}
- [ ] **IR-TRANS-001:** System SHOULD produce periodic transparency reports consumable by community members (multi-locale recommended). | Evidence: {{EVIDENCE_IR-TRANS-001}}
- [ ] **IR-RES-001:** Deployment SHOULD document resilience practices (backup/restore, disaster recovery, and offline queue management). | Evidence: {{EVIDENCE_IR-RES-001}}
