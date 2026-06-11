# Guía de uso — ¿qué comando corro?

Esta guía responde una sola pregunta: **de los 20 comandos, ¿cuáles tengo que ejecutar yo y cuáles se corren solos o según el caso?**

No repite el detalle de cada comando (eso está en el [`README.md`](README.md) y en cada `.md` de `.claude/commands/`). Acá te decimos **qué es principal y qué es complementario**, para que no te pierdas entre tantos slash commands.

---

## La idea en una línea

> **Comandos PRINCIPALES** = los que **iniciás vos** y conducen una fase o una decisión central. Si solo pudieras correr uno por fase, es ese.
>
> **Comandos COMPLEMENTARIOS** = se ejecutan **dentro** de un principal (delegado o handoff), **según una condición** (full code, usa IA), como **motor** que profundiza un paso, o son **transversales/utilitarios**.

Regla mental: **arrancá siempre por un comando principal.** Él te va a pedir (o invocar) los complementarios cuando hagan falta.

---

## La espina dorsal (corré estos y vas bien)

Este es el camino mínimo de punta a punta. Si solo seguís estos comandos, recorrés el método completo:

```
1. /saas_idea_encontrar_idea          ← solo si todavía NO tenés una idea concreta
        ↓
2. /saas_idea_validar_2_20_200        ← DIRECTOR DE VALIDACIÓN (conduce las ~2h y las ~20h por vos)
        ↓  (solo pasás si el gate da 🟢)
3. /saas_build_mvp_5pasos             ← plan y construcción del MVP (con gate anti-código)
   /saas_build_lista_lanzamiento      ← en PARALELO: armás la lista para no lanzar "a crickets"
   /saas_build_pricing                ← el primer precio (alimenta pre-venta, early access y lanzamiento)
        ↓  (MVP completo y sin bugs + lista nutrida + precio definido)
4. /saas_launch_lanzamiento_por_fases ← lanzás (por fases, sin abrir las compuertas)
        ↓
5. /saas_launch_fortalecer_pmf        ← después del día de lanzamiento: iterás hacia el product-market fit
```

Todo lo demás es **complementario**: lo corrés cuando el principal te lo pida, cuando se cumpla una condición, o cuando quieras profundizar un paso.

---

## Tabla de decisión

| Comando | Rol | ¿Cuándo lo corro? |
|---|---|---|
| **`/saas_idea_encontrar_idea`** | 🟦 **Principal** | Punto de entrada, **solo si no tenés idea**. Si ya la tenés, saltalo. |
| `/saas_idea_validar_idea` | ⬜ Complementario *(filtro opcional)* | Filtro de escritorio rápido (18 factores) para **matar ideas flojas** antes de gastar horas. Opcional. |
| **`/saas_idea_validar_2_20_200`** | 🟦 **Principal** *(director)* | **El que conduce toda la validación.** Delega la Fase 2 y la Fase 20 y respeta los gates. Corré este y dejate llevar. |
| `/saas_idea_prevalidar_2h` | ⬜ Complementario *(delegado)* | Lo invoca el director (Fase 2). Podés correrlo standalone si querés solo la pre-validación de ~2h. |
| `/saas_idea_validar_20h` | ⬜ Complementario *(delegado)* | Lo invoca el director (Fase 20). Podés correrlo standalone para la validación de campo. |
| `/saas_idea_campana_llamadas` | ⬜ Complementario *(motor)* | Motor del **Approach 1** (hablar con gente) dentro de la Fase 20. |
| `/saas_idea_campana_landing` | ⬜ Complementario *(motor)* | Motor del **Approach 2** (landing + tráfico) dentro de la Fase 20. |
| `/saas_build_marketing_antes_de_codear` | ⬜ Complementario *(gate de actitud)* | **Antes de escribir una línea** en la Fase 200. Encuadre "marketear antes de codificar"; hace handoff a la lista. |
| **`/saas_build_mvp_5pasos`** | 🟦 **Principal** | Conduce el **plan y la construcción del MVP** (5 pasos + gate anti-código). |
| `/saas_build_mvp_tips_dev` | ⬜ Complementario *(condicional)* | **Solo si** el approach termina siendo **full code**. Tips de Derek Reimer para no sobre-construir. |
| `/saas_idea_evaluar_ia` | ⬜ Complementario *(condicional)* | **Solo si** el MVP incorpora **IA**. Gate "¿IA es el approach correcto?" + 16 riesgos. |
| **`/saas_build_lista_lanzamiento`** | 🟦 **Principal** | Conduce el armado de la **lista de lanzamiento**. Se corre **en paralelo** al MVP. |
| **`/saas_build_pricing`** | 🟦 **Principal** | Conduce la decisión del **primer precio**. Conviene definirlo **temprano**. |
| **`/saas_launch_lanzamiento_por_fases`** | 🟦 **Principal** | Conduce el **lanzamiento** (5 pasos o por fases). Cuando el MVP está completo, la lista nutrida y el precio definido. |
| **`/saas_launch_fortalecer_pmf`** | 🟦 **Principal** | Conduce el **post-lanzamiento**: hablar con clientes, filtrar requests, medir el PMF. |
| `/saas_launch_ventas_fundador` | ⬜ Complementario *(motor)* | El **CÓMO** de las ventas high-touch (founder-led sales) que piden el lanzamiento por fases y el fortalecimiento del PMF. |
| `/saas_idea_preguntas_entrevista` | 🟨 Transversal *(motor de preguntas)* | Cuando vas a **entrevistar** a alguien (validación, PMF o ventas) y querés un set de preguntas **Mom Test** a medida del contexto. Lo podés invocar desde `validar_20h`/`campana_llamadas` o suelto. |
| `/saas_idea_icp` | 🟨 Transversal *(panel del ICP)* | Para **ver/corregir** el perfil del comprador. El ICP se **enriquece solo** desde toda la cadena; este comando es el panel (ver, inicializar, re-detectar, fusionar/separar). |
| `/saas_launch_cuando_abandonar` | 🟨 Transversal *(decisión)* | Cuando **"algo no se siente bien"** y dudás si seguir. Invocable **desde cualquier etapa**. |
| `/saas_idea_sync_drive` | 🟨 Transversal *(utilitario)* | Cuando editaste los Docs **directo en Drive** y querés traer esos cambios de vuelta a `data/`. |

