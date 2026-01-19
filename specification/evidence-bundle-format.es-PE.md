<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Formato de paquete de evidencia (Informativo / No normativo)

> Traducción informativa del estándar IR. La versión normativa es `specification/evidence-bundle-format.md`.

Este documento describe un formato mínimo y repetible de paquete de evidencia para apoyar auditorías y revisión comunitaria.

## 1. Contenidos mínimos (recomendado)

Un paquete de evidencia DEBERÍA incluir:
- Manifiesto(s) de constitución
- Artefactos Boundary Card
- Registros de consentimiento y referencias
- Registro de decisiones y actas
- Archivos de stream(s) del registro de auditoría
- Manifiesto de hashes de archivos del paquete
- Notas de hashing y canonicalización

## 2. Estructura recomendada

```
/manifest.json
/audit/streams/<stream_id>.jsonl
/audit/stream-manifest.json
/artifacts/constitution/
/artifacts/boundaries/
/artifacts/consent/
/artifacts/decisions/
/hashes.txt
```

### manifest.json (recomendado)
Incluir:
- bundle_id, created_at, created_by
- método de canonicalización (p. ej., RFC 8785) y algoritmo de hash
- representación del hash (hex o multibase)
- referencias a stream-manifest y archivo de hashes

### audit/stream-manifest.json (recomendado)
Listar:
- todos los `stream_id`
- heads actuales por stream (`entry_hash`)
- política de valor génesis (hash fijo; para secuencia 1 use `0000000000000000000000000000000000000000000000000000000000000000`)
- notas para reconciliación multi-stream, si aplica

## 3. Referencias de evidencia

Los punteros de evidencia DEBERÍAN ser estables y resolubles dentro del paquete.
Ejemplo de convención: `local://artifacts/consent/CR-2026-001.json`.

## 4. Manifiesto de hashes

Un manifiesto de hashes (p. ej., `hashes.txt`) DEBERÍA listar:
- ruta del archivo
- valor de hash
- algoritmo de hash

Esto habilita verificaciones de integridad de extremo a extremo.
