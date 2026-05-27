# Guía de Uso — Plugin Analista Scrum Mobiik

> Manual completo para los Scrum Masters de Mobiik.
> Aprende a usar el agente en tu día a día, desde la propuesta comercial hasta el cierre del proyecto.

---

## Tabla de contenido

1. [Qué hace este plugin](#1-qué-hace-este-plugin)
2. [Cuándo usarlo](#2-cuándo-usarlo)
3. [Tu primer proyecto con el agente — paso a paso](#3-tu-primer-proyecto-con-el-agente)
4. [Comandos disponibles y cuándo usarlos](#4-comandos-disponibles)
5. [Conversar con el agente directamente](#5-conversar-con-el-agente)
6. [Estándar visual Mobiik aplicado automáticamente](#6-estándar-visual-mobiik)
7. [Estándar Jira aplicado automáticamente](#7-estándar-jira)
8. [Buenas prácticas](#8-buenas-prácticas)
9. [Preguntas frecuentes](#9-preguntas-frecuentes)

---

## 1. Qué hace este plugin

Este plugin agrega a tu Claude Code un **agente Analista Scrum Senior especializado en delivery Mobiik**. Su misión es ayudarte a convertir cualquier propuesta comercial firmada en un proyecto ejecutable completo, en **minutos** en lugar de horas.

Cubre las **5 fases del flujo Mobiik**:

| Fase | Entregable | Tiempo manual | Con el agente |
|---|---|---|---|
| 1 | Análisis de alcance + RAID Log | 4-6 horas | 15-30 min |
| 2 | Plan de trabajo en Excel | 3-4 horas | 10 min |
| 3 | Estructura completa en Jira | 6-8 horas | 20 min |
| 4 | Documento Word de Historias de Usuario | 8-12 horas | 30 min |
| 5 | PPT de Kickoff | 2-3 horas | 10 min |

Todo con la **identidad visual de Mobiik aplicada** y el **estándar Jira estandarizado** entre proyectos.

---

## 2. Cuándo usarlo

✅ **Casos ideales:**

- Acabas de recibir una propuesta firmada y necesitas armar el proyecto
- Vas a un kickoff con cliente y necesitas el PPT
- Tienes que documentar HUs formalmente para sign-off del cliente
- Estás iniciando un proyecto en Jira y quieres seguir el estándar Mobiik
- Necesitas actualizar el RAID Log durante la ejecución

❌ **Casos donde NO ayuda mucho:**

- Refinement de HUs específicas con el cliente (mejor en vivo)
- Estimaciones técnicas detalladas (necesitas al Tech Lead)
- Decisiones políticas de alcance (eso es tu trabajo, no del agente)

---

## 3. Tu primer proyecto con el agente

Imagina que recibes una propuesta firmada para migrar un aplicativo a Azure. Vamos paso a paso.

### Paso 1: Coloca la propuesta en una carpeta del proyecto

```
~/proyectos/cliente-nuevo/
└── SOW-Migracion.docx
```

Abre Claude Code en esa carpeta.

### Paso 2: Análisis de la propuesta

Escribe:

```
/analizar-propuesta SOW-Migracion.docx
```

El agente leerá la propuesta y te entregará en pantalla:
- Cliente, proveedor, inversión, duración
- Alcance detallado, entregables, hitos
- Equipo propuesto
- Supuestos contractuales
- Lista preliminar de riesgos
- Dependencias del cliente
- **Preguntas que debes hacer al cliente** antes de comprometer

⏰ Tiempo: ~5 minutos.

### Paso 3: Generar RAID Log

Si el análisis te convence:

```
/generar-raid
```

El agente te confirmará los datos, te pedirá que valides la lista de riesgos, y generará el Excel.

Resultado:
```
./entregables/RAID Log - <proyecto>.xlsx
```

Con 6 hojas: Portada, Dashboard, Riesgos, Supuestos, Issues (vacío), Dependencias.

⏰ Tiempo: ~5 minutos.

### Paso 4: Generar el Plan de Trabajo Excel

```
/generar-plan-excel
```

El agente te pedirá datos faltantes (fechas, equipo, hitos de facturación) y generará el plan.

Resultado:
```
./entregables/Plan de Trabajo - <proyecto>.xlsx
```

Con 8 hojas: Portada, Dashboard, WBS, Gantt, Sprints, Recursos, Hitos, RAID link.

⏰ Tiempo: ~5 minutos.

### Paso 5: Setup en Jira

Si tienes el MCP de Atlassian configurado:

```
/setup-jira NUEVO-PROY
```

(Reemplaza `NUEVO-PROY` con tu projectKey real de Jira.)

El agente:
1. Verifica acceso al proyecto en Jira
2. Te propone una estructura completa (épicas → HUs → subtareas)
3. **Espera tu confirmación**
4. Crea todos los issues con labels y jerarquía correcta

⏰ Tiempo: ~15-20 minutos (depende del tamaño del proyecto).

### Paso 6: Generar PPT de Kickoff

```
/generar-kickoff-pptx
```

Resultado: PPT de 10 slides con identidad visual Mobiik aplicada, listo para presentar al cliente.

⏰ Tiempo: ~5 minutos.

### Paso 7: Documento Word de HUs para sign-off

```
/generar-hu-docx
```

Resultado: Documento Word formal de ~40-60 páginas con todas las HUs en formato Gherkin, listo para sign-off del PO del cliente.

⏰ Tiempo: ~10 minutos.

### ✅ Resultado total

En menos de **1 hora** tienes todo lo que normalmente toma **2-3 días**:

```
./entregables/
├── RAID Log - <proyecto>.xlsx
├── Plan de Trabajo - <proyecto>.xlsx
├── KO - <proyecto>.pptx
└── Historias de Usuario - <proyecto>.docx
```

Más todo el backlog estructurado en Jira con trazabilidad bidireccional.

---

## 4. Comandos disponibles

| Comando | Cuándo usarlo | Tiempo |
|---|---|---|
| `/analizar-propuesta <archivo>` | Recién firmaste el contrato, antes de cualquier kickoff | 5 min |
| `/generar-raid` | Después del análisis, antes del primer sprint planning | 5 min |
| `/generar-plan-excel` | Cuando ya tienes alcance + equipo asignado | 5 min |
| `/setup-jira <KEY>` | Cuando el proyecto en Jira está creado pero vacío | 15-20 min |
| `/generar-hu-docx` | Tras setup de Jira, para entregar formalmente al cliente | 10 min |
| `/generar-kickoff-pptx` | 24-48 horas antes del kickoff con cliente | 5 min |

### Orden recomendado en un proyecto nuevo

```
1. /analizar-propuesta SOW.docx
2. /generar-raid                  ← validar con PM Mobiik
3. /generar-plan-excel            ← revisar con Tech Lead
4. /setup-jira NUEVO-PROY         ← crear backlog
5. /generar-kickoff-pptx          ← preparar presentación
6. /generar-hu-docx               ← entregar al cliente para sign-off
```

---

## 5. Conversar con el agente

Además de los comandos slash, puedes invocar al agente directamente con `@`:

```
@analista-scrum-senior tengo un cliente que insiste en agregar 5 features más sin 
ampliar el cronograma, ¿cómo abordo esa conversación según el estándar Mobiik?
```

O simplemente:

```
@analista-scrum-senior ayúdame a refinar esta HU:
"Como usuario quiero poder loguear con Google"
```

El agente te responderá:
- Reformulará con formato correcto (Como/Quiero/Para)
- Agregará criterios Gherkin
- Identificará dependencias técnicas
- Te sugerirá una prioridad MoSCoW
- Estimará story points

---

## 6. Estándar visual Mobiik

Todos los entregables generados aplican automáticamente:

| Elemento | Estándar |
|---|---|
| **Fondo de portadas** | Negro `#0A0A0A` |
| **Acento corporativo** | Verde lima `#AADC1E` |
| **Tipografía titulares** | Arial Black |
| **Tipografía body** | Calibri |
| **Slogan en pie** | "© 2026 Mobiik   \|   coding for the future" |
| **Semaforización** | 🔴 `#FF4444` · 🟠 `#FFA040` · 🟢 `#AADC1E` · 🔵 `#1EA0DC` |

**No necesitas configurar nada** — el agente y los scripts lo aplican solos. Consulta [ESTANDAR-VISUAL-MOBIIK.md](./ESTANDAR-VISUAL-MOBIIK.md) para el detalle completo.

---

## 7. Estándar Jira

Todos los proyectos creados por el agente siguen la **nomenclatura estándar Mobiik**:

### Project keys
```
[CLIENTE]-[ABREV_PROYECTO]
```

Ejemplos:
- `TEC-PRESEL` (TecMilenio Preselección)
- `BBVA-ONBO` (BBVA Onboarding)
- `BIMBO-INTRA` (Bimbo Intranet)

### Jerarquía
```
Iniciativa
└─ Épica         [EPIC][Módulo] Nombre del entregable
    └─ HU        [HU][S<N>] Como X, quiero Y, para Z
        └─ Sub   [TASK][Disciplina] Acción concreta
```

### Labels obligatorios
- `cliente-<nombre>` — para filtros cross-projects
- `sprint-1` / `sprint-2` / `sprint-3` / `go-live`
- `tipo-<migracion|nuevo|mantenimiento>`
- `bloqueador-cliente` — cuando dependa del cliente
- `riesgo-alto` / `riesgo-medio` — cuando aplique
- `hito-facturacion-N` — asociado al hito de pago
- `must-have` / `should-have` / `could-have` / `wont-have` (MoSCoW)

### Dashboards estándar (recomendados)

Por cada proyecto, el agente sugiere crear 3 dashboards:

1. **Dashboard Ejecutivo (para PO)**: burndown sprint actual, avance por épica, bloqueadores, hitos próximos
2. **Dashboard Operativo (para SM/equipo)**: velocity, cycle time, carga por persona
3. **Dashboard de Riesgos**: issues con `riesgo-alto` abiertos, dependencias bloqueantes

### JQL útiles

```jql
project = TEC-PRESEL AND sprint in openSprints()
project = TEC-PRESEL AND labels = "bloqueador-cliente" AND status != Done
project = TEC-PRESEL AND "Hito de Facturación" = 2 AND status != Done
project = TEC-PRESEL AND labels = "riesgo-alto" AND resolution = Unresolved
```

---

## 8. Buenas prácticas

### ✅ Antes de invocar al agente

- Ten la propuesta firmada disponible (PDF, DOCX o texto)
- Conoce el equipo asignado (nombres + roles)
- Ten el projectKey de Jira si vas a hacer `/setup-jira`
- Define una carpeta `./entregables/` en tu proyecto

### ✅ Durante el uso

- **Lee la propuesta del agente antes de aprobarla** — el agente te muestra lo que va a hacer ANTES de crear archivos o issues
- **Valida los riesgos con el PM Mobiik** antes de pasarlos al cliente
- **Confirma estructura de Jira con el cliente** antes de ejecutar `/setup-jira`
- **Personaliza los entregables generados** — el agente te da el 80% del trabajo, el 20% restante es ajuste manual fino

### ✅ Después de generar

- Abre los archivos en su aplicación nativa para validar visualmente
- Verifica que no quedaron datos placeholder de otros proyectos
- Sube los archivos finales a la carpeta compartida del cliente
- Documenta cualquier mejora al agente abriendo un issue en este repo

### ❌ Evita

- Generar Jira issues sin confirmar la estructura primero
- Compartir un Excel/PPT generado sin abrirlo y validarlo antes
- Asumir que los riesgos identificados están completos — siempre agrega los específicos de tu proyecto
- Olvidar actualizar el RAID Log durante la ejecución (es un documento vivo)

---

## 9. Preguntas frecuentes

### ¿El agente entiende propuestas en inglés?

Sí, pero por defecto te responde en español (estándar Mobiik para clientes en LATAM). Si tu cliente requiere entregables en inglés, dile explícitamente:

```
@analista-scrum-senior genera el documento en inglés
```

### ¿Puedo usar el agente para clientes con identidad visual distinta a Mobiik?

No por defecto. Este plugin aplica **identidad Mobiik corporativa**. Si el cliente requiere su propia identidad, deberás:
- Ajustar manualmente la paleta y fuentes en los archivos generados
- O bien crear un plugin variante para ese cliente específico

### ¿Cómo actualizo a una versión nueva del plugin?

```
/plugin marketplace update mobiik
```

### ¿Funciona sin acceso a Jira?

Sí, excepto el comando `/setup-jira`. Todos los demás comandos funcionan sin Jira.

### ¿Los entregables generados ya están listos para enviar al cliente?

**Casi.** Te dan el 80-90% del trabajo. Siempre:
1. Abre el archivo y revísalo
2. Reemplaza cualquier dato genérico
3. Ajusta secciones específicas del proyecto
4. Valida con tu equipo Mobiik antes de enviar

### ¿Puedo proponer mejoras al agente?

Sí, abre un issue en https://github.com/Mobiik/docs-claude-plugins/issues con tu sugerencia.

### ¿Qué hago si encuentro un bug?

Reporta con:
- Versión del plugin (`/plugin` para verla)
- Descripción del problema
- Pasos para reproducir
- Output esperado vs obtenido

---

## Para más detalle

- 📖 [Instalación paso a paso](./INSTALACION.md)
- 🎨 [Estándar visual Mobiik completo](./ESTANDAR-VISUAL-MOBIIK.md)
- 🔧 [README del plugin](../analista-scrum-mobiik/README.md)

---

**¿Listo para acelerar tu próximo proyecto?**

Empieza con: `/analizar-propuesta` 🚀

---

© 2026 Mobiik · coding for the future
