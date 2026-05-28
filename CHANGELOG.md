# Changelog

Todos los cambios notables a este repositorio se documentan aquí.

El formato sigue [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/) y este proyecto adhiere a [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html).

---

## [1.1.0] — 2026-05-28

### Added

- **4 nuevas habilidades de relación con el cliente** en el plugin `analista-scrum-mobiik`:
  - **Cartas de cierre** — cartas formales de cierre (proyecto, fase o entregable) con tono cordial y *relationship-forward*.
  - **Minutas de reunión** — generación de minutas a partir de transcripciones/notas (parafraseadas), con tabla de acciones y marcado `[POR CONFIRMAR]`.
  - **Negociación y resolución de problemas** — protocolo que entrega replanteo por intereses, 2–3 estrategias diferenciadas y recomendación (método Harvard, BATNA, CNV).
  - **Presentación de estatus** — reporte ejecutivo en PPT (4 slides) con semáforo de salud, métricas de Jira, riesgos y próximos pasos.
- **4 scripts Python nuevos** en la skill `mobiik-scrum-templates/scripts/`:
  - `build_carta_cierre_docx.py` — Carta de Cierre (Word)
  - `build_minuta_docx.py` — Minuta de Reunión (Word)
  - `build_negociacion_docx.py` — Guía de Preparación de Negociación (Word)
  - `build_estatus_pptx.py` — Presentación de Estatus (PPT, 4 slides)
- **4 comandos slash nuevos**: `/generar-carta-cierre`, `/generar-minuta`, `/negociar`, `/generar-estatus-pptx`.
- **Protocolo de Negociación** documentado en la skill `mobiik-scrum-templates` (intereses, BATNA, estrategias diferenciadas).

### Changed

- Agente `analista-scrum-senior` ampliado con las 4 nuevas habilidades, reglas (no inventar, parafrasear, adaptar formato) y comandos.
- Skill `mobiik-scrum-templates` ahora documenta 8 generadores (antes 4).
- `plugin.json` y `marketplace.json` actualizados a **v1.1.0** con keywords ampliadas.
- Los entregables de estatus usan el footer corporativo "Mobiik — AI, Cloud & Software Development" y el logo partido MOB·IIK, conforme a la plantilla oficial.

---

## [1.0.0] — 2026-05-27

### Added

- **Plugin `analista-scrum-mobiik` v1.0.0** — primera versión publicada.
- **Agente `analista-scrum-senior`** con system prompt completo para flujo de delivery Mobiik (análisis → RAID → Plan Excel → Jira → HU Word → Kickoff PPT).
- **Skill `mobiik-branding`** con paleta corporativa, tipografía y reglas de identidad visual.
- **Skill `mobiik-scrum-templates`** con 4 scripts Python listos para generar entregables:
  - `build_kickoff_pptx.py` — PPT de Kickoff (10 slides)
  - `build_raid_xlsx.py` — RAID Log Excel con Dashboard
  - `build_plan_xlsx.py` — Plan de Trabajo Excel (8 hojas)
  - `build_hu_docx.py` — Documento Word de Historias de Usuario
- **6 comandos slash** para acelerar el flujo:
  - `/analizar-propuesta`, `/generar-raid`, `/generar-plan-excel`
  - `/setup-jira`, `/generar-hu-docx`, `/generar-kickoff-pptx`
- **Documentación completa en español** en `docs/`:
  - `INSTALACION.md` — guía paso a paso de instalación
  - `GUIA-DE-USO.md` — manual completo para Scrum Masters
  - `ESTANDAR-VISUAL-MOBIIK.md` — referencia de identidad visual corporativa
- **Marketplace catalog** en `.claude-plugin/marketplace.json` para instalación remota vía `/plugin marketplace add Mobiik/docs-claude-plugins`.
- Validado contra el proyecto real **Migración TecMilenio Preselección** (53 issues creados en Jira TEC26).

### Changed

- Inicializado bajo esqueleto Mobiik (`Mobiik/.github/scripts/new-repo-init.yml`).

---

## [Unreleased]

### Added
### Changed
### Deprecated
### Removed
### Fixed
### Security

---

## Convenciones

| Cambio | Bump SemVer |
|---|---|
| Breaking change en API pública | MAJOR (1.x.x → 2.0.0) |
| Nueva feature backward-compatible | MINOR (1.0.x → 1.1.0) |
| Bug fix backward-compatible | PATCH (1.0.0 → 1.0.1) |

## Procedimiento de release

```bash
# 1. Mergear cambios a main
# 2. Verificar que CI corre en verde (Quality Gates pipeline)
# 3. Bump en plugin.json y marketplace.json
# 4. Bump en este CHANGELOG (mover [Unreleased] → [v1.X.Y])
# 5. Tag firmado
git tag -s v1.X.Y -m "Release v1.X.Y"
git push origin v1.X.Y

# 6. Anuncio en Slack/Teams según política del proyecto
```

---

[1.1.0]: https://github.com/Mobiik/docs-claude-plugins/releases/tag/v1.1.0
[1.0.0]: https://github.com/Mobiik/docs-claude-plugins/releases/tag/v1.0.0
[Unreleased]: https://github.com/Mobiik/docs-claude-plugins/compare/v1.1.0...HEAD
