---
description: Genera el documento Word formal de Historias de Usuario entregable al cliente con sign-off
---

Genera el **Documento de Historias de Usuario en Word** — entregable formal al cliente.

## Proceso

1. **Valida que tengas las HUs definidas**, ya sea:
   - En el backlog de Jira del proyecto (usa MCP Atlassian para leerlas)
   - O en información que el usuario ya te proporcionó

2. **Carga el script**: `mobiik-scrum-templates/scripts/build_hu_docx.py`

3. **Personaliza la sección de datos**:
   - Cliente, proyecto, fecha, versión
   - Lista de épicas (con su key de Jira si aplica)
   - Lista completa de HUs por épica con:
     - ID (key Jira)
     - Summary (formato "Como X, quiero Y")
     - Propósito (el "para Z")
     - Criterios de aceptación Gherkin
     - Reglas de negocio
     - Definition of Done
     - Prioridad MoSCoW + estimación + sprint

4. **Estructura del documento** (11 secciones):
   1. Introducción y propósito
   2. Audiencia
   3. Glosario
   4. Actores del sistema
   5. Mapa de Épicas
   6. Historias de Usuario (cuerpo principal)
   7. Matriz de Trazabilidad Comercial ↔ Funcional
   8. Supuestos y Restricciones
   9. Fuera de Alcance
   10. Anexos
   11. Aceptación y Sign-off (firmas)

5. **Ejecuta el script** y guarda en `./entregables/Historias de Usuario - <proyecto>.docx`.

6. **Reporta resultado** con:
   - Ruta del archivo
   - Total de HUs documentadas
   - Páginas estimadas

## Reglas del agente

- Aplica identidad visual Mobiik:
  - Portada con fondo oscuro `#0A0A0A` y acento verde lima `#AADC1E`
  - Headers con barra lateral verde lima (NO líneas debajo)
  - Tablas con header `#252525` blanco y filas alternas
  - Pie con slogan "Mobiik | coding for the future | Confidencial"
- Cada HU sigue el criterio INVEST
- Cada HU referencia su key de Jira para trazabilidad
- Cada HU tiene Gherkin formal (Dado/Cuando/Entonces)
- Documento listo para sign-off del cliente con firmas
