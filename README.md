# SaaS Launchpad — método Rob Walling

Conjunto de **comandos de Claude** para encontrar y validar ideas de SaaS siguiendo el método de **Rob Walling** (SaaS Launchpad, "Start Small, Stay Small", TinySeed) y, en particular, el framework de validación **2/20/200** (≈2 horas de research + ≈20 horas de campo + ≈200 horas de MVP). Todo el trabajo se persiste en Markdown bajo `data/` y se espeja como Google Docs en Drive.

---

## Comandos disponibles (`.claude/commands/`)

### `/saas_idea_encontrar_idea`
Proceso guiado paso a paso (una pregunta a la vez) para **encontrar ideas de SaaS B2B** según las 7 aproximaciones de Rob Walling. Parte de las ventajas del fundador (experiencia, audiencia/red, capacidades, restricciones) y converge en ideas candidatas listas para validar. Construye `perfil-fundador.md` y una ficha `idea.md` por cada idea procesada.

### `/saas_idea_validar_idea`
Evalúa una idea de SaaS contra los **18 factores del "negocio SaaS ideal"** de Rob Walling (método SaaS Launchpad / Stair Step), penaliza los 8 anti-patrones/errores comunes que él marca, y entrega un puntaje justificado. Es una evaluación de escritorio rápida (sin salir a campo), útil como filtro antes de invertir horas en validación real.

### `/saas_idea_prevalidar_2h`
Automatiza la **pre-validación de ~2 horas** (la "2" del framework). Recorre el scorecard **5 PM** (Problem, Purchaser, Pricing model, Market, product-founder fit, Painfulness) haciendo el research web por vos (competidores, SimilarWeb, Crunchbase, BLS, pricing pages, ads, orgánico), NO inventa datos (si están detrás de un login o solo los tenés vos, te los pide y pausa), y cierra con un scorecard y un gate de decisión hacia las ~20h de campo. Escribe `prevalidacion.md`.

### `/saas_idea_validar_2_20_200`
**Tablero maestro reanudable** de toda la validación 2/20/200 de una idea. Es el director de orquesta: delega la Fase 2 a `/saas_idea_prevalidar_2h` y la Fase 20 a `/saas_idea_validar_20h`, registra los gates de decisión entre fases y la decisión final de construir (o no) el MVP. Hace el research por vos, no inventa datos y no escribe código hasta la Fase 200. Escribe el tablero maestro `validacion.md`.

### `/saas_idea_validar_20h`
Conduce la **validación de campo de ~20 horas** (la "20" del framework), ya sin escribir código. Sale a conseguir señal real con dos approaches —hablar con gente (warm + cold) y/o una landing con tráfico—, arma la lista de a quién contactar, redacta el outreach, prepara las preguntas no-leading del Mom Test, registra los resultados reales (yeses, opt-ins, citas) y cierra con un gate hacia las ~200h del MVP. Escribe `validacion-campo.md` e invoca sus dos motores operativos.

### `/saas_idea_campana_llamadas`
**Motor operativo del Approach 1** (hablar con gente), al estilo de las ~100 llamadas de Jason Buckingham (Senior Place): cómo conseguir y agendar las llamadas, cuántos emails mandar y qué respuesta esperar, qué decir antes/durante/después de cada llamada, cómo leer patrones (volumen + %), el ritual de "game tape" para mejorar, y cómo cerrar con pre-venta real (los 5 cheques). Trae un template de hoja de cálculo. Escribe `campana-llamadas.md`.

### `/saas_idea_campana_landing`
**Motor operativo del Approach 2** (landing page + tráfico): cómo debe verse y qué debe decir una buena landing de validación (H1 que nombra el problema + para quién, H2 de diferenciación, CTA de captura de email), ejemplos reales (SwipeWell, Transistor, Setup, Level, Tuple, Buffer), cuándo conviene un sales letter/manifiesto, por qué NO poner screenshots todavía, cómo leer las métricas de éxito (volumen + % de opt-in) y cómo iterar headline/canal. Trae un template de hoja de cálculo. Escribe `campana-landing.md`.

### `/saas_idea_sync_drive`
Utilitario transversal que **sincroniza Google Drive → `data/`** (el camino inverso del espejo). Recorre cada idea y fase, compara cada Google Doc del Drive contra su `.md` local normalizando el ruido de la conversión Doc↔Markdown, clasifica el estado de cada par (en sync / solo en Drive / solo local / difieren) y, ante cualquier inconsistencia, te avisa con el diff y te deja decidir. NUNCA crea, sobreescribe ni borra nada sin tu confirmación explícita.

---

## Estructura de datos de `data/`

`data/` es la **copia de trabajo viva** del proyecto: los comandos persisten acá su trabajo en Markdown, de forma incremental. Es la **fuente de verdad**; cada archivo se espeja además como Google Doc nativo en Drive (ver `CLAUDE.md` → "Espejo en Google Drive de los tableros de `data/`").

```
data/
├── perfil-fundador.md                      ← perfil del fundador (COMPARTIDO entre todas las ideas)
└── idea-NNN-<slug>/                         ← una carpeta por idea (NNN correlativo, slug kebab-case)
    ├── 1-idea_phase/                        ← fase de idea + validación (las ~2h y ~20h del framework)
    │   ├── idea.md
    │   ├── prevalidacion.md
    │   ├── validacion.md
    │   ├── validacion-campo.md
    │   ├── campana-llamadas.md
    │   └── campana-landing.md
    ├── 2-build_phase/                        ← fase de construcción del MVP (las ~200h) — aún sin comandos
    └── 3-launch_phase/                       ← fase de lanzamiento — aún sin comandos
```

