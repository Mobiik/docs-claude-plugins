# Scripts de Plantillas Mobiik Scrum

Estos 4 scripts Python generan los entregables principales del flujo Scrum Mobiik con identidad visual aplicada. Son **plantillas funcionales basadas en un proyecto real** (Migración TecMilenio Preselección) que sirven como punto de partida.

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
python3 build_kickoff_pptx.py    # → entregables/KO ... .pptx
python3 build_raid_xlsx.py        # → entregables/RAID Log ... .xlsx
python3 build_plan_xlsx.py        # → entregables/Plan de Trabajo ... .xlsx
python3 build_hu_docx.py          # → entregables/Historias de Usuario ... .docx
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

- Los scripts contienen datos del proyecto **TecMilenio Preselección** como ejemplo funcional. Reemplázalos por los datos de tu proyecto.
- La paleta y tipografía (Arial Black, `#AADC1E`) NO debe modificarse — es estándar corporativo.
- Si necesitas el manual completo de la identidad visual, consulta la skill `mobiik-branding`.