🟦 = lo iniciás vos · ⬜ = se corre dentro/según condición · 🟨 = se corre cuando lo necesitás, sin orden fijo

---

## Fase por fase: "yo corro…"

### Fase IDEA — encontrar y validar
- **Corré:** `/saas_idea_validar_2_20_200` (si no tenés idea, antes `/saas_idea_encontrar_idea`).
- **Él se encarga de:** `prevalidar_2h` (2h) y `validar_20h` (20h), que a su vez usan `campana_llamadas` y `campana_landing`.
- **Opcional:** `/saas_idea_validar_idea` como filtro de escritorio previo.
- ⚠️ **No avanzás a la fase siguiente si el gate no es 🟢.**

### Fase BUILD — construir el MVP (~200h)
- **Antes de codear:** `/saas_build_marketing_antes_de_codear` (gate de actitud).
- **Corré (principales):** `/saas_build_mvp_5pasos` + `/saas_build_lista_lanzamiento` (en paralelo) + `/saas_build_pricing`.
- **Según condición:** `/saas_build_mvp_tips_dev` solo si es **full code**; `/saas_idea_evaluar_ia` solo si usa **IA**.

### Fase LAUNCH — lanzar y fortalecer (~día de lanzamiento y después)
- **Corré (principales):** `/saas_launch_lanzamiento_por_fases` → después `/saas_launch_fortalecer_pmf`.
- **Motor de apoyo:** `/saas_launch_ventas_fundador` para liderar tus ventas high-touch (onboarding 1-a-1, pre-venta, deals de ACV alto).

### Transversal — en cualquier momento
- `/saas_idea_preguntas_entrevista` para generar un set de preguntas Mom Test a medida antes de entrevistar (validación, PMF o ventas).
- `/saas_idea_icp` para ver o corregir el perfil del comprador (el ICP se va llenando solo desde los demás comandos; este es el panel de control).
- `/saas_launch_cuando_abandonar` cuando dudás si seguir.
- `/saas_idea_sync_drive` para sincronizar Drive → `data/`.

---

## Reglas de oro de navegación

1. **Empezá siempre por un principal.** Los complementarios los dispara él o una condición; rara vez los corrés "por las tuyas".
2. **Respetá los gates.** No saltes a la fase siguiente con un veredicto 🟡 o 🔴.
3. **No escribís código hasta pasar la Fase 20.** Toda la validación existe para no tirar las ~200h del MVP.
4. **Los condicionales son opt-out, no opt-in:** si el approach no es full code, salteá `tips_dev`; si no hay IA, salteá `evaluar_ia`.
5. **Escalá horas solo cuando la señal lo justifica** (2 → 20 → 200) y **no inventes datos** (si no hay dato real, se pide y se pausa).

> Para el detalle completo de cada comando, qué archivo escribe y cómo se conectan entre sí, mirá el [`README.md`](README.md).
