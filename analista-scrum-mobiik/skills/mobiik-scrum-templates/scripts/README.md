# Scripts de Plantillas Mobiik Scrum

Estos 8 scripts Python generan los entregables principales del flujo Scrum Mobiik y de la relación con el cliente, con identidad visual aplicada. Son **plantillas funcionales** que sirven como punto de partida; edita la sección de datos de cada una.

## Cómo personalizar para tu proyecto

Antes de correr cualquier script:

1. **Edita la sección de datos al inicio del script**: cliente, proyecto, fechas, montos, equipo, riesgos específicos.
2. **Crea la carpeta de salida**: `mkdir entregables` (los scripts escriben en `./entregables/`).
3. **Instala las dependencias** (una sola vez):
   ```bash
   pip3 install --user python-pptx openpyxl python-docx
   ```

## Ejecutar

```bash
# Desde el directorio donde quieras los entregables:
mkdir -p entregables

# Generar cada artefacto:
python3 build_kickoff_pptx.py       # → entregables/KO ... .pptx
python3 build_raid_xlsx.py           # → entregables/RAID Log ... .xlsx
python3 build_plan_xlsx.py           # → entregables/Plan de Trabajo ... .xlsx
python3 build_hu_docx.py             # → entregables/Historias de Usuario ... .docx
python3 build_carta_cierre_docx.py   # → entregables/Carta de Cierre ... .docx
python3 build_minuta_docx.py         # → entregables/Minuta ... .docx
python3 build_negociacion_docx.py    # → entregables/Preparacion Negociacion ... .docx
python3 build_estatus_pptx.py        # → entregables/Estatus ... .pptx
```

## Estructura de cada script

```
┌─ Header con imports
├─ CONSTANTES DE PALETA (no tocar — identidad Mobiik)
├─ HELPERS (no tocar — funciones de estilo)
├─ DATOS DEL PROYECTO  ← EDITAR AQUÍ
└─ GENERACIÓN (no tocar — lógica de armado)
```

## Validación recomendada después de generar

| Archivo | Cómo validar |
|---|---|
| PPT | Abrir en PowerPoint, revisar slide por slide |
| Excel | Abrir, verificar fórmulas (no `#REF!`, `#DIV/0!`) y semaforización |
| Word | Abrir, revisar portada, secciones y sign-off |

## Notas

- Los scripts de delivery (kickoff, RAID, plan, HU) contienen datos del proyecto **TecMilenio Preselección** como ejemplo funcional. Los scripts de relación con el cliente (carta de cierre, minuta, negociación, estatus) usan **placeholders `[...]`** listos para reemplazar.
- La paleta y tipografía (Arial Black, `#AADC1E`) NO debe modificarse — es estándar corporativo.
- El generador de estatus (`build_estatus_pptx.py`) usa el footer "Mobiik — AI, Cloud & Software Development" y el logo partido MOB·IIK, conforme a la plantilla oficial de estatus.
- Si necesitas el manual completo de la identidad visual, consulta la skill `mobiik-branding`.
