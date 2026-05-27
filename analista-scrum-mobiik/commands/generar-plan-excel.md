---
description: Genera el Plan de Trabajo en Excel con WBS, Gantt, sprints, recursos e hitos (estándar Mobiik)
---

Genera el **Plan de Trabajo en Excel** para el proyecto actual.

## Proceso

1. **Valida que tengas los datos del proyecto**:
   - Cliente, Proyecto, fechas inicio/Go-Live
   - Inversión total y desglose de hitos de facturación
   - Duración del proyecto en sprints
   - Equipo asignado (nombre + rol + asignación por sprint)
   - Lista de épicas con cantidad de HUs por épica

2. **Carga el script**: `mobiik-scrum-templates/scripts/build_plan_xlsx.py`

3. **Personaliza la sección de datos**:
   - Información del proyecto (cliente, fechas, inversión)
   - WBS completo (jerarquía 1.0, 1.1, 2.0, etc.)
   - Asignación de actividades a sprints
   - Equipo y % de asignación
   - Hitos contractuales con fechas y montos
   - Tareas del Gantt con día de inicio/fin (1-15) y color (lima/rojo/naranja/azul)

4. **Valida la coherencia** antes de generar:
   - Suma de esfuerzo días = capacidad total
   - Cada actividad en Gantt tiene épica en WBS
   - Hitos de facturación cuadran con el contrato

5. **Ejecuta el script** y guarda en `./entregables/Plan de Trabajo - <proyecto>.xlsx`.

6. **Valida formulas Excel** (sin errores #REF!, #DIV/0!, #VALUE!).

7. **Reporta resultado** con:
   - Ruta del archivo
   - Total de actividades en WBS
   - Total de días-persona del proyecto
   - Sprints planificados

## Hojas generadas

1. Portada (con control de versiones)
2. Dashboard Ejecutivo (KPIs + avance por épica + hitos próximos)
3. WBS jerárquico
4. Cronograma tipo Gantt visual
5. Planificación por Sprint + velocity acumulado
6. Recursos y asignaciones
7. Hitos y entregables + esquema de pagos
8. RAID (link al archivo separado)

## Reglas del agente

- Identidad visual Mobiik aplicada en todas las hojas
- Gantt con barras coloreadas según semaforización
- Totales con fórmulas dinámicas (no hardcoded)
- Pie de página con slogan "coding for the future"
