# Plugin: analista-scrum-mobiik

> Agente Analista Scrum Senior + identidad visual Mobiik para Claude Code.

Convierte propuestas comerciales en proyectos ejecutables completos: análisis de alcance, RAID Log, plan de trabajo en Excel, estructura en Jira, documento formal de Historias de Usuario y PPT de kickoff. Además asiste en la relación con el cliente: cartas de cierre, minutas de reunión, estrategias de negociación y presentaciones de estatus. Todo en español, con estándar visual corporativo de Mobiik aplicado.

## ¿Qué contiene este plugin?

### 1 Agente

- **`analista-scrum-senior`** — Subagente especializado en delivery híbrido pre-venta. Habla español, conoce el flujo de Mobiik, sigue las reglas de identidad visual.
  - **Invocación:** el equipo lo convoca con **`@scrummobiik`** (alias acordado; nombre técnico `analista-scrum-senior`).

### 2 Skills

- **`mobiik-branding`** — Paleta de colores oficial (`#AADC1E`), tipografía (Arial Black / Calibri), slogan ("coding for the future") y reglas de estilo cross-format (Excel/Word/PPT).
- **`mobiik-scrum-templates`** — 8 scripts Python listos para generar entregables con identidad visual aplicada: RAID Log Excel, Plan de Trabajo Excel, Documento de HUs Word, PPT de Kickoff, Carta de Cierre Word, Minuta Word, Guía de Negociación Word y PPT de Estatus. Incluye el **Protocolo de Negociación** del agente.

### 10 Comandos Slash

| Comando | Qué hace |
|---|---|
| `/analizar-propuesta` | Lee una propuesta comercial y extrae alcance + riesgos preliminares |
| `/generar-raid` | Genera RAID Log en Excel con dashboard |
| `/generar-plan-excel` | Genera Plan de Trabajo (WBS, Gantt, sprints, recursos, hitos) |
| `/setup-jira` | Propone y crea estructura completa en Jira |
| `/generar-hu-docx` | Genera documento Word formal de Historias de Usuario para sign-off |
| `/generar-kickoff-pptx` | Genera PPT de Kickoff (10 slides) |
| `/generar-carta-cierre` | Redacta una Carta de Cierre formal (proyecto/fase/entregable) |
| `/generar-minuta` | Genera una Minuta de Reunión desde transcripción o notas |
| `/negociar` | Entrega estrategias de negociación / resolución de conflictos |
| `/generar-estatus-pptx` | Genera la Presentación de Estatus ejecutiva (4 slides) |

## Estándar Jira incluido

El agente conoce la nomenclatura estándar Mobiik:

```
Proyecto:   [CLIENTE]-[ABREV]      (ej: TEC-PRESEL)
Épica:      [EPIC][Módulo] Nombre
HU:         [HU][S<N>] Como X, quiero Y, para Z
Subtarea:   [TASK][Disciplina] Acción
```

Y los labels obligatorios:
- `cliente-<nombre>`, `sprint-N`, `tipo-<categoria>`
- `bloqueador-cliente`, `riesgo-alto/medio`
- `hito-facturacion-N`, `must-have/should-have/could-have/wont-have`

## Cómo usar el agente

Tras instalar el plugin (ver [INSTALACION.md](../docs/INSTALACION.md)):

```
@analista-scrum-senior tengo una propuesta nueva en ~/Downloads/SOW-cliente.docx, 
analízala y prepárame el RAID Log
```

O bien usa los comandos directamente:

```
/analizar-propuesta ~/Downloads/SOW-cliente.docx
/generar-raid
/generar-plan-excel
/setup-jira NUEVO-PROY
/generar-hu-docx
/generar-kickoff-pptx
/generar-carta-cierre
/generar-minuta
/negociar
/generar-estatus-pptx
```

## Requisitos

- Claude Code instalado
- Python 3.9+ con: `python-pptx`, `openpyxl`, `python-docx`
- (Opcional) MCP de Atlassian configurado para el comando `/setup-jira`
- (Opcional) Microsoft PowerPoint / LibreOffice para validar PPTs visualmente

## Documentación adicional

- [Guía de uso completa para Scrums Mobiik](../docs/GUIA-DE-USO.md)
- [Estándar visual Mobiik](../docs/ESTANDAR-VISUAL-MOBIIK.md)
- [Guía de instalación](../docs/INSTALACION.md)

## Versión

v1.1.0 — Añade 4 habilidades de relación con el cliente (cartas de cierre, minutas, negociación, estatus), 4 scripts Python y 4 comandos slash. Ver [CHANGELOG](../CHANGELOG.md).

v1.0.0 — Versión inicial. Construida con base en el proyecto real "Migración TecMilenio Preselección".
