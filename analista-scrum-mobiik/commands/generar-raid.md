---
description: Genera el archivo Excel del RAID Log (Riesgos, Supuestos, Issues, Dependencias) con identidad visual Mobiik
---

Genera el archivo **RAID Log en Excel** para el proyecto actual.

## Proceso

1. **Valida que tengas los datos del proyecto**. Si te faltan:
   - Cliente
   - Nombre del proyecto
   - Scrum Master asignado
   - Inversión y duración

   …pide al usuario que te los proporcione antes de continuar.

2. **Carga el script de plantilla**: `mobiik-scrum-templates/scripts/build_raid_xlsx.py`

3. **Personaliza la sección de datos del proyecto** en el script:
   - Reemplaza el ejemplo de TecMilenio Preselección con los datos reales
   - Ajusta la lista de Riesgos según el análisis previo (usa `/analizar-propuesta` primero si no lo has hecho)
   - Ajusta Supuestos extraídos de la propuesta
   - Ajusta Dependencias del cliente

4. **Confirma la lista de riesgos con el usuario** antes de generar el archivo. Muestra una tabla resumen:

   | ID | Riesgo | Categoría | Severidad |
   |---|---|---|---|
   | R-01 | ... | ... | ... |

5. **Ejecuta el script** y guarda el archivo en `./entregables/RAID Log - <proyecto>.xlsx`.

6. **Valida que no haya errores de fórmula** (#REF!, #DIV/0!, etc.) en el Dashboard.

7. **Reporta el resultado** al usuario con:
   - Ruta del archivo generado
   - Resumen: # riesgos, # supuestos, # dependencias críticas
   - Próximo paso sugerido

## Reglas del agente

- Aplica la identidad visual Mobiik (skill `mobiik-branding`)
- Semaforización estándar: rojo `#FF4444` / naranja `#FFA040` / lima `#AADC1E` / azul `#1EA0DC`
- Pie de página con slogan "coding for the future"
- Control de versiones al inicio del archivo
