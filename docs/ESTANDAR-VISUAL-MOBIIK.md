# Estándar Visual Mobiik

> Referencia completa de la identidad visual corporativa Mobiik para aplicar consistentemente en todos los entregables.

## Paleta de colores oficial

### Colores primarios

| Rol | Hex | RGB | Cuándo usar |
|---|---|---|---|
| **Fondo base** | `#0A0A0A` | `10,10,10` | Background de portadas, slides, headers de Excel |
| **Fondo elevado** | `#181818` | `24,24,24` | Cards, paneles secundarios |
| **Superficie clara** | `#252525` | `37,37,37` | Headers de tabla, separadores |
| **Acento corporativo** ⭐ | `#AADC1E` | `170,220,30` | **Verde lima** — números grandes, KPIs, highlights, accent bars, totales |
| **Texto blanco** | `#FFFFFF` | `255,255,255` | Titulares y body sobre fondo oscuro |
| **Texto gris medio** | `#AAAAAA` | `170,170,170` | Captions, etiquetas, fechas |
| **Texto gris suave** | `#666666` | `102,102,102` | Pies de página, metadata |

### Colores de semaforización

| Severidad | Hex | RGB | Uso |
|---|---|---|---|
| 🔴 **Crítico** | `#FF4444` | `255,68,68` | Tags "CRÍTICO", riesgos altos, errores |
| 🟠 **Alerta** | `#FFA040` | `255,160,64` | Iconos ⚠️, advertencias |
| 🟢 **OK / Bajo** | `#AADC1E` | `170,220,30` | Estados exitosos, riesgos bajos |
| 🔵 **Informativo** | `#1EA0DC` | `30,160,220` | "INFORMATIVA", links, neutrales |

## Tipografía oficial

| Elemento | Fuente | Tamaño |
|---|---|---|
| **Titulares de portada** | Arial Black | 32-52 pt |
| **Titulares de sección** | Arial Black | 16-22 pt |
| **Subtítulos** | Arial Black | 13-15 pt |
| **Body** | Calibri | 10-12 pt |
| **Captions / leyendas** | Calibri | 9-10 pt |
| **Pies de página** | Calibri italic | 9 pt |

**Fallback:** Cuando Arial Black no esté disponible, usa **Arial Bold** como alternativa.

## Slogan corporativo

### Versión estándar
```
© 2026 Mobiik   |   coding for the future
```

### Versión extendida (documentos confidenciales)
```
© 2026 Mobiik   |   coding for the future   |   Confidencial
```

Aplicar al pie de cada slide, hoja de Excel y página de Word.

## Reglas de diseño cross-format

### ✅ SÍ hacer
- Fondo oscuro en portadas y slogan visible al pie
- Verde lima `#AADC1E` para destacar números, KPIs, totales
- **Barra accent verde a la izquierda** de headers (no líneas debajo del título)
- Tablas con header oscuro `#252525` y filas alternas `#F5F5F5` / `#FFFFFF`
- Logotipo Mobiik arriba-izquierda o en portada centrada
- Numeración grande de sección (`01`, `02`...) en verde lima
- Iconos en círculos con acento

### ❌ NO hacer
- **NUNCA** líneas decorativas debajo de titulares (hallmark de "AI generated")
- **NUNCA** centrar párrafos de body (solo titulares pueden centrarse)
- **NO** usar verde Office por defecto (`#70AD47`) — siempre `#AADC1E`
- **NO** mezclar bullets unicode con bullets numerados
- **NO** dejar tablas sin bordes ni headers diferenciados

## Aplicación por tipo de entregable

### Excel — Plan de Trabajo, RAID Log, Cronograma

- Header de hojas: `#0A0A0A` con texto blanco Arial bold
- Acento verde `#AADC1E` para totales, KPIs, hitos
- Semaforización en celdas según leyenda
- Gantt: barras verde lima sobre fondo claro
- Portada tipo "dashboard ejecutivo" con KPIs en cards oscuras

### PowerPoint — Kickoff, Status, Cierre

- Fondo `#0A0A0A` consistente en todos los slides
- Numeración grande de sección en verde lima top-right
- Cards en `#181818` con accent bar lima a la izquierda
- Slogan en footer en gris `#666666`

### Word — HU, Memorias técnicas, Carta de cierre

- Portada con fondo oscuro full-bleed + título Arial Black blanco
- Headers H1/H2 con barra lateral verde lima `#AADC1E`
- Tablas con header `#252525` + texto blanco, filas alternas
- Control de versiones en tabla al inicio
- Pie de página: `Mobiik | coding for the future | Confidencial`

## Constantes Python (para scripts)

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

## ¿Cuándo NO aplica este estándar?

- Código fuente
- Archivos de configuración (JSON, YAML, .env)
- Scripts shell
- Documentos técnicos puramente internos

Este estándar aplica **exclusivamente** a entregables visuales destinados al cliente o al equipo.

---

© 2026 Mobiik · coding for the future
