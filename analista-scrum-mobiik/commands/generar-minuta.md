---
description: Genera una Minuta de Reunión a partir de transcripciones o notas, con identidad visual Mobiik
---

Genera una **Minuta de Reunión** (acta de seguimiento) a partir de la transcripción, notas o resumen que te proporcione el usuario.

## Proceso

1. **Recibe el insumo**: transcripción, notas crudas o bullets de la sesión.

2. **Parafrasea, NO transcribas**. Resume cada tema en su punto y conclusión. Nunca copies literal la conversación.

3. **Valida los datos generales**. Si faltan, pregúntalos:
   - Proyecto y cliente
   - Fecha, hora y lugar/medio (Teams / presencial)
   - Quién elabora la minuta
   - Objetivo de la reunión
   - Asistentes (nombre / rol / organización)

4. **Estructura el contenido**:
   - Temas tratados (resumidos)
   - Acuerdos y decisiones
   - **Tabla de compromisos**: acción / responsable / fecha compromiso / estatus
   - Pendientes para la próxima sesión
   - Riesgos o bloqueos detectados
   - Próxima reunión (fecha y temas)

5. **Marca lo ambiguo con `[POR CONFIRMAR]`** donde la información no sea clara (responsables, fechas, decisiones a medias). No rellenes con suposiciones.

6. **Decide el formato de salida**:
   - **Texto / Markdown**: para revisión o correo, redáctala directamente.
   - **Word (.docx)**: usa `mobiik-scrum-templates/scripts/build_minuta_docx.py`.

   ```bash
   pip3 install --user python-docx   # una sola vez
   python3 scripts/build_minuta_docx.py
   ```

   Guarda en `./entregables/Minuta - <proyecto> - <fecha>.docx`.

7. **Reporta el resultado** y resalta los compromisos con responsable y fecha.

## Reglas

- **Parafrasea**, nunca transcribas literal.
- Marca `[POR CONFIRMAR]` donde haya ambigüedad; el script lo resalta en naranja.
- No inventes responsables ni fechas: si no se dijeron, márcalos como pendientes de confirmar.
- Aplica identidad visual Mobiik (skill `mobiik-branding`).
- Sugiere de inmediato dar seguimiento a los compromisos en Jira (PL2 u otro proyecto).
