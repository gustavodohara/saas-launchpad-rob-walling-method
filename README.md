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

### `/saas_build_mvp_5pasos`
Comando principal de la **Fase 200 (build)**: planifica y arranca la construcción del MVP siguiendo los **5 pasos de Rob Walling**. Su columna vertebral son **dos barreras** que impiden tirar horas: (1) un **gate anti-código** —según Rob hay 3 formas de hacer un MVP además de la landing: **human automation** (lo hacés a mano), **no-code** y, recién al final, **full code**; full code arranca *prohibido* y solo se desbloquea si se justifica que es lo más rápido / menos tiempo / más barato (ser dev y "rápido codeando" NO cuenta como justificación)—; y (2) una **barrera de alcance** que, para cada feature, pregunta *"¿esto se puede hacer a mano rápido?"* (reset de contraseña, alta de usuarios, delete, billing, reembolsos…) y deja afuera del MVP todo lo que sí. Empieza con el gate "¿MVP o lanzar la v1 directa?" + nombrar el supuesto más riesgoso, y recorre objetivo → features core → approach → timeline → ejecución, cerrando con un veredicto de **plan-readiness**. Tiene **dos reglas de oro** que lo hacen deliberadamente incómodo: **no inventa tus datos** (early-access list, métricas, stack, presupuesto: te los pide) y **no te da la razón** cuando querés construir de más — actúa como freno, no como un sí, porque toda esta fase existe para validar hipótesis de la forma más barata y rápida posible. Escribe `2-build_phase/plan-mvp.md`.

### `/saas_build_mvp_tips_dev`
**Continuación de `/saas_build_mvp_5pasos`** para cuando el approach del MVP ya es **full code** (Fase 200, build): convierte la entrevista de **Derek Reimer** (fundador de SavvyCal, ex-CTO de Drip) en un sistema guiado para **construir bien un MVP de código sin sobre-construir**. Primero un **gate de entrada** —*¿de verdad toca escribir código, o seguís en human automation / no-code?*— que devuelve al fundador a los 5 pasos si saltó el gate anti-código. Después recorre 7 decisiones de Derek: (1) **drillar el core** (la salsa secreta) y prohibir lo secundario/administrativo (login, settings, forgot-password = procrastinación); (2) **lo que NO se construye y se hace a mano** (delete, sorting, search, billing, password reset, self-signup, refunds, admin dashboards) + la **única must-have**: "login-as-user" (ghost) para diagnosticar bugs; (3) calidad de código, frameworks batteries-included y **tests sí pero no 100% coverage**; (4) cuánto pulir — **usabilidad siempre, estética solo si es tu value prop**; (5) elección de **stack** (Rails/Django/Laravel, backend-centric, **usá lo que ya sabés**); (6) chequeo anti-sobre-construcción (**Drip 3–4 meses vs Level 9 meses**); (7) **lanzamiento por fases** sin quemar tu lista. Cierra con un veredicto de **code-readiness**. Mismas dos reglas de oro: **no inventa tus datos** (stack, skills, early-access, timeline: te los pide) y **es el freno**, no te da la razón cuando querés construir de más. Escribe `2-build_phase/mvp-codigo.md`.

### `/saas_build_marketing_antes_de_codear`
Comando de **encuadre y gate** del **puente Fase 20 → 200 (build)**: decide **CUÁNDO** empezar a hacer marketing, basado en la lección de **Rob Walling** *"empezá a hacer marketing **antes** de codificar"* (no su viejo lema "el día que empezás a codificar", sino **meses antes de lanzar**). Es el **"¿POR QUÉ y CUÁNDO?"** del pre-marketing; el **"¿CÓMO?"** lo conduce `/saas_build_lista_lanzamiento`, al que hace **handoff**. Primero desmonta las **2 objeciones** clásicas: (1) **"me roban la idea"** —a nadie le importa tu idea; podés pre-marketear contando solo el **problema** sin revelar la salsa secreta; el código casi no vale (se clona en 1–2 meses), gana la **ejecución de marketing**—; y (2) **"estoy muy ocupado codificando"** —el marketing es un **building block** tan fundamental como los unit tests; sin él tu producto es un hobby—. Después enmarca los **3 beneficios + bonus**: (bonus) te fuerza a articular problema/para-quién; (1) **validación** real con tráfico (650 emails vs 6 opt-ins); (2) **lista de early access** instantánea (cobrá, no hagas betas gratis); (3) **momentum del día de lanzamiento** (conversión 5–40%: US$60 de MRR vs 260 trials). Cierra con un veredicto de **marketing-readiness** y el **compromiso** concreto de fecha de arranque. Mismas dos reglas de oro: **no inventa tus datos** (tu objeción real, timeline, si ya tenés landing: te los pide) y **es el freno** contra posponer el marketing "para después de codificar". Escribe `2-build_phase/premarketing.md`.

