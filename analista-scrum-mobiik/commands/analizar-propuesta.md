---
description: Analiza una propuesta comercial (SOW/PDF/DOCX) y genera análisis de alcance + RAID Log preliminar
argument-hint: <ruta a la propuesta comercial>
---

Analiza la propuesta comercial proporcionada siguiendo el flujo del agente Analista Scrum Senior de Mobiik:

**Propuesta a analizar:** $ARGUMENTS

## PASO 1 — ANÁLISIS

Lee el documento y extrae:

1. **Información comercial**
   - Cliente
   - Proveedor
   - Fecha de propuesta
   - Inversión total y desglose de hitos
   - Duración / cronograma propuesto

2. **Alcance funcional**
   - Lista detallada de entregables
   - Hitos contractuales
   - Criterios de aceptación

3. **Equipo propuesto**
   - Roles Mobiik (Scrum Master, Devs, DevOps, QA, etc.)
   - Roles esperados del cliente

4. **Supuestos contractuales**
   - Qué se asume del cliente
   - Restricciones técnicas
   - Garantías

5. **Fuera de alcance**
   - Lista explícita
   - Áreas grises potenciales

6. **Términos legales relevantes**
   - Confidencialidad
   - Propiedad intelectual
   - Limitación de responsabilidad
   - Penalizaciones por dependencias

## PASO 2 — RAID PRELIMINAR

Identifica de forma preliminar:

- **Riesgos** (mínimo 5, con probabilidad × impacto × severidad)
- **Supuestos** (todos los explícitos + los implícitos detectados)
- **Dependencias del cliente** (con criticidad y sprint donde se requieren)

## ENTREGABLE DE ESTE PASO

Presenta el análisis en formato estructurado en pantalla. **NO generes archivos todavía** — eso es responsabilidad de los siguientes comandos (`/generar-raid`, `/generar-plan-excel`, etc.).

Si detectas ambigüedades o gaps en la propuesta, **listalos como preguntas para el cliente** antes de avanzar.

Al final, pregunta al usuario:
- ¿Procedemos a generar el RAID Log en Excel? (usa `/generar-raid`)
- ¿Procedemos a generar el Plan de Trabajo? (usa `/generar-plan-excel`)
- ¿Procedemos a proponer la estructura de Jira? (usa `/setup-jira`)
