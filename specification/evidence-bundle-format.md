<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Evidence Bundle Format (Informative / Non-Normative)

This document describes a minimal, repeatable evidence bundle layout to support audits and community review.

## 1. Minimum contents (recommended)

An evidence bundle SHOULD include:
- Constitution manifest(s)
- Boundary Card artifacts
- Consent records and references
- Decision Register and meeting minutes
- Audit log stream files
- Hash manifest for bundle files
- Hashing and canonicalization notes

## 2. Recommended layout

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

### manifest.json (recommended)
Include:
- bundle_id, created_at, created_by
- canonicalization method (e.g., RFC 8785) and hash algorithm
- hash representation (hex or multibase)
- references to stream-manifest and hashes file

### audit/stream-manifest.json (recommended)
List:
- all `stream_id` values
- current heads per stream (`entry_hash`)
- genesis value policy (e.g., fixed string or null)
- notes for multi-stream reconciliation, if used

## 3. Evidence references

Evidence pointers SHOULD be stable and resolvable within the bundle.
Example convention: `local://artifacts/consent/CR-2026-001.json`.

## 4. Hash manifest

A file hash manifest (e.g., `hashes.txt`) SHOULD list:
- file path
- hash value
- hash algorithm

This supports end-to-end bundle integrity checks.
