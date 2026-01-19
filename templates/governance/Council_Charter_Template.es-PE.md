<!--
  IR v1.0 Core Standard
  Copyright (c) 2026 Higher Self Forge Ltd (UK) — Owner/Rights Holder
  Research & field lab: Qori Labs (Peru)

  Licensed under Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International
  https://creativecommons.org/licenses/by-nc-sa/4.0/

  SPDX-License-Identifier: CC-BY-NC-SA-4.0
-->
---
version: "1.0.0"
status: "stable"
locale: "es-PE"
community_name: "{{COMMUNITY_NAME}}"
---

# Carta del Consejo — {{COMMUNITY_NAME}}

> Plantilla localizada (es-PE). Este documento es una traducción informativa del estándar IR. Una vez adoptado por una comunidad, es normativo para la gobernanza de ese despliegue, pero no sustituye la especificación normativa en inglés.

<!--
INSTRUCCIONES:
- Esta plantilla define el órgano de gobernanza responsable de los despliegues IR.
- Mantenga un lenguaje legible para la comunidad. Agregue traducciones si corresponde.
- Reemplace los marcadores como {{COMMUNITY_NAME}} y {{QUORUM_THRESHOLD}}.
-->

## 1. Propósito

<!-- Describir por qué existe el Consejo y de qué es responsable. -->
**Propósito:** El Consejo de {{COMMUNITY_NAME}} existe para custodiar infraestructura de IA soberana y *Offline-First* y salvaguardar los derechos, valores y bienestar de la comunidad.

## 2. Composición

<!-- Definir categorías de membresía, proceso de selección, periodos y criterios de retiro. -->
- **Número de custodios:** {{CUSTODIAN_COUNT}}
- **Categorías de miembros:** {{MEMBER_CATEGORIES}}
- **Proceso de selección:** {{SELECTION_PROCESS}}
- **Duración del mandato:** {{TERM_LENGTH}}
- **Remoción / reemplazo:** {{REMOVAL_PROCESS}}

## 3. Reglas de quórum

<!-- Definir umbrales de quórum y reglas de votación. -->
- **Umbral de quórum:** {{QUORUM_THRESHOLD}}
- **Regla de decisión:** {{DECISION_RULE}} (p. ej., mayoría simple / consenso / supermayoría)

## 4. Proceso de toma de decisiones

<!-- Especificar agenda, plazos de aviso, periodicidad de reuniones, registro de decisiones y apelaciones. -->
1. **Aviso y agenda:** {{NOTICE_AND_AGENDA_RULES}}
2. **Facilitación:** {{FACILITATION_METHOD}}
3. **Registro:** Todas las decisiones DEBEN registrarse en el Registro de Decisiones.
4. **Apelaciones / reconsideración:** {{APPEALS_PROCESS}}

## 5. Responsabilidades de custodia

<!-- Aclarar deberes operativos y mecanismos de rendición de cuentas. -->
Los custodios de {{COMMUNITY_NAME}} DEBEN:
- Proteger la soberanía de datos y respetar las decisiones de consentimiento
- Mantener la integridad del sistema y la exportación de evidencias de auditoría
- Hacer cumplir límites y disparadores de consentimiento en la operación
- Proveer reportes de transparencia comunitaria con la frecuencia {{REPORTING_CADENCE}}

## 6. Autoridad de kill switch

<!-- Definir quién puede activar el kill switch, bajo qué condiciones y cómo se restituye. -->
- **Condiciones de activación:** {{KILL_SWITCH_CONDITIONS}}
- **Autoridades autorizadas:** {{KILL_SWITCH_AUTHORITY}}
- **Requisitos de restitución:** {{REINSTATEMENT_REQUIREMENTS}}
- **Requisito de auditoría:** Toda activación de kill switch DEBE registrarse como `KILL_SWITCH_ACTIVATION` en el registro de auditoría con evidencia de respaldo.

## 7. Procedimiento de enmienda

<!-- Definir cómo se enmienda esta carta y cómo se comunican las enmiendas. -->
- **Proceso de propuesta:** {{AMENDMENT_PROPOSAL_PROCESS}}
- **Umbral de aprobación:** {{AMENDMENT_APPROVAL_THRESHOLD}}
- **Regla de vigencia:** {{AMENDMENT_EFFECTIVE_DATE_RULE}}
- **Versionado:** Las versiones de la carta DEBEN numerarse y archivarse.

## 8. Declaraciones de conflicto de interés

<!-- Definir expectativas de divulgación, recusación y cumplimiento. -->
- Los miembros DEBEN declarar cualquier conflicto de interés relacionado con alianzas, proveedores y decisiones de acceso a datos.
- **Método de divulgación:** {{DISCLOSURE_METHOD}}
- **Regla de recusación:** {{RECUSAL_RULE}}
- **Cumplimiento:** {{CONFLICT_ENFORCEMENT}}

---

## Firmas

<!-- Proveer bloques de firma para adopción del Consejo. -->
**Aprobado el:** {{ADOPTION_DATE}}  
**Lugar:** {{ADOPTION_LOCATION}}

| Nombre | Rol | Firma / Huella | Fecha |
|---|---|---|---|
| {{NAME_1}} | {{ROLE_1}} | _______________________ | __________ |
| {{NAME_2}} | {{ROLE_2}} | _______________________ | __________ |
| {{NAME_3}} | {{ROLE_3}} | _______________________ | __________ |