La estructura es **una carpeta por idea**; dentro, una subcarpeta por fase. Los archivos de la fase de idea conviven en `1-idea_phase/`. Las carpetas `2-build_phase/` y `3-launch_phase/` existen como placeholders (con `.gitkeep`) para las fases siguientes; todavía **ningún comando escribe en ellas**.

### Archivos — qué comando escribe cada uno y qué guarda

| Archivo | Comando que lo escribe | Qué guarda |
|---|---|---|
| `perfil-fundador.md` | `/saas_idea_encontrar_idea` | Perfil del fundador (compartido, no pertenece a ninguna idea): ventajas, experiencia, audiencia/red, capacidades técnicas, restricciones de tiempo/dinero y preferencias. Incluye un puntero corto a cada idea ya procesada. |
| `1-idea_phase/idea.md` | `/saas_idea_encontrar_idea` | Ficha de la idea candidata: problema, para quién, aproximación(es) de Walling, ventaja del fundador, evidencia inicial, banderas de riesgo y veredicto con fecha. |
| `1-idea_phase/prevalidacion.md` | `/saas_idea_prevalidar_2h` | Tablero de la pre-validación de ~2h: scorecard 5 PM con research web citado y veredicto 🟢/🟡/🔴 + gate hacia las ~20h. Distingue verificado / declarado / pendiente. |
| `1-idea_phase/validacion.md` | `/saas_idea_validar_2_20_200` | Tablero **maestro** y reanudable de toda la validación 2/20/200: hereda los veredictos de cada fase, registra los gates entre fases y la decisión final de construir el MVP. |
| `1-idea_phase/validacion-campo.md` | `/saas_idea_validar_20h` | Tablero de la validación de campo de ~20h: approach elegido, dónde está la gente, outreach, preguntas del Mom Test y resultados reales (yeses, opt-ins, citas). Consolida los dos motores operativos. |
| `1-idea_phase/campana-llamadas.md` | `/saas_idea_campana_llamadas` | Sub-tablero del Approach 1: setup de campaña, cadencia, guiones, banco de preguntas, game tape y resultados (respuestas, % con el problema, yeses calificados, cheques de pre-venta). |
| `1-idea_phase/campana-landing.md` | `/saas_idea_campana_landing` | Sub-tablero del Approach 2: copy (H1/H2/CTA), versiones probadas, plan de tráfico, ritual de iteración y métricas reales (visitas, opt-ins, % por canal). |

---

## Secuencia recomendada

El **tablero maestro `/saas_idea_validar_2_20_200`** orquesta las fases 2 y 20 por vos (delegando en los comandos de cada fase). Podés correrlo a él y dejarte llevar, **o** correr cada comando suelto en este orden:

```
1. /saas_idea_encontrar_idea       → perfil del fundador + ideas candidatas (perfil-fundador.md, idea.md)
        ↓
2. /saas_idea_validar_idea         → filtro de escritorio rápido (18 factores). Opcional, para descartar antes de gastar horas.
        ↓
3. /saas_idea_validar_2_20_200     → DIRECTOR DE ORQUESTA (de acá en adelante guía todo; delega 2 y 20)
        ├─ Fase 2  → /saas_idea_prevalidar_2h     → prevalidacion.md  ── gate 🟢/🟡/🔴 ─┐
        │                                                                              │ (solo pasás si 🟢)
        ├─ Fase 20 → /saas_idea_validar_20h       → validacion-campo.md  ←─────────────┘
        │              ├─ Approach 1 → /saas_idea_campana_llamadas → campana-llamadas.md
        │              └─ Approach 2 → /saas_idea_campana_landing  → campana-landing.md
        │                                                          ── gate 🟢/🟡/🔴 ─┐
        └─ Fase 200 → construir el MVP (~200h) ←───────────────────────────────────┘ (solo construís si 🟢)
```

- **Empezá por `/saas_idea_encontrar_idea`** si todavía no tenés una idea concreta. Si ya la tenés, podés saltar directo.
- **`/saas_idea_validar_idea`** es un filtro opcional de escritorio: úsalo para matar rápido las ideas flojas antes de invertir las ~2h de pre-validación.
- **A partir de la pre-validación, dejá que `/saas_idea_validar_2_20_200` conduzca:** él invoca `prevalidar_2h` (Fase 2) y `validar_20h` (Fase 20), y respeta los gates —no avanzás a la fase siguiente si el veredicto no es 🟢—. Cada comando de fase también puede correrse standalone si preferís.
- **Dentro de la Fase 20**, Rob recomienda hacer **los dos approaches**: las conversaciones (`campana_llamadas`) y la landing (`campana_landing`) se complementan y se calibran entre sí.
- **`/saas_idea_sync_drive`** es transversal: corrélo cuando hayas editado los Docs directamente en Drive y quieras traer esos cambios de vuelta a `data/`.

> **Regla que atraviesa todo el método:** se escala la inversión de horas solo cuando la señal lo justifica (2 → 20 → 200), no se inventan datos (si no hay dato real, se pide y se pausa), y no se escribe una línea de código hasta pasar el gate de la Fase 20.
