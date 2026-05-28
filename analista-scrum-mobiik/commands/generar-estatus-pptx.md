---
description: Genera la Presentación de Estatus de proyecto (4 slides) con datos de Jira e identidad visual Mobiik
---

Genera un **reporte ejecutivo de Estatus de Proyecto** como presentación (4 slides), alimentado con datos de Jira.

## Proceso

1. **Valida que tengas los datos del periodo**. Si faltan, pídelos u obténlos de Jira:
   - Proyecto, periodo (sprint / semana), PM responsable
   - **Salud general**: Verde (en tiempo) / Ámbar (en riesgo) / Rojo (desviado)
   - Resumen ejecutivo (2–3 líneas)
   - Métricas: total, completados, en progreso, por hacer, bloqueados
   - Avance global (%), velocidad del sprint (pts), sprint actual
   - Logros del periodo
   - Trabajo en progreso (clave / resumen / responsable / estado)
   - Riesgos y bloqueos (descripción / mitigación / responsable / severidad)
   - Próximos pasos
   - Decisiones / apoyos requeridos del cliente

   > Si tienes acceso a Jira, puedes obtener las métricas con JQL del sprint actual. **No inventes números**: confírmalos.

2. **Decide el formato de salida**:
   - **Texto / resumen ejecutivo**: redáctalo directamente con el semáforo y los KPIs.
   - **PowerPoint (.pptx)**: usa `mobiik-scrum-templates/scripts/build_estatus_pptx.py`.

3. Si es PPT: **personaliza la sección de datos** del script y ejecútalo:

   ```bash
   pip3 install --user python-pptx   # una sola vez
   python3 scripts/build_estatus_pptx.py
   ```

   Guarda en `./entregables/Estatus - <proyecto> - <periodo>.pptx`.

4. **Valida visualmente** (opcional): abre el archivo y verifica el semáforo, las métricas y que no queden placeholders `[...]`.

5. **Reporta el resultado** con el color del semáforo y el % de avance.

## Estructura (4 slides)

| # | Slide | Contenido |
|---|---|---|
| 1 | **Portada** | Logo MOB·IIK, proyecto/periodo/PM, semáforo de salud |
| 2 | **Resumen y métricas** | Resumen + 5 métricas + KPIs + logros del periodo |
| 3 | **Distribución y WIP** | Gráfica (placeholder) + tabla de trabajo en progreso |
| 4 | **Riesgos y decisiones** | Riesgos con severidad + próximos pasos + apoyos del cliente |

## Reglas de diseño

- Fondo `#0A0A0A`, acento verde lima `#AADC1E`, logo partido **MOB·IIK**.
- Footer corporativo: **"Mobiik — AI, Cloud & Software Development"** (este deliverable NO usa el slogan "coding for the future").
- Semáforo de salud: Verde `#AADC1E` / Ámbar `#FFA040` / Rojo `#FF4444`.
- Severidad de riesgos coloreada (alta=rojo, media=naranja, baja=lima).
- **No inventes métricas**: confírmalas con Jira o con el usuario.
