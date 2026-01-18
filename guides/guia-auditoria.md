<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Guía de Auditoría — IR v1.0

Esta guía apoya a auditores independientes o comunitarios en la evaluación de conformidad con IR v1.0. Asume acceso a un paquete de exportación de evidencias que contiene artefactos y registros.

> Traducción informativa; la versión normativa es la guía en inglés: `guides/auditor-guide.md`.

---

## 1. Objetivos de auditoría
- Verificar legitimidad de la gobernanza (carta, custodios, proceso de decisión)
- Verificar que existan consentimientos y límites, y que se apliquen
- Verificar controles de integridad (continuidad de Hash-Chain, firmas si aplica)
- Verificar que la evidencia sea exportable y revisable sin conexión

---

## 2. Contenido del paquete de evidencias (recomendado)
Una implementación DEBERÍA exportar un paquete que incluya:
- Manifiesto(s) de constitución + notas de hash compilado
- Boundary cards y referencias
- Registros de consentimiento + referencias de evidencia
- Registro de decisiones y actas de reunión
- Flujo(s) completo(s) del registro de auditoría con notas del procedimiento de hashing
- Manifiesto de streams de auditoría con stream_id y head por stream
- Manifiesto de hashes de los archivos del paquete (se recomienda direccionamiento por contenido)
- Método de canonicalización utilizado (ver `specification/hash-and-canonicalization.md`)

### 2.1 Terminología clave
- **Hash-Chain (cadena hash):** secuencia de entradas de auditoría donde cada `entry_hash` se calcula incorporando el `prev_hash` de la entrada anterior; permite detectar alteraciones y preservar integridad.
- **White Room (sala blanca):** entorno de verificación aislado y limpio, independiente del sistema auditado, usado para recomputar hashes y validar el paquete de evidencias sin contaminación.

---

## 3. Procedimiento de evaluación de conformidad

### Paso 1 — Identificar el nivel de conformidad declarado
- Ubicar la declaración o reporte de conformidad del implementador.
- Determinar si el reclamo es **IR-Conformant** o **IR-Conformant+**.

### Paso 2 — Validar esquemas
Use un validador JSON Schema (draft 2020-12) para validar:
- artefactos de `schemas/constitution.schema.json`
- artefactos de `schemas/boundary-card.schema.json`
- artefactos de `schemas/consent-record.schema.json`
- artefactos de `schemas/audit-entry.schema.json`
- artefactos de `schemas/graph-node.schema.json` (si se usan)

### Paso 3 — Revisión de gobernanza
- Confirmar que exista una Carta del Consejo y que esté adoptada (evidencia de firma).
- Confirmar que los custodios estén identificados y existan declaraciones.
- Cruzar entradas del Registro de Decisiones con entradas de auditoría correspondientes (GOVERNANCE_DECISION).

### Paso 4 — Revisión de consentimiento (FPIC)
- Confirmar que cada función/categoría de datos habilitada se mapee a un alcance **activo** de Consent Record.
- Confirmar que los disparadores de consentimiento en la constitución se alineen con las operaciones:
  - introducir nuevos datasets/funciones debería producir eventos CONSENT_CHANGE o GOVERNANCE_DECISION
- Revisar referencias de evidencia (actas, traducciones, fotos) para completitud y accesibilidad.

### Paso 5 — Revisión de límites
- Confirmar que existan boundary cards para restricciones de alto riesgo.
- Confirmar que los mecanismos de cumplimiento estén documentados.
- Para IR-Conformant+, exigir evidencia de hooks de prueba o reglas de política.

### Paso 6 — Integridad del registro de auditoría
- Verificar que `sequence_number` incremente en 1 dentro de cada `stream_id`.
- Verificar que `prev_hash` sea igual al `entry_hash` anterior dentro de cada stream.
- Recalcular `entry_hash` usando el método de canonicalización documentado (ver `specification/hash-and-canonicalization.md`) idealmente en un entorno White Room.
- Para IR-Conformant+:
  - Verificar firmas en entradas SECURITY_ALERT y KILL_SWITCH_ACTIVATION.

### Paso 7 — Kill switch y manejo de incidentes
- Confirmar que la autoridad de kill switch esté documentada en la carta.
- Confirmar que cualquier activación esté registrada como `KILL_SWITCH_ACTIVATION` con evidencia.
- Confirmar que decisiones de restitución y revisiones estén registradas.

---

## 4. Muestreo y entrevistas (recomendado)
- Muestrear decisiones a lo largo de la línea de tiempo del despliegue y validar trazabilidad.
- Entrevistar a custodios sobre:
  - procedimientos de sincronización *Offline-First*
  - pasos de respuesta a incidentes
  - cómo se gestionan las actualizaciones de consentimiento
- Entrevistar a representantes comunitarios sobre:
  - accesibilidad de materiales de consentimiento
  - beneficio percibido y transparencia

---

## 5. Reporte
Los reportes de auditoría DEBERÍAN incluir:
- Determinación del nivel de conformidad
- Lista de verificación con referencias de evidencia
- No conformidades y recomendaciones de remediación
- Cualquier riesgo que requiera atención urgente
