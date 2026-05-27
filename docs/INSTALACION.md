# Guía de Instalación — Plugin Analista Scrum Mobiik

Esta guía explica paso a paso cómo instalar el plugin en tu Claude Code.

> ⏱️ Tiempo estimado: **3 minutos**.

---

## Requisitos previos

Antes de instalar, asegúrate de tener:

- ✅ **Claude Code instalado** ([descargar aquí](https://claude.com/claude-code))
- ✅ **Python 3.9 o superior** instalado en tu Mac/PC
- ✅ Acceso al repo `Mobiik/docs-claude-plugins` (público)

### Verificar Python

Abre la terminal y ejecuta:

```bash
python3 --version
```

Debe responder con `Python 3.9.x` o superior. Si no tienes Python:
- **macOS**: ya viene instalado por defecto
- **Windows**: descarga desde [python.org](https://www.python.org/downloads/)
- **Linux**: `sudo apt install python3` o `sudo yum install python3`

### Instalar las librerías Python necesarias

```bash
pip3 install --user python-pptx openpyxl python-docx
```

> Si te dice que `pip3` no existe, intenta `pip install --user python-pptx openpyxl python-docx`

---

## Instalación del plugin — 2 caminos

### 🟢 Camino A — Marketplace remoto (recomendado, más simple)

Es el camino más limpio. Claude Code se encarga de descargar y mantener actualizado el plugin.

1. Abre Claude Code.
2. En la barra de comandos (`/`), escribe:

```
/plugin marketplace add Mobiik/docs-claude-plugins
```

3. Cuando termine, escribe:

```
/plugin install analista-scrum-mobiik@mobiik
```

4. **Listo.** El plugin está activo en TODOS tus proyectos de Claude Code.

### 🟡 Camino B — Clone local + marketplace local

Si prefieres tener el repo físico en tu máquina (más control):

1. Abre la terminal:

```bash
cd ~
git clone https://github.com/Mobiik/docs-claude-plugins.git
```

2. En Claude Code, ejecuta:

```
/plugin marketplace add ~/docs-claude-plugins
/plugin install analista-scrum-mobiik@mobiik
```

3. **Listo.** Para actualizar después: `cd ~/docs-claude-plugins && git pull`

---

## Verificar que funcionó

Después de instalar, prueba lo siguiente en cualquier proyecto:

### 1. ¿El agente está disponible?

Escribe `@` en la barra de Claude Code. Debe aparecer **`analista-scrum-senior`** en la lista de agentes.

### 2. ¿Los comandos slash funcionan?

Escribe `/` en la barra. Deberías ver:

- `/analizar-propuesta`
- `/generar-raid`
- `/generar-plan-excel`
- `/setup-jira`
- `/generar-hu-docx`
- `/generar-kickoff-pptx`

### 3. ¿Las skills están cargadas?

Pregúntale a Claude Code:

> "¿Cuál es la paleta de colores oficial de Mobiik?"

Debería responder con `#AADC1E` (verde lima), `#0A0A0A` (fondo oscuro), etc. — eso significa que la skill `mobiik-branding` está activa.

---

## Actualizaciones

Cuando se libere una nueva versión:

```
/plugin marketplace update mobiik
```

Si usaste el Camino B (clone local):

```bash
cd ~/docs-claude-plugins
git pull
```

Y en Claude Code:

```
/plugin marketplace update mobiik
```

---

## Desinstalar

Si quieres remover el plugin:

```
/plugin uninstall analista-scrum-mobiik@mobiik
```

Y si también quieres remover el marketplace:

```
/plugin marketplace remove mobiik
```

---

## Troubleshooting

### "Marketplace not found"

Verifica que escribiste el nombre correcto:
```
/plugin marketplace add Mobiik/docs-claude-plugins
```

Es **`Mobiik`** con M mayúscula (es el nombre de la organización en GitHub).

### "Permission denied" en git clone

Si el repo está privado y no tienes acceso, pide a tu Lead Scrum que te agregue a la organización Mobiik en GitHub.

### Los comandos slash no aparecen

1. Cierra y abre Claude Code.
2. Ejecuta `/plugin` para ver plugins instalados — debe aparecer `analista-scrum-mobiik`.
3. Si no aparece, ejecuta de nuevo `/plugin install analista-scrum-mobiik@mobiik`.

### Los scripts Python fallan al ejecutar

Asegúrate de haber instalado las dependencias:

```bash
pip3 install --user python-pptx openpyxl python-docx
```

Si te dice "ModuleNotFoundError: No module named 'X'", instala esa librería específica:

```bash
pip3 install --user X
```

### El comando /setup-jira no funciona

Necesitas tener configurado el **MCP de Atlassian** en Claude Code. Pregunta a tu Lead Scrum o consulta la [documentación de Anthropic sobre MCP](https://docs.claude.com/en/docs/claude-code/mcp).

---

## Necesitas ayuda

- 📧 Contacta al equipo de Scrums de Mobiik
- 🐛 Abre un issue en https://github.com/Mobiik/docs-claude-plugins/issues
- 📖 Lee la [Guía de Uso completa](./GUIA-DE-USO.md)
