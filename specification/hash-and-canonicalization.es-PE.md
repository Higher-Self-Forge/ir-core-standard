<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Hashing y Canonicalización (Traducción informativa)

> Traducción informativa; la versión normativa es `specification/hash-and-canonicalization.md`.

Este documento define el método de canonicalización y hashing usado para entradas de auditoría IR.

## 1. Método de canonicalización

- Las implementaciones DEBEN usar JSON Canonicalization Scheme (RFC 8785 / JCS).
- La entrada para canonicalización DEBE estar codificada en UTF-8.

## 2. Entrada para hash (audit entry)

El objeto hasheado DEBE incluir **todos los campos de primer nivel** de una entrada de auditoría **excepto**:
- `entry_hash`
- `signatures`

Esto significa que campos como `sequence_number`, `stream_id`, `timestamp`, `event_type`, `actor`, `payload`, `prev_hash` y `metadata` (cuando existan) se incluyen en el objeto canonicalizado.

Si un campo opcional está ausente, se omite del objeto canonicalizado.

## 2.1 Valor génesis

Para la primera entrada de un stream (`sequence_number = 1`), `prev_hash` DEBE ser el valor génesis fijo:

`0000000000000000000000000000000000000000000000000000000000000000`

## 3. Algoritmo y representación

- El algoritmo de digest DEBE ser SHA-256 sobre los bytes canonicalizados en UTF-8.
- La representación por defecto es hexadecimal en minúsculas (64 caracteres).
- Representaciones alternativas (p. ej., multibase) SOLO PUEDEN usarse si se declaran explícitamente en el manifiesto del paquete de evidencia.

## 4. Firmas

Cuando existan, las firmas DEBERÍAN calcularse sobre `entry_hash`. Los objetos de firma se excluyen de la entrada para hash para preservar la verificabilidad.
