# Instrucciones del proyecto

## Referencias de comandos (imágenes, PDFs, diagramas)

El material de conocimiento **estable** que consume un comando (imágenes, PDFs, diagramas,
plantillas visuales, screenshots de ejemplo) vive en `.claude/assets/` y **se versiona
en git**. Es "parte del comando", no datos de una idea.

- Una subcarpeta por comando, nombrada **sin el prefijo `saas_idea_`** (ej. el comando
  `saas_idea_campana_landing.md` → `.claude/assets/campana_landing/`).
- Referencias usadas por varios comandos → `.claude/assets/_compartido/`.
- Desde el `.md` del comando, referenciá con la ruta del repo
  `.claude/assets/<comando>/<archivo>`.
- **Importante:** NO va en `.claude/commands/assets/` — todo `.md` bajo `.claude/commands/`
  se registra como slash command y ensuciaría la lista. Por eso vive en `.claude/assets/`.
- Ver `.claude/assets/README.md` para la convención completa.

> Material específico de **una idea** (screenshot de SimilarWeb, pricing page de un competidor,
> capturas de ads) NO va acá: va en `data/idea-NNN-<slug>/<fase>/assets/` y se espeja a Drive.

## Directorio raíz de trabajo en Google Drive

Todo el trabajo en Google Drive (vía el MCP server `google-workspace`, cuenta `gustavo.dohara.infoproductos@gmail.com`) debe ocurrir **dentro de esta carpeta**, que actúa como directorio raíz del proyecto:

- **Carpeta raíz:** `analisis de ideas`
- **ID:** `1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig`
- **Link:** https://drive.google.com/drive/folders/1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig

### Reglas

1. **Nunca** crear archivos ni carpetas en la raíz del Drive (`root`). Todo va dentro de `analisis de ideas` o de subcarpetas de esa carpeta.
2. **Subcarpetas:** usar `create_drive_folder` con `parent_folder_id=1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig` (o el ID de una subcarpeta existente).
3. **Archivos genéricos:** usar `create_drive_file` con `folder_id=1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig` (o subcarpeta).
4. **Google Docs / Sheets:** las herramientas `create_doc` y `create_spreadsheet` crean en `root` (no aceptan carpeta destino). Después de crear, **mover inmediatamente** el archivo a la carpeta con:
   `update_drive_file(file_id=<nuevo id>, add_parents="1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig", remove_parents="root")`
5. Si el usuario pide organizar por tema/idea, crear una subcarpeta dentro de `analisis de ideas` y trabajar ahí.

## Espejo en Google Drive de los tableros de `data/`

Los comandos de validación de ideas persisten su trabajo en archivos Markdown dentro de `data/` (en la raíz del repo). **`data/` es la copia de trabajo viva**: se actualiza de forma incremental durante la sesión. Además de eso, **todo lo recolectado debe espejarse en Google Drive como Google Docs nativos**, en la carpeta de fase correspondiente.

### Mapeo de carpetas `data/` → Drive

La estructura es **una carpeta por idea** y, dentro, las carpetas de fase — espeja 1:1 a `data/`. La raíz en Drive es **`analisis de ideas`** (ID `1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig`).

| Carpeta local | Carpeta Drive | ID de carpeta Drive |
|---|---|---|
| `data/idea-001-deploys-shopify-sin-visibilidad/` | `analisis de ideas/idea-001-deploys-shopify-sin-visibilidad` | `1aabUmpDoEXA6nguKROSIxpyP1YUH4ZsF` |
| &nbsp;&nbsp;↳ `1-idea_phase/` | `…/1-idea_phase` | `16dsKtCGwhqi6oD4beGOD7Y8h6BSwDgyE` |
| &nbsp;&nbsp;↳ `2-build_phase/` | `…/2-build_phase` | `1axwW5A19VLh7pIvVfkjaKgpsTigdGHSe` |
| &nbsp;&nbsp;↳ `3-launch_phase/` | `…/3-launch_phase` | `1RzK3Nd31OdqLd6jl4qrFvDBmoc-Qp_gI` |
| `data/idea-002-staging-environments-shopify/` | `analisis de ideas/idea-002-staging-environments-shopify` | `1_gTaRkbcxM_ceHYc5CKUZVIrrxAmGBAG` |
| &nbsp;&nbsp;↳ `1-idea_phase/` | `…/1-idea_phase` | `1RnWiHwyJaJpMhr9jS9QNRGVedM-dc3zL` |
| &nbsp;&nbsp;↳ `2-build_phase/` | `…/2-build_phase` | `1MWj2yJ_LYmpXxDsI_Fsd9_7-2CQ77ATH` |
| &nbsp;&nbsp;↳ `3-launch_phase/` | `…/3-launch_phase` | `1gE8GOVpJGALMNYPlAx1cEiclud7XhhYd` |

