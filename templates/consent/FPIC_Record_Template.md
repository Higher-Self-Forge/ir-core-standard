<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
---
version: "1.0"
status: "stable"
locale_primary: "es-PE"
locales_supported:
  - "es-PE"
  - "quz"
community_name: "{{COMMUNITY_NAME}}"
consent_session_id: "{{CONSENT_SESSION_ID}}"
---

# FPIC Record — {{COMMUNITY_NAME}}

<!--
INSTRUCTIONS:
- This template captures Free, Prior, and Informed Consent in a community-legible format.
- Add translations under the language sections.
- Link to machine-readable Consent Record objects (schemas/consent-record.schema.json) when possible.
-->

## A. Consent Scope

**Purpose (why):** {{PURPOSE}}  
**What data:** {{DATA_CATEGORIES}}  
**What processing:** {{PROCESSING_ACTIVITIES}}  
**Who benefits / who can access outputs:** {{BENEFICIARIES}}  
**Where (geography):** {{GEOGRAPHY}}  
**How long (retention):** {{RETENTION}}  
**Derivatives (models/reports):** {{DERIVATIVES_RULES}}

## B. Information Provided

<!-- List materials presented (slides, demos, risks, rights). -->
- Materials: {{MATERIALS_LIST}}
- Risks discussed: {{RISKS_DISCLOSED}}
- Rights explained (including revocation): {{RIGHTS_EXPLAINED}}
- Contact/complaints channel: {{CONTACT_CHANNEL}}

## C. Understanding Verification

<!-- Document how understanding was verified (Q&A, re-explanation, quizzes, peer interpretation). -->
- Verification method: {{UNDERSTANDING_METHOD}}
- Key questions asked: {{KEY_QUESTIONS}}
- Responses summary: {{RESPONSES_SUMMARY}}
- Interpreter(s) (if any): {{INTERPRETERS}}

## D. Conditions (if any)

<!-- Conditions become binding constraints; mirror them into the machine-readable consent record. -->
- Condition 1: {{CONDITION_1}}
- Condition 2: {{CONDITION_2}}
- Condition 3: {{CONDITION_3}}

## E. Revocation Mechanism

<!-- Describe how consent can be revoked, timelines, and what happens to data and outputs. -->
- Revocation request method: {{REVOCATION_METHOD}}
- Expected response time: {{REVOCATION_SLA}}
- Effect of revocation: {{REVOCATION_EFFECTS}}

## F. Multi-language Record

<!-- Provide a parallel statement in each supported language. -->
### F.1 Español (es-PE)
{{FPIC_TEXT_ES}}

### F.2 Quechua (quz)
{{FPIC_TEXT_QUZ}}

### F.3 Other / Additional Language
{{FPIC_TEXT_OTHER}}

---

## Signatures / Thumbprints

<!-- Use additional rows as needed. -->
**Date:** {{DATE}}  
**Location:** {{LOCATION}}

| Name | Role / Relationship | Signature | Thumbprint (if used) |
|---|---|---|---|
| {{NAME_1}} | {{ROLE_1}} | _______________________ | _______________________ |
| {{NAME_2}} | {{ROLE_2}} | _______________________ | _______________________ |
| {{NAME_3}} | {{ROLE_3}} | _______________________ | _______________________ |

**Witness / Facilitator:** {{FACILITATOR_NAME}} _______________________  
**Interpreter (if any):** {{INTERPRETER_NAME}} _______________________
