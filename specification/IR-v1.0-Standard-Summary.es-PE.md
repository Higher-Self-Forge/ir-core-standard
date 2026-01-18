<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Resumen del Estándar IR v1.0 — Infraestructura Soberana e Inteligencia Distribuida

> Traducción informativa; la versión normativa es `specification/IR-v1.0-Standard-Summary.md`.

Este documento ofrece una visión concisa del **IR v1.0 Core Standard** y de los artefactos normativos en este repositorio.

> Nota: Los requisitos normativos se expresan con **MUST**, **SHOULD** y **MAY** según las convenciones IETF.

---

## 1. Alcance

IR v1.0 especifica un conjunto mínimo e interoperable de estructuras de datos y artefactos de gobernanza para desplegar **infraestructura soberana e IA *offline-first*** en contextos donde:
- La conectividad es intermitente o limitada
- Se requiere gobernanza comunitaria y consentimiento para legitimidad
- El comportamiento del sistema debe ser auditable y revisable en el tiempo

IR v1.0 **no** prescribe:
- Una arquitectura específica de modelos de IA
- Un motor de base de datos o protocolo de red específicos
- Un proveedor de identidad o método DID específico

En cambio, IR v1.0 define **artefactos portables** y **requisitos de conformidad** que las implementaciones pueden cumplir con elecciones locales.

---

## 2. Tipos de artefactos normativos

### 2.1 Graph Nodes
Un **Graph Node** es una estructura de propósito general para representar entidades, eventos, decisiones, artefactos y relaciones en un grafo de conocimiento de despliegue.

Esquema: `schemas/graph-node.schema.json`

Nota: el `id` de Graph Node DEBE ser un UUID. Otros identificadores de artefactos PUEDEN ser URI/URN según sus esquemas.

### 2.2 Manifiestos de Constitución
Un **Manifiesto de Constitución** declara principios exigibles y límites que restringen el comportamiento del sistema y la toma de decisiones de gobernanza, incluyendo disparadores de consentimiento.

Esquema: `schemas/constitution.schema.json`

El contenido de límites DEBERÍA mantenerse en Boundary Cards y referenciarse desde la Constitución para evitar deriva.

### 2.3 Boundary Cards
Una **Boundary Card** es una restricción ética/legal/cultural/técnica expresada como un objeto legible por máquina, apto para hooks de cumplimiento y revisión humana.

Esquema: `schemas/boundary-card.schema.json`

Boundary Cards son la fuente de verdad; las Constituciones deberían referenciarlas en lugar de duplicar contenido.

Nota de mantenimiento (informativa): si cambian los campos de Boundary Cards, actualice tanto `boundary-card.schema.json` como la definición embebida en `constitution.schema.json` en paralelo.

### 2.4 Registros de Consentimiento (FPIC)
Un **Registro de Consentimiento** documenta el Consentimiento Libre, Previo e Informado para un alcance definido, con transiciones de estado y referencias de evidencia. Los registros de consentimiento DEBERÍAN incluir notas de alineamiento con los Principios CARE.

Esquema: `schemas/consent-record.schema.json`

### 2.5 Entradas de Auditoría (Hash-Chain)
Una **Entrada de Auditoría** es un registro de eventos append-only diseñado para encadenarse por hash. Las implementaciones DEBEN preservar la integridad de la cadena y DEBERÍAN soportar atestación criptográfica para eventos de alto impacto.

Esquema: `schemas/audit-entry.schema.json`

Las secuencias y `prev_hash` se interpretan dentro de un stream; los despliegues pueden operar múltiples streams.

---

## 3. Artefactos de gobernanza (plantillas)

IR v1.0 provee plantillas alineadas a lo normativo:
- Carta del Consejo (roles, quórum, proceso de decisión)
- Registro de Decisiones (CSV con decisiones)
- Declaración de Custodia (compromisos y responsabilidades)
- Plantilla de registro FPIC (captura de consentimiento legible por la comunidad)
- Acuerdo de Retorno de Valor (alianza + retorno de beneficios)

Las plantillas se encuentran en `templates/`.

---

## 4. Conformidad

Las implementaciones DEBEN declarar uno de:
- **IR-Conformant** (mínimo) — gobernanza base, validez de esquemas, evidencia exportable
- **IR-Conformant+** (extendido) — verificación criptográfica más fuerte, reportes automatizados, hooks de cumplimiento en runtime

Ver: `specification/conformance/checklist.md`

Hashing y canonicalización: `specification/hash-and-canonicalization.md`

---

## 5. Notas de interoperabilidad

IR v1.0 adopta patrones establecidos cuando resulta útil:
- **Pruebas tipo W3C Verifiable Credentials** para firmas/atestaciones en artefactos de constitución
- **Integridad por hash-chain** para entradas de auditoría
- **Gobernanza legible para humanos** con plantillas alineadas a procesos comunitarios

---

## 6. Versionado y control de cambios

- Los valores `$id` de los esquemas están versionados bajo `/schemas/v1.0/` en sus URLs; los archivos viven en `schemas/*.schema.json`.
- Cambios incompatibles con versiones anteriores DEBEN incrementar la versión mayor y actualizar rutas `$id` en consecuencia.
- Cambios en requisitos normativos DEBEN reflejarse en la lista de conformidad.

---

## 7. Licencia y stewardship

Este estándar está licenciado bajo CC BY-NC-SA 4.0.

Owner/Rights Holder: Higher Self Forge Ltd (UK).  
Research & field lab: Qori Labs (Peru).

Para consultas de licenciamiento comercial o doble licenciamiento, contacte a Higher Self Forge Ltd.
