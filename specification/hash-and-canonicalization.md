<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
# Hashing & Canonicalization (Normative)

This document defines the canonicalization and hashing method used for IR audit entries.

## 1. Canonicalization method

- Implementations MUST use JSON Canonicalization Scheme (RFC 8785 / JCS).
- Canonicalization input MUST be UTF-8 encoded.

## 2. Hash input (audit entry)

The hashed object MUST include **all top-level fields** of an audit entry **except**:
- `entry_hash`
- `signatures`

This means fields such as `sequence_number`, `stream_id`, `timestamp`, `event_type`, `actor`, `payload`, `prev_hash`, and `metadata` (when present) are included in the canonicalized object.

If an optional field is absent, it is omitted from the canonicalized object.

## 2.1 Genesis value

For the first entry in a stream (`sequence_number = 1`), `prev_hash` MUST be the fixed genesis value:

`0000000000000000000000000000000000000000000000000000000000000000`

## 3. Digest algorithm and representation

- Digest algorithm MUST be SHA-256 over the canonicalized UTF-8 bytes.
- The default representation is lowercase hexadecimal (64 chars).
- Alternate representations (e.g., multibase) MAY be used only if explicitly declared in the evidence bundle manifest.

## 4. Signatures

When present, signatures SHOULD be computed over `entry_hash`. Signature objects are excluded from the hash input to preserve verifiability.