### `/saas_build_lista_lanzamiento`
Comando de la **Fase 200 (build)**: motor operativo para **construir tu lista de lanzamiento por email**, basado en la lección de **Rob Walling** sobre listas de lanzamiento. Sirve para dos momentos —**validar** (llevar tráfico a tu landing para medir cómo resuena el H1 y cuántos opt-in) y **construir la lista de interesados** a la que lanzás—; ambos valen en build (la lista se arma **en paralelo** al MVP para no lanzar a "crickets": Drip lanzó con **3.400**; dotNetInvoice arrancó con **80** → 5 ventas → ~6%). Arranca con el encuadre **anti-spam** (permiso + desuscripción + nunca vender/alquilar) y la regla "**targeteá, no junta vanity metrics**". Su corazón son los **4 círculos concéntricos** (audiencia → red → audiencia de la red → tráfico frío) con su gran advertencia: la **maldición de la audiencia** (**NO construyas audiencia para SaaS** —convierte mal y churnea; <5% de TinySeed la tenía—; **construí tu RED, no tu audiencia**). Después: **pixel de retargeting día 1**, los **~9 canales** de tráfico pre-producto (SEO, contenido, PPC, cold outreach, hangouts, Q&A, launch sites, eventos, free tools), el **tracking de atribución por canal**, y el **test brutal**: *"si no podés llevar tráfico frío AHORA, ¿cómo lo hacés tras lanzar?"*. Es el **motor de tráfico** que complementa a `/saas_idea_campana_landing` (ese da la **página y el copy**; este, la **gente que la visita**). Mismas dos reglas de oro: **no inventa tus datos** (tráfico, opt-ins, % por canal, quién hay en tu red: te los pide) y **es el freno** contra el vanity-metric y la construcción de audiencia. Trae un template de hoja de cálculo. Escribe `2-build_phase/lista-lanzamiento.md`.

### `/saas_idea_evaluar_ia`
Comando de la **Fase 200 (build)**: evalúa **si y cómo** incorporar IA a tu SaaS, basado en la entrevista de **Arvid Kahl** (PodScan.fm) en el curso de Rob Walling. Primero hace el **gate honesto** —*¿IA es siquiera el approach correcto, o estás "espolvoreando IA" porque está de moda?* (tener un problema NO obliga a resolverlo con IA)— y si la respuesta es sí, recorre los **16 riesgos/landmines de Arvid** agrupados (abuso/costo, observabilidad/control, calidad del output, relacionales y legales), puntuando severidad para TU solución concreta y dejando una mitigación accionable por cada uno. Cierra con un veredicto de **build-readiness** y un registro de riesgos. NO inventa tu stack, presupuesto ni régimen de compliance: te los pide. Escribe `2-build_phase/evaluacion-ia.md`.

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
    ├── 2-build_phase/                        ← fase de construcción del MVP (las ~200h)
    │   ├── plan-mvp.md                        ← plan del MVP (5 pasos de Rob Walling)
    │   ├── mvp-codigo.md                      ← (solo si el approach es full code) tips de Derek Reimer
    │   ├── premarketing.md                    ← encuadre "marketing antes de codificar" (puente 20→200)
    │   ├── lista-lanzamiento.md               ← lista de lanzamiento por email (círculos concéntricos)
    │   └── evaluacion-ia.md                  ← (solo si el MVP usa IA)
    └── 3-launch_phase/                       ← fase de lanzamiento — aún sin comandos
