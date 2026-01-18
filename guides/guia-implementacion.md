<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Guía de Implementación — IR v1.0

Esta guía ayuda a las entidades implementadoras a construir un sistema conforme a IR v1.0 (Ayni Algorítmico). Está escrita para ser accionable por equipos de ingeniería y facilitadores de gobernanza.

> Traducción informativa; la versión normativa es la guía en inglés: `guides/implementation-guide.md`.

---

## 1. Prerrequisitos

### 1.1 Hardware (despliegue *Offline-First* típico)
- Un nodo de cómputo local (x86_64 o ARM64) con:
  - 16–64 GB de RAM según el tamaño del modelo
  - Almacenamiento local duradero (SSD recomendado)
  - GPU/NPU opcional si se requiere inferencia
- Red local: router Wi‑Fi o nodo de malla
- Resiliencia energética: UPS o solar + batería cuando sea posible
- Almacenamiento físico seguro para respaldos de evidencia (unidades removibles cifradas)

### 1.2 Software
- Un validador JSON Schema compatible con draft 2020-12
- Una base de datos/almacenamiento local para artefactos (documental o relacional)
- Un mecanismo de sincronización (store-and-forward, replicación oportunista)
- Soporte criptográfico (recomendado): Ed25519 u otra suite de firmas moderna
- Una capa de cumplimiento de políticas (recomendada para IR-Conformant+)

### 1.3 Gobernanza
- Carta del Consejo adoptada (ver `templates/governance/Council_Charter_Template.md`)
- Custodios designados y declaraciones de custodia firmadas
- Proceso de registro de decisiones
- Flujo de consentimiento FPIC y materiales correspondientes

---

## 2. Ciclo de vida alineado al expediente (por fases)

> El concepto de “Dossier” se refiere a un expediente de evidencia que respalda la auditoría y la revisión comunitaria.

### Fase 0 — Inicio y alcance (Dossier: LVA-*)
**Objetivo:** Definir por qué existe el sistema y qué hará (y qué no hará).

Entregables:
- Borrador de declaración de propósito y alcance inicial
- Borrador de lista de verificación de materiales de consentimiento (`templates/consent/Consent_Materials_Checklist.md`)
- Registro inicial de riesgos (informativo)

Riesgos y mitigaciones:
- **Riesgo:** deriva de alcance de “piloto” a “producción” sin consentimiento.  
  **Mitigación:** definir los disparadores de consentimiento temprano en la constitución.

### Fase 1 — Configuración de gobernanza (Dossier: IR-GOV-*)
**Objetivo:** Establecer autoridad legítima de toma de decisiones.

Pasos:
1. Personalizar y adoptar la plantilla de la Carta del Consejo.
2. Asignar custodios y recopilar declaraciones firmadas.
3. Inicializar el Registro de Decisiones y acordar el formato de los ID de decisión.

Referencias de evidencia:
- PDF/MD de la carta, declaraciones firmadas, instantánea del registro de decisiones.

### Fase 2 — Constitución y definición de límites (Dossier: IR-CONST-*, IR-BOUND-*)
**Objetivo:** Declarar principios exigibles, límites y disparadores de consentimiento.

Pasos:
1. Redactar un Manifiesto de Constitución (`schemas/constitution.schema.json`).
2. Crear Boundary Cards (`schemas/boundary-card.schema.json`) para restricciones de alto riesgo.
3. Referenciar las Boundary Cards desde la Constitución para evitar duplicación y deriva.
4. Aprobar mediante decisión del Consejo y registrar en el Registro de Decisiones.
5. (Recomendado) Compilar la constitución en reglas de cumplimiento y calcular `compiled_hash`.

Riesgos y mitigaciones:
- **Riesgo:** los límites existen solo en papel.  
  **Mitigación:** IR-Conformant+ requiere hooks testeables y mecanismos de cumplimiento.

### Fase 3 — Captura de consentimiento (Dossier: LVA-*)
**Objetivo:** Obtener FPIC para el alcance definido.

Pasos:
1. Realizar sesión(es) de consentimiento usando la plantilla FPIC (`templates/consent/FPIC_Record_Template.md`).
2. Generar Registros de Consentimiento legibles por máquina (`schemas/consent-record.schema.json`).
3. Vincular referencias de evidencia (actas, traducciones, grabaciones, hashes).
4. Asegurar que todas las funciones habilitadas se mapeen a alcance(s) de consentimiento activo(s).

