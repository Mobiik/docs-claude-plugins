# Architecture — `docs-claude-plugins`

> Repositorio de plugins de Mobiik para Claude Code. Funciona simultáneamente como **marketplace** (catálogo de plugins) y como **monorepo** (contiene el código de los plugins).

---

## 1. Visión

**¿Qué problema resuelve este sistema?**

Estandariza el uso de Claude Code en el equipo de Scrums de Mobiik proporcionando un **agente Analista Scrum Senior** especializado en el flujo de delivery Mobiik, junto con plantillas, skills y comandos para acelerar la generación de entregables (Excel, Word, PPT, Jira) con identidad visual corporativa aplicada.

**¿Para qué usuario / equipo?**

- **Primario**: Scrum Masters y Analistas Scrum de Mobiik que gestionan proyectos pre-venta y delivery
- **Secundario**: Cualquier rol en Mobiik que necesite generar documentación de proyectos con identidad visual corporativa

**¿Qué lo diferencia de alternativas?**

- Habla **español** (la mayoría de plugins son en inglés)
- Está **especializado** en el flujo Mobiik (no es genérico Scrum)
- Aplica **identidad visual corporativa** automáticamente
- Conoce el **estándar Jira** Mobiik (nomenclatura, labels, dashboards)
- Validado en proyecto real (TecMilenio Preselección)

---

## 2. Stack tecnológico

| Capa | Tecnología | Versión |
|---|---|---|
| Plataforma | Claude Code | latest |
| Lenguaje de plantillas | Python | 3.9+ |
| Generación de PPT | python-pptx | ≥0.6 |
| Generación de Excel | openpyxl | ≥3.1 |
| Generación de Word | python-docx | ≥1.0 |
| Integración | MCP Atlassian | (opcional) |
| Formato de manifest | JSON | — |
| Documentación | Markdown | CommonMark |

---

## 3. Diagrama de componentes

```
                    ┌─────────────────────────────────────────┐
                    │       Mobiik/docs-claude-plugins         │
                    │      (Repositorio + Marketplace)         │
                    └─────────────────────────────────────────┘
                                       │
                       ┌───────────────┴───────────────┐
                       ▼                                ▼
              ┌──────────────────┐           ┌──────────────────┐
              │ .claude-plugin/  │           │ analista-scrum-  │
              │ marketplace.json │           │     mobiik/      │
              │  (catálogo)      │           │   (el plugin)    │
              └──────────────────┘           └──────────────────┘
                                                       │
                          ┌────────────────────────────┼─────────────────────┐
                          ▼                            ▼                     ▼
                  ┌──────────────┐            ┌──────────────┐       ┌──────────────┐
                  │   agents/    │            │   skills/    │       │  commands/   │
                  │              │            │              │       │              │
                  │ • analista-  │            │ • mobiik-    │       │ • analizar-  │
                  │   scrum-     │            │   branding   │       │   propuesta  │
                  │   senior     │            │ • mobiik-    │       │ • generar-*  │
                  │              │            │   scrum-     │       │ • setup-jira │
                  │              │            │   templates  │       │              │
                  └──────────────┘            └──────────────┘       └──────────────┘
                                                       │
                                                       ▼
                                              ┌──────────────┐
                                              │   scripts/   │
                                              │ Python que   │
                                              │ generan los  │
                                              │ entregables  │
                                              └──────────────┘
```

---

## 4. Componentes principales

| Componente | Responsabilidad | Tecnología | Owner |
|---|---|---|---|
| `marketplace.json` | Catálogo del marketplace para `/plugin marketplace add` | JSON | Mobiik Scrum |
| `plugin.json` | Manifest del plugin (nombre, versión, autor) | JSON | Mobiik Scrum |
| `analista-scrum-senior.md` | Agente subagent con system prompt completo | Markdown + YAML frontmatter | Mobiik Scrum |
| `mobiik-branding/SKILL.md` | Paleta, tipografía y reglas visuales | Markdown | Mobiik Scrum |
| `mobiik-scrum-templates/` | Scripts Python generadores de entregables | Python | Mobiik Scrum |
| `commands/*.md` | Comandos slash invocables | Markdown + YAML | Mobiik Scrum |

---

## 5. Flujos de datos clave

### Flujo 1: Instalación del plugin por un usuario

1. Usuario ejecuta `/plugin marketplace add Mobiik/docs-claude-plugins` en Claude Code
2. Claude Code lee `.claude-plugin/marketplace.json` del repo
3. Usuario ejecuta `/plugin install analista-scrum-mobiik@mobiik`
4. Claude Code descarga el subdirectorio `analista-scrum-mobiik/`
5. Claude Code registra:
   - El agente en su lista de subagentes (`@analista-scrum-senior`)
   - Las skills en su catálogo de skills
   - Los comandos en el menú de slash commands
6. Plugin disponible en todos los proyectos del usuario

### Flujo 2: Usuario genera un entregable