```

La estructura es **una carpeta por idea**; dentro, una subcarpeta por fase. Los archivos de la fase de idea conviven en `1-idea_phase/`. La carpeta `2-build_phase/` tiene los comandos de la familia `saas_build_` (`/saas_build_mvp_5pasos` → `plan-mvp.md`; su continuación `/saas_build_mvp_tips_dev` → `mvp-codigo.md`, que se escribe solo si el approach es full code; `/saas_build_marketing_antes_de_codear` → `premarketing.md`, el encuadre "marketing antes de codificar" que se corre en el puente Fase 20→200 y hace handoff a la lista; y `/saas_build_lista_lanzamiento` → `lista-lanzamiento.md`, el motor de tráfico para armar la lista de lanzamiento, que se construye en paralelo al MVP) más `/saas_idea_evaluar_ia` → `evaluacion-ia.md` (que se escribe solo si el MVP incorpora IA); `3-launch_phase/` sigue siendo un placeholder (con `.gitkeep`) para la fase de lanzamiento, donde todavía **ningún comando escribe**.

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
| `2-build_phase/plan-mvp.md` | `/saas_build_mvp_5pasos` | Plan del MVP (Fase 200, build) por los 5 pasos de Rob Walling: gate "¿MVP o v1?" + supuesto más riesgoso, objetivo y métricas, features core pasadas por la barrera "¿se hace a mano rápido?", approach con el **gate anti-código** (human automation → no-code → full code), timeline y plan de ejecución, con veredicto de plan-readiness. |
| `2-build_phase/mvp-codigo.md` | `/saas_build_mvp_tips_dev` | Tablero de la Fase 200 (build) para el approach **full code**, basado en la entrevista de Derek Reimer (SavvyCal / ex-Drip): gate de entrada "¿toca código?", el core/salsa secreta + lista negra de procrastinación, lo que NO se construye (se hace a mano) + la must-have "login-as-user", calidad/tests, pulido (usabilidad vs estética), stack ("usá lo que ya sabés"), chequeo anti-sobre-construcción (Drip vs Level) y lanzamiento por fases, con veredicto de code-readiness. Solo se crea si el approach es full code. |
| `2-build_phase/premarketing.md` | `/saas_build_marketing_antes_de_codear` | Tablero del encuadre "empezá a marketear antes de codificar" (puente Fase 20→200, lección de Rob Walling): setup (momento, vende/hobby, timeline del MVP, si ya pre-marketea, objeción real), la objeción trabajada (me roban la idea / muy ocupado codificando) con su desmonte + el "problema en 1 frase" que puede contar sin revelar la idea, los 3 beneficios + bonus conectados a su caso, y el compromiso concreto (primer paso + fecha) con veredicto de marketing-readiness. Hace handoff a `lista-lanzamiento.md`. |
| `2-build_phase/lista-lanzamiento.md` | `/saas_build_lista_lanzamiento` | Tablero de la Fase 200 (build) de la lista de lanzamiento por email (lección de Rob Walling): setup (momento validar/construir, ICP, landing destino, pixels, anti-spam), plan por los 4 círculos concéntricos (audiencia → red → audiencia de la red → frío) con la advertencia de la maldición de la audiencia, canales de tráfico activados (de los ~9 pre-producto), tracking de atribución por canal y resultados reales (opt-ins, % por origen, costo/sub), con veredicto del estado de la lista. Motor de tráfico que complementa a `campana-landing.md`. |
| `2-build_phase/evaluacion-ia.md` | `/saas_idea_evaluar_ia` | Tablero de la Fase 200 (build) para soluciones con IA: gate "¿IA es el approach correcto?", registro de los 16 riesgos de Arvid Kahl con su mitigación/decisión, bloqueantes y veredicto de build-readiness. Solo se crea si el MVP incorpora IA. |

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
                       ├─ (ANTES de codear) → /saas_build_marketing_antes_de_codear → premarketing.md ──┐ handoff
                       ├─ /saas_build_mvp_5pasos → plan-mvp.md   (plan del MVP — gate anti-código)        │
                       │     └─ (si el approach es full code) → /saas_build_mvp_tips_dev → mvp-codigo.md  │
                       ├─ (en paralelo al MVP) → /saas_build_lista_lanzamiento → lista-lanzamiento.md ←───┘
                       └─ (si el MVP usa IA) → /saas_idea_evaluar_ia → evaluacion-ia.md
```

