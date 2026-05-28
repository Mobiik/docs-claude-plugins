---
description: Analiza un problema o conflicto y entrega estrategias de negociación diferenciadas (intereses, BATNA, recomendación)
---

Ayuda al Scrum Master humano a preparar una **negociación o resolución de un conflicto**. **NUNCA des una sola respuesta**: entrega un análisis estructurado con estrategias diferenciadas.

## Proceso

1. **Si falta información clave, pregúntala ANTES de recomendar**:
   - ¿Quién es la contraparte y qué relación tienes con ella?
   - ¿Qué está en juego (valor, relación, recurrencia, reputación)?
   - ¿Qué quieres lograr realmente? ¿Qué te preocupa?
   - ¿Cuál es tu mejor alternativa si no hay acuerdo (BATNA)?
   - ¿Hay restricciones de tiempo, presupuesto o internas?

2. **Entrega SIEMPRE esta estructura**:

   ### 1. Replanteo del problema (por intereses)
   Reformula el problema en términos de **intereses** de cada parte — qué necesita y qué le preocupa a cada uno — **no de posiciones** ("yo quiero X").

   ### 2. Conflicto central y lo que está en juego
   El nudo real del desacuerdo, los riesgos y qué se juega para la **relación** a futuro.

   ### 3. Estrategias diferenciadas (2 o 3)
   No solo tonos distintos: **enfoques distintos**. Cada una con:
   - **Nombre claro** (ej. "Anclaje en valor", "Concesión condicionada", "Pausa estratégica")
   - **Qué prioriza y qué sacrifica**
   - **Cómo ejecutarla**: pasos concretos y **frases sugeridas**
   - **Resultado probable**

   ### 4. Recomendación final
   Cuál estrategia recomiendas y **por qué**, dada la situación.

3. **Fundamentos a aplicar**:
   - Negociación por intereses (método **Harvard**: separar persona/problema, intereses no posiciones, opciones de mutuo beneficio, criterios objetivos)
   - **BATNA** (mejor alternativa al acuerdo negociado) — propia y estimada de la contraparte
   - **Comunicación no violenta** (observación → sentimiento → necesidad → petición)

4. **(Opcional) Genera el entregable de preparación** en Word si el usuario lo pide:

   ```bash
   pip3 install --user python-docx   # una sola vez
   python3 scripts/build_negociacion_docx.py   # mobiik-scrum-templates/scripts/
   ```

   Guarda en `./entregables/Preparacion Negociacion - <contraparte>.docx`.

## Reglas

- **No des una respuesta única**: siempre 2–3 estrategias + recomendación.
- **Ataca el problema, no a la persona.**
- Condiciona toda concesión ("si… entonces…"); nunca regales sin contrapartida.
- Si falta información clave, **pregunta antes de recomendar**. No inventes el contexto.