1. Usuario abre propuesta comercial en su proyecto
2. Ejecuta `/analizar-propuesta SOW.docx`
3. Comando invoca al agente con el contexto de la propuesta
4. Agente lee el archivo, extrae alcance, identifica riesgos
5. Usuario ejecuta `/generar-kickoff-pptx`
6. Comando referencia script en `skills/mobiik-scrum-templates/scripts/`
7. Agente personaliza el script con datos del proyecto
8. Ejecuta `python3 build_kickoff_pptx.py`
9. PPT generado en `./entregables/`

---

## 6. Integraciones externas

| Sistema | Propósito | Protocolo | Auth |
|---|---|---|---|
| GitHub | Hosting del repo + marketplace remoto | HTTPS / Git | OAuth (Claude Code) o credenciales del usuario |
| Atlassian Jira | Comando `/setup-jira` para crear estructura | REST API vía MCP | OAuth o API token |
| Atlassian Confluence | (Futuro) documentación cross-team | REST API vía MCP | OAuth |

---

## 7. Almacenamiento y persistencia

- **¿Qué datos persiste el sistema?** Ninguno. El plugin es stateless — toda la configuración y datos viven en el repo Git.
- **¿Dónde?** Solo en el filesystem del usuario (cuando instalan) y en GitHub (canonical).
- **Backup / retention policy:** Git history en GitHub. Tags para releases.
- **Encryption at rest / in transit:** GitHub maneja TLS y storage encryption. No hay secretos en el repo.

---

## 8. Decisiones de diseño (ADRs)

| ADR | Decisión | Status | Trade-off |
|---|---|---|---|
| 0001 | Repo público vs privado | Accepted (público) | Mayor difusión vs. control de IP. Decisión: la identidad visual no es secreto comercial. |
| 0002 | Marketplace + plugin en mismo repo | Accepted | Simplicidad vs. flexibilidad multi-plugin. Decisión: simplicidad gana para v1. |
| 0003 | Python para generación de archivos | Accepted | vs. Node.js. Decisión: Python tiene mejores librerías para Office docs. |
| 0004 | Español como idioma principal | Accepted | vs. inglés. Decisión: usuario target es Mobiik LATAM. |

---

## 9. Quality Gates aplicado a este repo

Este repo está protegido por el sistema **Quality Gates org-wide** de Mobiik.

### Stages base (siempre activos)

1. ✅ **pre-flight** — Conventional Commits, file size <5MB, lang detect
2. ✅ **secrets-scan** — Gitleaks + TruffleHog (verified)
3. ✅ **lint-format** — Auto-detect (Markdown lint, Python lint)
4. ✅ **sast** — Semgrep + CodeQL (security-extended)
5. ✅ **sca** — Trivy fs + Dependabot HIGH+ alerts API
6. ⚠️ **tests-coverage** — No aplica (plugin sin tests automatizados aún)
7. ⏭️ **sonarqube-gate** — **Opt-out** (skip elegante). Ver ADR 0005 abajo.
8. ✅ **build** — Validación de JSON schema (marketplace.json, plugin.json)
9. ✅ **quality-gate-result** — Aggregator final

> **ADR 0005 — Opt-out de SonarCloud.** Este repo es un monorepo de plugins (Markdown + scripts Python de plantillas) sin carpetas `src/`/`tests/` ni suite de pruebas automatizadas, por lo que el análisis de SonarCloud no aporta valor. Se eliminó `sonar-project.properties`; el stage 7 hace *skip* elegante vía `hashFiles` (el archivo era un skeleton con placeholders `PLEASE_REPLACE_*` que hacía fallar el gate a propósito). Los demás gates de seguridad y calidad (secrets-scan, SAST/CodeQL, SCA, build) siguen activos. Si en el futuro se agregan tests o se quiere cobertura Sonar, registrar el proyecto en SonarCloud (org `mobiik`), agregar el secret `SONAR_TOKEN` y recrear `sonar-project.properties` con `projectKey`/`projectName` reales y `sonar.sources` apuntando a los scripts.

### Stages auto-activos según contenido del repo

| Stage | Se activa si | Cubre |
|---|---|---|
| 🔵 **OSV-Scanner** | siempre | Vulns complementarias a Trivy |

### Dependabot

Cubre: `pip` (las dependencias Python de los scripts).

---

## 10. Cómo monitorear este sistema

- **Logs:** N/A (plugin estático)
- **Métricas:** Adoption del plugin medible por:
  - Estrellas / forks del repo
  - Issues abiertos
  - Feedback directo del equipo de Scrums Mobiik
- **Alertas:** Notificaciones de issues en GitHub
- **Health checks:** Validación manual de instalación en cada release

---

## 11. Cómo correr local

```bash
# Clonar el repo
git clone https://github.com/Mobiik/docs-claude-plugins.git
cd docs-claude-plugins

# Instalar dependencias de los scripts Python
pip3 install --user python-pptx openpyxl python-docx

# Probar localmente en Claude Code
# Abrir Claude Code y ejecutar:
#   /plugin marketplace add ./
#   /plugin install analista-scrum-mobiik@mobiik

# Validar JSON schemas
python3 -c "import json; json.load(open('.claude-plugin/marketplace.json'))"
python3 -c "import json; json.load(open('analista-scrum-mobiik/.claude-plugin/plugin.json'))"
```

Ver [`README.md`](../README.md) para guía completa.
