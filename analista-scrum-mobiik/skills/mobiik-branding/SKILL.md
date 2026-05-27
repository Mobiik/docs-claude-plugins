---
name: mobiik-branding
description: Identidad visual corporativa Mobiik. Aplica esta skill cuando generes cualquier entregable (Excel, Word, PowerPoint, PDF) para un proyecto Mobiik y necesites la paleta de colores oficial, tipografía, slogan o reglas de estilo. Trigger por menciones de "Mobiik", "identidad visual", "branding", "portada corporativa", "estándar visual", "plantilla Mobiik".
---

# Identidad Visual Mobiik

Esta skill define el estándar visual corporativo de Mobiik para todos los entregables generados por Claude Code. Aplícala consistentemente en Excel, Word, PowerPoint, PDF y cualquier otro formato.

## Paleta de Colores Oficial

| Rol | Hex | RGB | Uso |
|---|---|---|---|
| **Fondo base** | `#0A0A0A` | `10,10,10` | Background de portadas, slides, headers de Excel |
| **Fondo elevado** | `#181818` | `24,24,24` | Cards, paneles secundarios |
| **Superficie clara** | `#252525` | `37,37,37` | Headers de tabla, separadores |
| **Acento primario** ⭐ | `#AADC1E` | `170,220,30` | Verde lima — números grandes, KPIs, highlights, accent bars |
| **Texto blanco** | `#FFFFFF` | `255,255,255` | Titulares y body sobre fondo oscuro |
| **Texto gris medio** | `#AAAAAA` | `170,170,170` | Captions, etiquetas, fechas |
| **Texto gris suave** | `#666666` | `102,102,102` | Pies de página, metadata |
| **Alerta** | `#FFA040` | `255,160,64` | Iconos ⚠️, advertencias amarillo-naranja |
| **Crítico** | `#FF4444` | `255,68,68` | Tags "CRÍTICO", riesgos altos, errores |
| **Info / Link** | `#1EA0DC` | `30,160,220` | Acentos azules, "INFORMATIVA", links secundarios |

## Tipografía Oficial

| Elemento | Fuente | Tamaño |
|---|---|---|
| **Titulares grandes** (portadas, slides) | Arial Black | 32-52pt |
| **Titulares de sección** | Arial Black | 16-22pt |
| **Body** | Calibri | 10-12pt |
| **Captions** | Calibri | 9-10pt |
| **Pies de página** | Calibri italic | 9pt |

Cuando Arial Black no esté disponible, usa **Arial Bold** como fallback.

## Slogan Corporativo

Siempre incluir al pie de cada entregable público:

```
© 2026 Mobiik   |   coding for the future
```

Variante extendida (documentos):

```
© 2026 Mobiik   |   coding for the future   |   Confidencial
```

## Reglas Transversales

### Sí hacer
- ✅ Aplicar fondo oscuro en portadas y dejar slogan visible al pie
- ✅ Usar verde lima `#AADC1E` para destacar números, KPIs, totales
- ✅ Barra accent verde a la izquierda de headers de sección (no líneas debajo)
- ✅ Tablas con header oscuro `#252525` y filas alternas `#F5F5F5` / `#FFFFFF`
- ✅ Logotipo Mobiik arriba-izquierda o en portada centrada
- ✅ Numeración grande de sección (`01`, `02`...) en verde lima como ancla visual
- ✅ Iconos en círculos con acento, no como dingbats sueltos

### No hacer
- ❌ NUNCA usar líneas debajo de titulares (es hallmark de "AI generated")
- ❌ NUNCA centrar párrafos de body (solo titulares pueden centrarse)
- ❌ NO usar verde Office por defecto (`#70AD47`) — siempre `#AADC1E`
- ❌ NO mezclar bullets unicode con bullets numerados
- ❌ NO dejar tablas sin bordes ni headers diferenciados

## Estándares por Tipo de Entregable

### Excel (Plan de Trabajo, RAID Log, Cronograma)

- Header de hojas: `#0A0A0A` con texto blanco Arial bold
- Acento verde `#AADC1E` para totales, KPIs, hitos
- Semaforización:
  - 🟢 OK / Bajo → `#AADC1E`
  - 🟡 Atención / Medio → `#FFA040`
  - 🔴 Crítico → `#FF4444`
  - 🔵 Informativo → `#1EA0DC`
- Gantt: barras verde lima `#AADC1E` sobre fondo claro; hitos en diamante negro
- Portada tipo "dashboard ejecutivo" con KPIs en cards oscuras

### PowerPoint (Kickoff, Status, Cierre)

- Fondo `#0A0A0A` consistente en todos los slides
- Numeración grande de sección en verde lima top-right (`01`, `02`...)
- Cards de contenido en `#181818` con accent bar lima a la izquierda
- Slogan en footer en gris `#666666`

### Word (HU, Memorias técnicas, Carta de cierre)

- Portada con fondo oscuro full-bleed + título Arial Black blanco + acento verde lima
- Headers H1/H2 con barra lateral verde lima `#AADC1E`
- Tablas con header `#252525` + texto blanco, filas alternas `#F5F5F5` / blanco
- Control de versiones en tabla al inicio
- Pie de página: `Mobiik | coding for the future | Confidencial`

## Constantes Reutilizables (Python)

Para scripts que generan archivos, usa estas constantes:

```python
# Brand palette
BG_DARK      = "#0A0A0A"
BG_PANEL     = "#181818"
BG_PANEL_LT  = "#252525"
LIME         = "#AADC1E"
WHITE        = "#FFFFFF"
GREY_TXT     = "#AAAAAA"
GREY_DIM     = "#666666"
ORANGE       = "#FFA040"
RED_CRIT     = "#FF4444"
BLUE_INFO    = "#1EA0DC"

# Typography
FONT_HEAD = "Arial Black"
FONT_BODY = "Calibri"

# Slogan
SLOGAN = "© 2026 Mobiik   |   coding for the future"
```

## Cuándo NO aplicar estos colores

Cuando estés generando código fuente, archivos de configuración, JSON, YAML, scripts shell o cualquier artefacto técnico interno — esta paleta NO aplica. Es exclusivamente para entregables visuales destinados al cliente o al equipo.