- **Empezá por `/saas_idea_encontrar_idea`** si todavía no tenés una idea concreta. Si ya la tenés, podés saltar directo.
- **`/saas_idea_validar_idea`** es un filtro opcional de escritorio: úsalo para matar rápido las ideas flojas antes de invertir las ~2h de pre-validación.
- **A partir de la pre-validación, dejá que `/saas_idea_validar_2_20_200` conduzca:** él invoca `prevalidar_2h` (Fase 2) y `validar_20h` (Fase 20), y respeta los gates —no avanzás a la fase siguiente si el veredicto no es 🟢—. Cada comando de fase también puede correrse standalone si preferís.
- **Dentro de la Fase 20**, Rob recomienda hacer **los dos approaches**: las conversaciones (`campana_llamadas`) y la landing (`campana_landing`) se complementan y se calibran entre sí.
- **Al entrar a la Fase 200, antes de escribir una línea, corré `/saas_build_marketing_antes_de_codear`**: es el encuadre de Rob *"empezá a marketear **antes** de codificar"*. Desmonta las 2 objeciones clásicas (me roban la idea / muy ocupado codificando), te muestra los 3 beneficios + bonus del pre-marketing (validación temprana, lista de early access, momentum de lanzamiento — conversión 5–40%) y te deja comprometido a poner una landing mínima en vivo ya. Es el **gate de actitud** que abre la construcción de la lista: hace handoff a `/saas_build_lista_lanzamiento` (el cómo) y `/saas_idea_campana_landing` (la página). Si es un hobby sin intención de vender, te lo dice y ahí no hace falta marketing.
- **Para planificar el MVP, seguí con `/saas_build_mvp_5pasos`**: te hace el gate "¿MVP o v1?", te obliga a nombrar el supuesto más riesgoso y —clave— **te frena de codear de entrada** (human automation → no-code → full code, en ese orden; codear solo si se justifica) y recorta el alcance dejando afuera todo lo que se resuelve a mano. **Solo si ahí el approach termina siendo full code (✅ justificado), seguí con `/saas_build_mvp_tips_dev`**: la continuación con los tips de Derek Reimer para construir bien el MVP de código sin sobre-construir (drillar el core, lo que NO se codea, "login-as-user", tests sin 100% coverage, stack que ya sabés, lanzamiento por fases). Y **si el MVP incorpora IA**, corré también `/saas_idea_evaluar_ia`: primero el gate "¿IA es siquiera el approach correcto?" (tener un problema no obliga a usar IA) y después los 16 riesgos de Arvid Kahl. Si el approach no es código, salteá `tips_dev`; si el MVP no usa IA, salteá `evaluar_ia`. **En paralelo a construir el MVP, corré `/saas_build_lista_lanzamiento`** para no llegar al lanzamiento "a crickets": es el motor de tráfico (los 4 círculos concéntricos + los ~9 canales) que llena tu lista de interesados; complementa a `/saas_idea_campana_landing` (ese te da la página y el copy; este, la gente que la visita). Su columna vertebral es la **maldición de la audiencia** (no construyas audiencia para SaaS — construí tu red) y el **test brutal** (si no podés llevar tráfico frío ahora, no pasará tras lanzar).
- **`/saas_idea_sync_drive`** es transversal: corrélo cuando hayas editado los Docs directamente en Drive y quieras traer esos cambios de vuelta a `data/`.

> **Regla que atraviesa todo el método:** se escala la inversión de horas solo cuando la señal lo justifica (2 → 20 → 200), no se inventan datos (si no hay dato real, se pide y se pausa), y no se escribe una línea de código hasta pasar el gate de la Fase 20.