El archivo **compartido** `data/perfil-fundador.md` (no pertenece a ninguna idea) se espeja en la **raíz** de `analisis de ideas` (ID `1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig`) como Doc `perfil-fundador` (ID `1ikMKjSuxzVfcuBoBDMMgthsjXf03raCGHM0vl4sN2ms`).

**Cuando aparece una idea nueva** (`data/idea-NNN-<slug>/`): creá en Drive su carpeta bajo `analisis de ideas` con `create_drive_folder(parent_folder_id="1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig")`, después sus 3 subcarpetas de fase **dentro** de esa carpeta de idea, y agregá las filas a esta tabla. Si no tenés a mano el ID de una carpeta, ubicala con `search_drive_files(query="name = '<nombre>' and '<parent-id>' in parents and mimeType = 'application/vnd.google-apps.folder' and trashed = false")`.

### Cuándo espejar

Cada vez que guardes/actualices un archivo en `data/` (los momentos en que avisás **"📝 Guardado en el tablero"**), espejá ese mismo archivo a Drive en la misma operación. `data/` es la fuente de verdad; el Doc de Drive es un reflejo fiel del `.md` completo y actualizado.

### Cómo espejar (sin duplicar)

El nombre del Doc = el nombre del archivo local **sin la extensión `.md`** (ej. `idea`, `icp`, `prevalidacion`, `validacion`, `validacion-campo` en `1-idea_phase/`; `plan-mvp`, `evaluacion-ia`, `mvp-codigo`, `premarketing`, `lista-lanzamiento` y `pricing` en `2-build_phase/`; `plan-lanzamiento`, `fortalecer-pmf`, `ventas-fundador` y `cuando-abandonar` en `3-launch_phase/`). La idea queda identificada por la **carpeta** (`idea-NNN-<slug>/<fase>/`), no por el nombre del archivo; por eso el Doc dedup se busca **scopeado a la carpeta de fase de esa idea** (ojo: `plan-mvp`, `evaluacion-ia`, `mvp-codigo`, `premarketing`, `lista-lanzamiento` y `pricing` se espejan en la carpeta espejo `2-build_phase/`, no en `1-idea_phase/`; y `plan-lanzamiento`, `fortalecer-pmf`, `ventas-fundador` y `cuando-abandonar` se espejan en `3-launch_phase/`). Eso garantiza que las actualizaciones reencuentren el Doc existente y no creen copias.

1. **Buscá si ya existe** el Doc en la carpeta de fase **de esa idea**:
   `search_drive_files(query="name = '<nombre-sin-md>' and '<ID-carpeta-fase-de-la-idea>' in parents and trashed = false")`
2. **Si NO existe → crealo** convirtiendo el Markdown a Doc nativo, pasando el contenido inline (los tableros son chicos, no hace falta archivo intermedio):
   `import_to_google_doc(file_name="<nombre-sin-md>", content="<contenido completo del .md>", folder_id="<ID-carpeta-fase>")`
3. **Si YA existe → actualizalo en sitio** (preserva ID, link, comentarios y permisos), reemplazando el contenido con el `.md` completo y actualizado:
   `update_drive_file(file_id="<id-del-doc>", content="<contenido completo del .md>", source_format="md")`

> **Gotcha:** `import_to_google_doc` con `file_path` solo lee desde `~/.workspace-mcp/attachments` (`ALLOWED_FILE_DIRS`). Por eso, para espejar tableros, **pasá el contenido inline con `content=`** y evitás copiar archivos. No anuncies cada espejo como paso aparte: alcanza con el "📝 Guardado en el tablero" habitual (incluye el espejo en Drive).

## Protocolo de ICP (`icp.md`) — construcción incremental

El **ICP** (Ideal Customer Profile / perfil del comprador) es la **fuente única de verdad del "para quién"** de una idea. Vive en **`data/idea-NNN-<slug>/1-idea_phase/icp.md`** (espejo en Drive como Doc `icp` en la carpeta `1-idea_phase/` de la idea). Reemplaza la práctica anterior de redefinir el "para quién" en cada tablero: ahora el ICP se **construye una vez y se enriquece** a medida que la idea avanza.

> **Importante:** ningún comando crea el ICP "de una sola vez". Se construye **incrementalmente**: cada comando que aprende algo del comprador **vuelca ese dato en `icp.md`** (además de en su propio tablero). El comando gestor `/saas_idea_icp` es el panel de control (ver / inicializar / re-detectar / fusionar-separar), pero el grueso del ICP se llena solo desde la cadena.