Riesgos y mitigaciones:
- **Riesgo:** supuestos de “consentir una vez, para siempre”.  
  **Mitigación:** definir vencimientos y disparadores; construir flujo de re-consentimiento.

### Fase 4 — Despliegue de nodos y almacén de artefactos (Dossier: IR-OPS-*)
**Objetivo:** Desplegar infraestructura *Offline-First* que pueda operar localmente y sincronizar de forma segura.

Pasos:
1. Implementar un almacén de artefactos para:
   - Constituciones, boundary cards, registros de consentimiento, decisiones, entradas de auditoría
2. Implementar soporte de Graph Nodes (`schemas/graph-node.schema.json`) para vincular artefactos y decisiones.
3. Implementar paquetes de exportación para auditoría y revisión (zip/tar con hashes).
4. Si existen múltiples streams de auditoría, incluir un manifiesto de streams (lista de stream_id, heads, política de génesis).

Recomendaciones *Offline-First*:
- Usar registros append-only localmente; sincronizar intercambiando lotes con identificadores direccionados por contenido.
- Hacer las fusiones explícitas y auditables (registrar conflictos como SYSTEM_EVENT).

### Fase 5 — Implementación del registro de auditoría (Hash-Chain) (Dossier: IR-AUD-*)
**Objetivo:** Producir trazas de auditoría verificables.

Pasos:
1. Implementar creación de Audit Entry (`schemas/audit-entry.schema.json`).
2. Definir reglas de serialización canónica para hashing (ver `specification/hash-and-canonicalization.md`).
3. Encadenar entradas usando `prev_hash` dentro de cada stream y mantener `sequence_number` monotónico por `stream_id`.
4. (Recomendado) Firmar eventos críticos con pruebas estilo W3C VC.

Eventos mínimos a registrar:
- GOVERNANCE_DECISION (enlace al ID de decisión)
- CONSENT_CHANGE (transiciones de estado)
- CONSTITUTION_UPDATE (nuevo manifiesto adoptado)
- DATA_ACCESS (operaciones de lectura/escritura/exportación)
- SECURITY_ALERT y KILL_SWITCH_ACTIVATION

### Fase 6 — Operación, reportes y revisión (Dossier: IR-TRANS-*)
**Objetivo:** Mantener el sistema responsable y legible.

Pasos:
- Elaborar reportes de transparencia periódicos (mensual/trimestral)
- Realizar reuniones de revisión según la carta
- Renovar el consentimiento cuando corresponda
- Revisar excepciones y renovaciones de límites

---

## 3. Riesgos comunes (y mitigaciones)

- **Límite “NonCommercial” poco claro en uso de licencia:**  
  Mitigación: documentar casos de uso aceptables y mantener integraciones comerciales separadas de los artefactos estándar.

- **Fragilidad de identidad en modo offline:**  
  Mitigación: soportar identidades locales con posterior vinculación a DID; registrar cambios de identidad en el registro de auditoría.

- **Pérdida de evidencia (fallo de dispositivos):**  
  Mitigación: respaldos cifrados regulares; resúmenes impresos cuando sea necesario; almacenar hashes en múltiples lugares.

- **Materiales de consentimiento no accesibles:**  
  Mitigación: artefactos multilingües, interpretación local, formatos de bajo ancho de banda.

---

## 4. Referencias de esquemas

- Graph nodes: `schemas/graph-node.schema.json`
- Constitution manifests: `schemas/constitution.schema.json`
- Audit entries: `schemas/audit-entry.schema.json`
- Consent records: `schemas/consent-record.schema.json`
- Boundary cards: `schemas/boundary-card.schema.json`

---

## 5. Plan mínimo de pruebas de conformidad (sugerido)

1. Validar un artefacto de muestra de cada esquema con un validador draft 2020-12.
2. Crear una cadena de auditoría de ≥ 10 entradas y verificar:
   - continuidad de secuencia
   - continuidad de prev_hash
   - coincidencia de entry_hash recomputado
3. Hacer cumplir al menos un límite mediante un hook de prueba (o un control de proceso documentado).
4. Demostrar la aplicación de estado de consentimiento revocando un consentimiento y bloqueando una función.

Ver la lista de conformidad: `specification/conformance/checklist.md`.
