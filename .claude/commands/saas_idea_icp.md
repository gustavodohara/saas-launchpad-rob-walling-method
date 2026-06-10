---
description: Panel de control del ICP (Ideal Customer Profile / perfil del comprador) de una idea de SaaS. NO es donde se crea el ICP de cero —eso pasa solo, incrementalmente, desde los demás comandos de la cadena (encontrar_idea → prevalidar → validar → campañas → lista → pricing → fortalecer PMF → ventas)—, sino donde lo VES y lo CORREGÍS. Tiene 4 funciones: (1) VER/CONSOLIDAR el/los ICP de la idea con su procedencia (qué comando aportó cada dato) y qué campos están ⏳ pendientes; (2) INICIALIZAR a mano el primer ICP si todavía no corriste la cadena; (3) RE-DETECTAR perfiles escaneando todos los tableros de la idea (validación, llamadas, landing, lista, pricing, PMF, ventas) por compradores que se colaron como "más data" cuando eran un perfil distinto; (4) FUSIONAR/SEPARAR/editar perfiles a mano cuando la detección automática se equivocó. Trabaja sobre el archivo único 1-idea_phase/icp.md (una sección ## ICP #N por perfil, el #1 es el primario) y lo espeja a Drive. Respeta el Protocolo de ICP de CLAUDE.md: avisa y pide confirmación al crear uno o varios ICP, y te pide la info faltante sin inventarla.
argument-hint: "[acción opcional: ver | init | redetectar | fusionar | separar] + [idea: número (001), slug, o vacío = la idea del contexto]"
---

# ICP — panel de control del perfil del comprador

Sos el **gestor del ICP** de una idea de SaaS. El ICP (perfil del comprador / Ideal Customer Profile) es la **fuente única de verdad del "para quién"**. Tu trabajo acá **no** es entrevistar al fundador desde cero para inventar un avatar: es **ver, consolidar y corregir** el/los ICP que la cadena de comandos fue construyendo, y —solo si hace falta— inicializarlo o reparar la detección de perfiles.

> **Leé primero `CLAUDE.md` → "Protocolo de ICP (`icp.md`) — construcción incremental".** Ahí están el formato del archivo, el modelo de campos, la heurística de detección 1-o-N y el protocolo de aviso + confirmación. Este comando **ejecuta** ese protocolo; no lo repite.

$ARGUMENTS

---

## Memoria persistente — LEÉ ESTO ANTES DE NADA

La persistencia vive en **una carpeta por idea**: `data/idea-NNN-<slug>/`, con subcarpetas de fase. El ICP es **transversal** pero su archivo vive en la fase de idea (es donde nace): **`data/idea-NNN-<slug>/1-idea_phase/icp.md`** (ej: `data/idea-001-deploys-shopify-sin-visibilidad/1-idea_phase/icp.md`).

1. **Ubicá la idea.** Si el argumento trae un número (`001`) o un slug, usá esa carpeta. Si viene vacío, usá la idea del contexto de la sesión; si hay ambigüedad, listá las carpetas `data/idea-*/` y pedile al fundador que elija. **No** crees una idea nueva desde este comando (el ICP cuelga de una idea que ya existe).
2. **Leé `1-idea_phase/icp.md` si existe.** Si no existe, estás en el caso **inicializar** (función 2). Si existe, leelo entero antes de cualquier acción.
3. **A medida que cambiás el ICP**, actualizá el archivo, refrescá la fecha y avisá **"📝 Guardado en el tablero"**. La memoria es **acumulativa y fechada**.
4. **Espejá en Google Drive.** Cada "📝 Guardado en el tablero" refleja `icp.md` como Doc nativo `icp` en la carpeta espejo `analisis de ideas/idea-NNN-<slug>/1-idea_phase/`, según **`CLAUDE.md` → "Espejo en Google Drive de los tableros de `data/`"** (buscar→crear/actualizar sin duplicar, contenido inline). Incluido en el mismo guardado, no como paso aparte.

---

## Las 4 funciones

Si el argumento trae una acción explícita (`ver`/`init`/`redetectar`/`fusionar`/`separar`), andá directo a ella. Si no, **por defecto hacé "ver"** (función 1) y, al final, ofrecé las demás según lo que encontraste (ej. si detectás un perfil mal clasificado, ofrecé separar).

### 1. Ver / consolidar (la más usada)

Mostrá el estado del/los ICP de la idea, leído de `icp.md`:

- **Cuántos perfiles hay** y cuál es el **primario** (ICP #1).
- Para cada uno, los campos del modelo (rol/industria, problema agudo, quién paga, dónde se junta, alternativa actual, disposición a pagar, evidencia/citas).
- **Qué está completo y qué está `⏳ pendiente`**, y de **qué comando vino cada dato** (el mapa de procedencia).
- Un **diagnóstico corto**: ¿el ICP primario está lo bastante **acotado** para targetear (niche down), o es "todo el planeta"? ¿Hay campos críticos pendientes (sobre todo *quién paga* y *dónde se junta*)?

No pidas datos nuevos en esta función salvo que el fundador quiera completar un `⏳ pendiente` ahí mismo.

### 2. Inicializar a mano

Solo si **no existe `icp.md`** (o el fundador quiere arrancar el ICP antes de correr la cadena). Entrevistá por los **campos mínimos** —rol/industria, problema agudo, quién paga, dónde se junta— y escribí el primer `## ICP #1`. Lo que no sepa queda `⏳ pendiente`. **Aplicá el protocolo de aviso + confirmación de `CLAUDE.md`**: avisá *"voy a crear el ICP #1: \<resumen>. ¿Lo creo?"* y esperá el OK. No inventes campos; lo que falta se completa después desde la cadena.

### 3. Re-detectar perfiles

Cuando el ICP creció desordenado. **Re-escaneá los tableros de la idea** en busca de compradores que se colaron como "más data" cuando en realidad eran un **perfil distinto** (aplicá la heurística de los 4 ejes duros de `CLAUDE.md`). Fuentes a leer en la carpeta de la idea:

- `1-idea_phase/`: `idea.md`, `prevalidacion.md`, `validacion-campo.md`, `campana-llamadas.md`, `campana-landing.md`.
- `2-build_phase/`: `pricing.md` (segmentos → tiers suele revelar N perfiles), `lista-lanzamiento.md`.
- `3-launch_phase/`: `plan-lanzamiento.md`, `fortalecer-pmf.md` (clientes / churneados / los que no compraron), `ventas-fundador.md`.

Presentá los **perfiles candidatos** que encontraste y **proponé** crear/separar → el fundador confirma (protocolo de confirmación). No reescribas sin OK.

### 4. Fusionar / separar / editar (válvula de escape)

Para cuando la detección automática se equivocó:

- **Fusionar:** dos secciones que son el mismo comprador → unilas en una (conservá la evidencia de ambas y la procedencia).
- **Separar:** una sección que esconde dos compradores distintos → partila en dos `## ICP #N` (re-numerá y definí cuál queda primario).
- **Editar / archivar:** corregí un campo, o marcá un perfil como **descartado** (no lo borres: dejalo como `## ICP #N — <slug> (descartado AAAA-MM-DD: motivo)`) para no perder el historial.

Toda fusión/separación se **confirma** antes de escribir, y se registra con fecha en la procedencia.

---

## Estructura de `icp.md`

Un solo archivo, una sección por perfil. El **ICP #1 es el primario**. Cuando lo crees o actualices, seguí esta estructura:

```markdown
# ICP — <nombre de la idea>

> Perfil(es) del comprador de esta idea. Fuente única de verdad del "para quién".
> Se construye incrementalmente desde la cadena de comandos (ver CLAUDE.md → Protocolo de ICP).
> Última actualización: AAAA-MM-DD

## ICP #1 — <slug-del-perfil> (primario)

- **Rol / industria:** ...
- **Problema agudo (su dolor #1):** ...
- **Quién paga (Purchaser):** ¿= quien sufre? · presupuesto · facilidad de venta: ...
- **Dónde se junta:** <comunidades / canales / outlets concretos>
- **Alternativa actual:** <software / Google Sheet / no hacer nada>
- **Disposición / capacidad de pago:** <rango / ACV esperado>
- **Evidencia / citas (con fuente):** ...
- **Procedencia:** <campo ← comando (AAAA-MM-DD)>; ...

## ICP #2 — <slug-del-perfil>
(mismos campos; solo si se confirmó un perfil distinto por ≥1 eje duro)
```

> Si solo hay un perfil, queda solo `## ICP #1`. No fuerces perfiles secundarios: Walling empuja a **nichar** (niche down). Crear el #2, #3… **siempre** se confirma con el fundador.

---

## Reglas de oro

1. **No inventás datos de comprador.** Lo que no se sabe es `⏳ pendiente`; lo que solo tiene el fundador, se lo pedís.
2. **Crear (uno o varios) ICP siempre se confirma.** Avisás y esperás el OK (protocolo de `CLAUDE.md`). Enriquecer no bloquea, pero se avisa.
3. **Este comando no entrevista de cero salvo en "inicializar".** Su valor es consolidar y reparar, no duplicar la cadena.
4. **Una idea = un `icp.md`**, con 1 o N secciones. El primario manda el foco.
