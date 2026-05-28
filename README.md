# Mobiik · Claude Code Plugins

> Repositorio oficial de plugins de Mobiik para Claude Code. Funciona como **marketplace** y como repositorio clonable.

## Plugins disponibles

| Plugin | Descripción | Versión |
|---|---|---|
| **[analista-scrum-mobiik](./analista-scrum-mobiik/)** | Agente Analista Scrum Senior + identidad visual Mobiik + plantillas Excel/Word/PPT/Jira + cartas de cierre, minutas, negociación y estatus | 1.1.0 |

## Instalación rápida

### Opción A — Marketplace (recomendado, sin clone manual)

En Claude Code, ejecuta:

```
/plugin marketplace add Mobiik/docs-claude-plugins
/plugin install analista-scrum-mobiik@mobiik
```

Listo. El agente, las skills y los comandos slash quedan disponibles en **todos** tus proyectos automáticamente.

### Opción B — Clone local

```bash
git clone https://github.com/Mobiik/docs-claude-plugins.git ~/mobiik-claude-plugins
```

Luego en Claude Code:

```
/plugin marketplace add ~/mobiik-claude-plugins
/plugin install analista-scrum-mobiik@mobiik
```

Para más detalles consulta [docs/INSTALACION.md](./docs/INSTALACION.md).

## Estructura del repo

```
docs-claude-plugins/
├── .claude-plugin/
│   └── marketplace.json              ← Catálogo del marketplace
├── analista-scrum-mobiik/             ← Plugin principal
│   ├── .claude-plugin/
│   │   └── plugin.json
│   ├── agents/
│   │   └── analista-scrum-senior.md
│   ├── skills/
│   │   ├── mobiik-branding/
│   │   └── mobiik-scrum-templates/    ← 8 scripts Python (Excel/Word/PPT)
│   ├── commands/
│   │   ├── analizar-propuesta.md
│   │   ├── generar-raid.md
│   │   ├── generar-plan-excel.md
│   │   ├── setup-jira.md
│   │   ├── generar-hu-docx.md
│   │   ├── generar-kickoff-pptx.md
│   │   ├── generar-carta-cierre.md
│   │   ├── generar-minuta.md
│   │   ├── negociar.md
│   │   └── generar-estatus-pptx.md
│   └── README.md
├── docs/
│   ├── GUIA-DE-USO.md                 ← Guía completa para Scrums Mobiik
│   ├── INSTALACION.md                 ← Instrucciones paso a paso
│   ├── ESTANDAR-VISUAL-MOBIIK.md      ← Referencia de identidad visual
│   └── architecture.md
├── CHANGELOG.md
├── LICENSE
└── README.md (este archivo)
```

## Para Scrum Masters de Mobiik

Si eres parte del equipo de Scrums de Mobiik y quieres usar este agente en tu día a día:

1. **Lee la [Guía de Uso completa](./docs/GUIA-DE-USO.md)** — explica todo paso a paso
2. **Instala el plugin** con los comandos de arriba
3. **Prueba en un proyecto real** — ten una propuesta comercial lista
4. **Reporta feedback** abriendo un issue en este repo o contactando al equipo de Mobiik

## Para colaboradores

Si quieres contribuir mejoras al agente o agregar nuevos plugins:

1. Haz fork del repo
2. Crea una rama: `git checkout -b feature/mi-mejora`
3. Realiza tus cambios y haz pull request
4. Actualiza el `CHANGELOG.md`

## Licencia

MIT — ver [LICENSE](./LICENSE).

## Sobre Mobiik

Mobiik es una consultora especializada en transformación digital y delivery de proyectos de tecnología.

**coding for the future** · [mobiik.com](https://mobiik.com)