### Un archivo, 1 o N perfiles

`icp.md` es **un solo archivo** con una **sección `## ICP #N — <slug-del-perfil>`** por perfil de comprador detectado. El **ICP #1 es el primario** (foco del lanzamiento); los demás son secundarios. Cada idea tiene su propio `icp.md`.

### Modelo de cada ICP (campos, fiel a Walling + operativo)

Cada sección `## ICP #N` lleva estos campos. Lo que todavía no se sabe se marca **`⏳ pendiente`** (no se inventa):

- **Rol / industria** — quién es, lo más acotado posible (niche down).
- **Problema agudo** — su dolor #1, en su lenguaje (no la solución).
- **Quién paga (Purchaser)** — ¿es quien sufre el problema?, presupuesto, qué tan fácil es venderle.
- **Dónde se junta** — comunidades / canales / outlets concretos por donde se lo alcanza.
- **Alternativa actual** — contra qué competís (software, una Google Sheet, no hacer nada).
- **Disposición / capacidad de pago** — señal de pricing (rango que toleraría, ACV esperado).
- **Evidencia / citas** — señal real con fuente (yeses, opt-ins, citas de entrevistas, pre-ventas).
- **Procedencia** — qué comando aportó cada dato y la fecha (memoria acumulativa y fechada).

### Detección: ¿es el mismo ICP o un perfil nuevo?

Cuando un comando ve datos del comprador, decide si **enriquece** un ICP existente o si es **candidato a perfil nuevo**. Es candidato a **ICP separado** si cambia **al menos uno de los ejes duros**:

1. **Rol / industria** central distinto.
2. **Quién paga** distinto (otro decisor, otro presupuesto).
3. **Problema central** distinto (otro job-to-be-done).
4. **Canal** donde se junta distinto (se lo alcanza de otra forma).

Si solo cambian **matices** (tamaño de empresa, geografía, seniority) → es el **mismo ICP** (a lo sumo un segmento dentro de él), no un perfil nuevo.

### Protocolo de aviso + confirmación (SIEMPRE)

Antes de tocar `icp.md`, el comando avisa y, según el caso, **pide confirmación**:

- 🆕 **Crear el primer ICP** (no existe `icp.md` todavía): *"Detecté el ICP de esta idea: \<resumen de 1 línea>. ¿Lo creo como ICP #1?"* → **esperá el OK** antes de escribir.
- ➕ **Perfil nuevo detectado** (≥1 eje duro divergente): *"Esto parece un perfil distinto al ICP #N (por \<eje que cambió>). ¿Creo un ICP nuevo o lo sumo al #N?"* → **esperá la decisión** del fundador. Si confirma, creás la nueva sección `## ICP #(N+1)`.
- ❓ **Falta info de un campo** que el comando necesita y que solo el fundador tiene: **preguntásela** (modo pausa), no la inventás. Mientras no llegue, queda `⏳ pendiente`.
- 🔄 **Enriquecer un ICP existente** (mismo perfil, más data): hacelo **sin bloquear** y resumilo en una línea, incluido en el **"📝 Guardado en el tablero"** habitual (que ya incluye el espejo a Drive).

> En resumen: **crear (uno o varios) ICP siempre se confirma con el fundador; enriquecer no bloquea pero se avisa.** Nunca se inventan datos de comprador: si no hay dato real, se pide o se marca `⏳ pendiente`.

### Qué comando aporta qué (cadena de enriquecimiento)

| Comando | Qué dato del comprador aporta al ICP |
|---|---|
| `/saas_idea_encontrar_idea` | **Siembra**: rol/industria y problema (el "para quién" inicial). |
| `/saas_idea_prevalidar_2h` | **Purchaser** (quién paga, presupuesto), consumer vs buyer, alternativa actual. |
| `/saas_idea_validar_20h` | Señal real de campo: a quién contactó, quién respondió, citas. |
| `/saas_idea_campana_llamadas` | Citas del dolor, yeses calificados, pre-ventas (disposición a pagar). |
| `/saas_idea_campana_landing` | Quién convierte en la landing, por qué canal (dónde se junta). |
| `/saas_build_lista_lanzamiento` | Canales/hangouts que funcionan, % por origen (refina "dónde se junta"). |
| `/saas_build_pricing` | Segmentos de cliente → puede **detectar perfiles distintos** (1 o N). |
| `/saas_launch_fortalecer_pmf` | Clientes reales, los que no compraron, los que churnearon (refina/parte perfiles). |
| `/saas_launch_ventas_fundador` | Prospectos high-touch reales, objeciones, quién cierra. |
