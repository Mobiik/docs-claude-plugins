---
description: Propone y crea estructura completa de proyecto en Jira (Iniciativa → Épicas → HUs → Subtareas) con estándar Mobiik
argument-hint: <projectKey opcional, ej: TEC26>
---

Propón y crea la estructura completa del proyecto en Jira siguiendo el estándar Mobiik.

**Project Key:** $ARGUMENTS

## PASO 1 — Validación previa

1. **Verifica acceso a Jira** vía MCP de Atlassian.
2. **Confirma el projectKey** (formato: `[CLIENTE]-[ABREV]`, ej: `TEC-PRESEL`, `BBVA-ONBO`).
3. **Verifica issue types disponibles** del proyecto (debe haber al menos: Epic, Historia/Story, Subtask).
4. **Lista issues existentes** para no duplicar.

## PASO 2 — Proponer estructura

Construye y muestra al usuario una tabla resumen:

| # | Épica | Sprint | # HU | # Subtareas |
|---|---|---|---|---|
| 1 | Análisis Técnico y Planeación | S1 | X | 0 |
| 2 | ... | ... | X | X |

Y la convención de labels que aplicarás:
- `cliente-<nombre>` (todos los issues)
- `sprint-1` / `sprint-2` / `sprint-3` / `go-live`
- `tipo-<migracion|nuevo|mantenimiento>`
- `bloqueador-cliente` (cuando dependa del cliente)
- `riesgo-alto` / `riesgo-medio` (cuando aplique)
- `hito-facturacion-N` (asociado al hito de pago)
- `must-have` / `should-have` / `could-have` / `wont-have` (MoSCoW)

## PASO 3 — Pedir confirmación

**ANTES de crear cualquier issue**, pide al usuario confirmación explícita de la estructura propuesta. Pregunta:

- ¿Aprueba la estructura completa?
- ¿O prefiere ajustar algo antes?

## PASO 4 — Crear en Jira

Si el usuario confirma:

1. Crea las **Épicas** primero (necesitas sus keys para parentear HUs).
2. Crea las **HUs** parenteadas a su Épica correspondiente, con descripción completa que incluya:
   - Narrativa "Como X, quiero Y, para Z"
   - Criterios de aceptación Gherkin (Dado/Cuando/Entonces)
   - Reglas de negocio
   - Definition of Done
   - Estimación + prioridad MoSCoW
3. Crea las **Subtareas** parenteadas a su HU.
4. Aplica labels en cada creación (en `additional_fields`).

## PASO 5 — Validación final

1. Ejecuta query JQL: `project = <KEY> ORDER BY created ASC`
2. Confirma conteo: # Épicas + # HUs + # Subtareas
3. Reporta al usuario:
   - URL del board
   - Total de issues creados
   - Resumen por épica

## Nomenclatura obligatoria de títulos

- Épica: `[EPIC][Módulo] Nombre del entregable`
- HU: `[HU][S<N>] Como <rol>, quiero <acción>, para <objetivo>`
- Subtarea: `[<TIPO>] Descripción corta` (ej: `[H-01] Out-of-date Version (jQuery)`)

## Custom fields recomendados (trazabilidad comercial)

Si el proyecto los tiene configurados:
- `ID Propuesta`
- `Hito de Facturación`
- `% Avance`
- `Responsable Cliente`
