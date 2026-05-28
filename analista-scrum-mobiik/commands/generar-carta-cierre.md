---
description: Redacta una Carta de Cierre formal (proyecto, fase o entregable) con identidad visual Mobiik
---

Genera una **Carta de Cierre** formal para el cliente, que formaliza la conclusión y aceptación de entregables.

## Proceso

1. **Confirma el tipo de cierre**: ¿proyecto completo, fase o entregable específico?

2. **Valida que tengas los datos**. Si faltan, pídelos antes de continuar:
   - Destinatario (nombre, cargo, empresa/área)
   - Nombre del proyecto y cliente
   - Periodo de ejecución (inicio – fin)
   - Patrocinador / contacto y número de contrato u OC
   - Objetivos alcanzados (3–5)
   - Entregables aceptados (con fecha de entrega)
   - Pendientes / observaciones (garantía, soporte post-implementación, o "Ninguno")
   - Firmantes por Mobiik y por el cliente

   > **No inventes datos.** Si algo es ambiguo, márcalo y pregunta.

3. **Decide el formato de salida** según lo solicitado:
   - **Texto** (para correo o revisión rápida): redáctala directamente con tono cordial y *relationship-forward*.
   - **Word (.docx)**: usa el script `mobiik-scrum-templates/scripts/build_carta_cierre_docx.py`.

4. Si es Word: **personaliza la sección de datos** del script y ejecútalo:

   ```bash
   pip3 install --user python-docx   # una sola vez
   python3 scripts/build_carta_cierre_docx.py
   ```

   Guarda en `./entregables/Carta de Cierre - <proyecto>.docx`.

5. **Valida visualmente** (opcional): abre el archivo y verifica branding, datos correctos y que no queden placeholders `[...]`.

6. **Reporta el resultado** al usuario.

## Estructura de la carta

1. Encabezado formal (lugar y fecha)
2. Destinatario y saludo cordial
3. Párrafo de constancia del cierre
4. Datos generales (tabla)
5. Objetivos alcanzados
6. Entregables aceptados (tabla)
7. Asuntos pendientes / observaciones
8. Declaración de cierre + agradecimiento + disposición a futuro
9. Firmas (Mobiik y cliente)

## Reglas

- Tono **cordial, formal y relationship-forward** (agradece y deja abierta la colaboración futura).
- Aplica identidad visual Mobiik (skill `mobiik-branding`): acento verde lima `#AADC1E`, tablas branded.
- No inventes objetivos ni entregables: confírmalos con el usuario.
