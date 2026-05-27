---
description: Genera el PPT de Kickoff (10 slides) con identidad visual Mobiik
---

Genera el **PPT de Kickoff** para presentación al cliente en el inicio del proyecto.

## Proceso

1. **Valida datos clave del proyecto**:
   - Cliente, nombre del proyecto, fecha de inicio
   - Inversión total + esquema de pagos
   - Duración (sprints, días útiles)
   - Stack tecnológico
   - Equipo asignado (5 personas típico)
   - Lista de hallazgos / riesgos críticos si aplica
   - Dependencias del cliente con criticidad
   - Hitos / próximos pasos con fechas

2. **Carga el script**: `mobiik-scrum-templates/scripts/build_kickoff_pptx.py`

3. **Personaliza la sección de datos del proyecto**.

4. **Ejecuta el script** y guarda en `./entregables/KO - <proyecto>.pptx`.

5. **Valida visualmente** (opcional pero recomendado):
   - Abre el archivo en PowerPoint
   - Verifica que no haya texto cortado ni overflow
   - Verifica que números de sección (01, 02...) se vean completos
   - Verifica que el slogan esté en cada slide

6. **Reporta resultado** al usuario.

## Estructura del PPT (10 slides estándar)

| # | Slide | Contenido |
|---|---|---|
| 1 | **Portada** | Título, fechas, inversión, duración |
| 2 | **Agenda** | 6 secciones numeradas |
| 3 | **Contexto y Objetivo** | 4 pilares con iconos |
| 4 | **Alcance del Proyecto** | Grid 2×3 de bloques de alcance |
| 5 | **Arquitectura** | Componentes técnicos (cuando aplique) |
| 6 | **Plan de Trabajo** | 5 sprints en timeline + advertencia |
| 7 | **Dependencias del Cliente** | 8 deps con semaforización |
| 8 | **Equipo del Proyecto** | 5 roles + modelo de gobernanza |
| 9 | **Inversión y Entregables** | Stats + lista de entregables |
| 10 | **Próximos Pasos** | 6 hitos en timeline |

## Reglas de diseño

- Fondo `#0A0A0A` consistente
- Acento verde lima `#AADC1E` en titulares de sección
- Cards en `#181818` con accent bar lima a la izquierda
- Número de sección grande (`01`, `02`...) en verde lima top-right
- Footer: `© 2026 Mobiik   |   coding for the future`
- Tipografía: Arial Black (titulares) / Calibri (body)
- Semaforización: rojo `#FF4444` / naranja `#FFA040` / lima `#AADC1E` / azul `#1EA0DC`

## Validación post-generación

```bash
# Abrir en PowerPoint (macOS)
open "./entregables/KO - <proyecto>.pptx"
```

Revisa slide por slide y reporta si:
- Hay overflow de texto
- Algún número de sección está cortado
- Hay datos placeholder que olvidaste reemplazar
- Falta el slogan en alguna slide
