---
name: mobiik-scrum-templates
description: Scripts Python listos para generar entregables Mobiik con identidad visual aplicada — Kickoff PPT, RAID Log Excel, Plan de Trabajo Excel y Documento de Historias de Usuario Word. Usa esta skill cuando necesites crear cualquiera de estos artefactos. Trigger por menciones de "kickoff PPT", "RAID Log", "plan de trabajo Excel", "historias de usuario Word", "generar entregable Mobiik", "plantilla scrum".
---

# Plantillas Scrum Mobiik — Generadores Automáticos

Esta skill contiene 4 scripts Python que generan los entregables principales del proceso de delivery Mobiik con la identidad visual ya aplicada.

## Scripts Disponibles

Todos los scripts están en `scripts/` dentro de esta skill:

| Script | Genera | Dependencia Python |
|---|---|---|
| `build_kickoff_pptx.py` | PPT de Kickoff (10 slides) | `python-pptx` |
| `build_raid_xlsx.py` | RAID Log con Dashboard | `openpyxl` |
| `build_plan_xlsx.py` | Plan de Trabajo (8 hojas) | `openpyxl` |
| `build_hu_docx.py` | Documento Word de HUs | `python-docx` |

## Cómo Usar Cada Script

### 1. Kickoff PPT

```bash
# Instalar dependencia (una sola vez)
pip3 install --user python-pptx

# Editar el script para llenar los datos del proyecto:
# - Cliente, Proyecto, Fecha, Inversión
# - Lista de hallazgos / riesgos
# - Equipo asignado
# - Cronograma por sprint

python3 scripts/build_kickoff_pptx.py
```

El script genera un PPT con:
- Portada con datos clave del proyecto
- Agenda en 6 secciones numeradas
- Contexto y objetivo con 4 pilares
- Alcance del proyecto (grid 2x3)
- Arquitectura (cuando aplique)
- Plan de trabajo / Cronograma
- Dependencias del cliente con semaforización
- Equipo del proyecto
- Inversión y entregables
- Próximos pasos / timeline

### 2. RAID Log Excel

```bash
pip3 install --user openpyxl
python3 scripts/build_raid_xlsx.py
```

Genera 6 hojas:
1. **Portada** — datos del proyecto, control de versiones, leyenda de semaforización
2. **Dashboard** — KPIs con fórmulas COUNTIF dinámicas
3. **Riesgos** — con probabilidad × impacto × severidad coloreada
4. **Supuestos** — con estado (Confirmado/Pendiente)
5. **Issues** — plantilla para llenar durante ejecución
6. **Dependencias** — internas y externas con criticidad

### 3. Plan de Trabajo Excel

```bash
python3 scripts/build_plan_xlsx.py
```

Genera 8 hojas:
1. **Portada** — datos del proyecto + control de versiones
2. **Dashboard** — KPIs, avance por épica con fórmulas, hitos próximos
3. **WBS** — Work Breakdown Structure jerárquico
4. **Cronograma** — Gantt visual coloreado por tipo de actividad
5. **Sprints** — planificación + velocity acumulado
6. **Recursos** — asignaciones por persona y sprint
7. **Hitos** — entregables contractuales + esquema de pagos
8. **RAID (link)** — enlace al archivo RAID separado

### 4. Documento Word de HUs

```bash
pip3 install --user python-docx
python3 scripts/build_hu_docx.py
```

Genera documento formal con:
- Portada con identidad visual Mobiik
- Control de versiones
- Índice (11 secciones)
- Introducción, Audiencia, Glosario, Actores
- Mapa de Épicas
- Cada HU con: ID Jira, Sprint, Prioridad MoSCoW, Estimación, Narrativa, Criterios de Aceptación Gherkin, Reglas de Negocio, DoD
- Matriz de Trazabilidad Comercial ↔ Funcional
- Supuestos, Restricciones, Fuera de Alcance
- Anexos
- Sign-off para ambas partes

## Personalización

Cada script tiene una sección de datos al inicio que debes editar para tu proyecto:

```python
# ─── DATOS DEL PROYECTO (editar) ─────────────────────────
CLIENTE   = "TuCliente"
PROYECTO  = "Migración X"
FECHA     = "Junio 2026"
INVERSION = "$XXX,XXX MXN"
SPRINTS   = 3
EQUIPO    = [
    ("Nombre", "Rol"),
    # ...
]
# ─────────────────────────────────────────────────────────
```

## Identidad Visual Aplicada

Los 4 scripts aplican automáticamente la paleta Mobiik definida en la skill `mobiik-branding`:

- Fondo oscuro `#0A0A0A`
- Acento verde lima `#AADC1E`
- Tipografía Arial Black (titulares) / Calibri (body)
- Slogan "coding for the future" en pie de página
- Semaforización estándar (rojo/naranja/lima/azul)

## Dependencias del Sistema

Para que los scripts corran, asegúrate de tener:

```bash
# Python 3.9+
python3 --version

# Librerías
pip3 install --user python-pptx openpyxl python-docx
```

En macOS Microsoft PowerPoint instalado permite renderizar el PPT a PDF/imagen para validación visual (via AppleScript).

## Validación Visual (Recomendado)

Después de generar un archivo, ábrelo en su aplicación nativa (PowerPoint, Excel, Word) para validar:

1. ✓ Branding aplicado correctamente (colores, tipografía, slogan)
2. ✓ Sin overflow de texto ni elementos cortados
3. ✓ Tablas con todas las filas/columnas correctas
4. ✓ Fórmulas Excel sin errores (#REF!, #DIV/0!, etc.)
5. ✓ Datos del proyecto correctos (no quedaron placeholders de TecMilenio o ejemplos)

## Trazabilidad

Los scripts están diseñados para integrarse con la **estructura Jira Mobiik** (`[CLIENTE]-[ABREV]`). Cada documento referencia el ID del proyecto Jira y mantiene trazabilidad bidireccional.
