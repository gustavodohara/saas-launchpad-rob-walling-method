---
description: Sincroniza Google Drive → carpeta local `data/` (el camino inverso del espejo que ya existe). Recorre cada idea y fase, compara cada Google Doc del Drive contra su archivo `.md` local NORMALIZANDO el ruido de la conversión Doc↔Markdown (espacios, saltos, estilos de heading, viñetas), clasifica el estado de cada par (en sync / solo en Drive / solo local / difieren) y, ante cualquier inconsistencia real, TE AVISA con el diff y te deja decidir qué gana. NUNCA sobreescribe ni borra nada sin tu confirmación explícita.
argument-hint: "[idea opcional: número (001), slug, o vacío = todas las ideas + perfil-fundador]"
---

# Sincronización Google Drive → `data/` (inverso del espejo)

Eres un **asistente de sincronización**. El proyecto ya tiene un mecanismo **`data/` → Drive** (definido en `CLAUDE.md`, sección "Espejo en Google Drive de los tableros de `data/`"): `data/` es la fuente de verdad y los Google Docs son su reflejo. Este comando hace el **camino inverso y reconciliador**: trae a `data/` lo que cambió en Drive y, cuando los dos lados no coinciden, **no decide solo** — te muestra qué difiere y vos elegís.

> Por qué existe: editás (o alguien edita) un Doc directo en Drive — comentarios resueltos, un párrafo agregado, un número actualizado — y ese cambio nunca vuelve a `data/`. Sin reconciliación, los dos lados divergen en silencio. Este comando es el que los vuelve a juntar, **bajo tu control**.

## Qué SÍ hace y qué NO hace

**SÍ:**
- Recorre las ideas y fases mapeadas en `CLAUDE.md` (o la idea que le pases como argumento) y, además, el archivo compartido `perfil-fundador`.
- Para cada par (`.md` local ↔ Doc de Drive) **compara contenido normalizado** (ver "Normalización") y clasifica el estado.
- Presenta un **reporte** de todo lo que está fuera de sync, con un diff legible de los cambios reales.
- Resuelve **una inconsistencia a la vez**, aplicando solo lo que vos confirmás.

**NO:**
- **No borra ni sobreescribe nada sin tu OK explícito.** Ni un `.md`, ni un Doc.
- **No inventa contenido** ni "mergea" a ciegas: si elegís merge, te muestro ambos lados y vos dictás el resultado.
- No toca archivos fuera de `data/` ni Docs fuera de la carpeta `analisis de ideas`.

## Regla de oro — CERO destrucción sin confirmar

1. Toda operación que **escriba** (bajar de Drive sobreescribiendo el `.md`, subir local pisando el Doc, crear, o borrar de cualquier lado) requiere **confirmación explícita tuya para ESE archivo**. No hay "aplicar todo" automático salvo que vos lo pidas tras ver el reporte.
2. **`data/` está en git.** Antes de aplicar cambios que sobreescriban archivos locales, recordá/recordame que conviene tener el working tree limpio o commiteado, así cualquier pull es reversible con `git`. Si hay cambios sin commitear en `data/`, avisalo antes de pisar.
3. Cuando una resolución implique **borrar** (un `.md` que ya no está en Drive, o un Doc que ya no está local), tratalo como la decisión más delicada: explicá explícitamente que el archivo fue creado por vos o no, y que borrar es difícil de deshacer. Por default **NO borres** — ofrecé recrear el lado faltante. Borrar solo si lo pedís sin ambigüedad.

## Antes de nada — leé el mapa

1. **Leé `CLAUDE.md`**, sección "Espejo en Google Drive de los tableros de `data/`". De ahí salen: la carpeta raíz de Drive (`analisis de ideas`, ID `1OL-GWgEu_7CirAvHtjhyg0yVkKp3Edig`), la **tabla de mapeo** `data/` ↔ IDs de carpetas de Drive por idea y fase, y la regla del `perfil-fundador` compartido.
2. Usá `gustavo.dohara.infoproductos@gmail.com` como `user_google_email` en todas las herramientas de `google-workspace`.
3. **Alcance (scope) según `$ARGUMENTS`:**

   > $ARGUMENTS

   - **Vacío** → sincronizá **todas** las ideas (`data/idea-*/`) + `perfil-fundador`.
   - **Un número** (`001`, `2`) o **un slug** (`staging-environments-shopify`) → scopeá solo a esa idea (`data/idea-NNN-<slug>/` y su carpeta espejo). No toques las demás.

## Normalización — qué cuenta como "inconsistencia real"

El Doc de Drive nace de convertir el Markdown a Doc nativo; al traerlo de vuelta con `get_doc_as_markdown` reaparece con **ruido de ida y vuelta** que NO es un cambio de contenido. Si comparás byte-a-byte, todo da "distinto" y el reporte es inútil. Por eso comparás **versiones normalizadas** de ambos lados. Antes de comparar, aplicá a las dos cadenas:

- **Saltos de línea:** normalizá `\r\n`/`\r` → `\n`.
- **Espacios finales:** quitá whitespace al final de cada línea.
- **Líneas en blanco:** colapsá 2+ líneas en blanco consecutivas a una sola; quitá líneas en blanco al inicio/fin del archivo.
- **Headings:** normalizá el estilo (`#`, `##`, …) y un solo espacio tras los `#`; tratá heading "Setext" (subrayado con `===`/`---`) como equivalente a su `#`/`##`.
- **Viñetas:** tratá `*`, `-`, `+` de lista como equivalentes (normalizá a `-`); normalizá la sangría de listas a múltiplos consistentes.
- **Énfasis:** tratá `*texto*`/`_texto_` y `**texto**`/`__texto__` como equivalentes.
- **Tablas:** normalizá espacios internos de celdas y los `|` de borde; ignorá el ancho de la fila separadora (`---|---`).
- **Comillas/guiones:** normalizá comillas tipográficas (`" "` `' '`) a rectas y `—`/`–` de forma consistente, **solo** para la comparación.
- **Enlaces e imágenes:** compará el texto y el destino, no el formateo alrededor.

> La normalización es **solo para decidir si difieren**. Cuando escribas (en cualquier dirección), escribí el contenido **fiel y completo**, no el normalizado.

**Resultado de la comparación de cada par:**
- Normalizado **igual** → `EN SYNC` (no hagas nada, ni siquiera reescribas).
- Normalizado **distinto** → `DIFIEREN` (inconsistencia real: hay que mostrar diff y preguntar).

## Procedimiento de escaneo

Para el scope elegido, construí el inventario de los dos lados y emparejá:

1. **Lado local:** listá los `.md` bajo `data/idea-NNN-<slug>/<fase>/` (fases: `1-idea_phase`, `2-build_phase`, `3-launch_phase`) y el `data/perfil-fundador.md` compartido. Ignorá `.gitkeep`.
2. **Lado Drive:** para cada carpeta de fase, obtené su **ID** desde la tabla de `CLAUDE.md`. Si una idea/fase **no está en la tabla**, ubicá la carpeta con
   `search_drive_files(query="name = '<nombre>' and '<parent-id>' in parents and mimeType = 'application/vnd.google-apps.folder' and trashed = false")`.
   Luego listá los Docs nativos de esa carpeta con `list_docs_in_folder(folder_id=<ID-fase>)`.
3. **Emparejamiento:** la identidad es **carpeta de fase + nombre** (Doc `validacion` ↔ `validacion.md`, etc.; el Doc va **sin** la extensión `.md`). Emparejá por nombre dentro de la misma carpeta de fase.
4. Para cada par emparejado, traé el Markdown del Doc con `get_doc_as_markdown(<doc-id>)`, leé el `.md` local, **normalizá ambos** y clasificá.
5. **Discrepancias de carpeta también cuentan:** una idea que existe en `data/` pero no tiene carpeta espejo en Drive (o al revés) es una inconsistencia de nivel carpeta — reportala igual.

### Estados posibles

| Estado | Situación | Acción que vas a ofrecer |
|---|---|---|
| `EN SYNC` | Local y Drive iguales (normalizado) | Nada. |
| `DIFIEREN` | Ambos existen, contenido real distinto | Mostrar diff. ¿Gana Drive (pull→pisa local) / gana local (push→pisa Doc) / merge manual? |
| `SOLO EN DRIVE` | Hay Doc, no hay `.md` local | ¿Bajar (crear el `.md`) o lo borraste local a propósito (entonces ofrecer borrar el Doc)? |
| `SOLO LOCAL` | Hay `.md`, no hay Doc | ¿Subir al Drive (crear el Doc, como el espejo normal) o lo borraste en Drive a propósito (entonces ofrecer borrar el `.md`)? |
| `CARPETA SOLO LOCAL` | Idea en `data/`, sin carpeta espejo en Drive | Ofrecer crear la carpeta de idea + 3 subcarpetas de fase y agregar la fila a la tabla de `CLAUDE.md`. |
| `CARPETA SOLO EN DRIVE` | Carpeta de idea en Drive, sin `data/` | Ofrecer crear el árbol local `data/idea-NNN-<slug>/` y bajar sus Docs. |

## Reporte — primero el panorama, después resolvés

Tras escanear, **antes de tocar nada**, mostrá un reporte compacto. Agrupá por idea/fase y listá solo lo que NO está en sync (los `EN SYNC` resumilos en un conteo). Ejemplo:

```
Escaneo de sincronización — 2026-06-07
Scope: todas las ideas + perfil-fundador

idea-001-deploys-shopify-sin-visibilidad
  1-idea_phase
    idea.md            ✅ EN SYNC
    prevalidacion.md   ⚠️ DIFIEREN      (Drive tiene cambios no presentes local)
    validacion.md      ⬇️ SOLO EN DRIVE (no existe data/.../validacion.md)
idea-002-staging-environments-shopify
  1-idea_phase
    prevalidacion.md   ⬆️ SOLO LOCAL    (no existe el Doc en Drive)
perfil-fundador        ✅ EN SYNC

Resumen: 1 en sync · 1 difiere · 1 solo en Drive · 1 solo local · 0 conflictos de carpeta
```

Si **todo está en sync**, decílo y terminá (no preguntes nada).

## Resolución — una inconsistencia a la vez

Recorré las discrepancias **de a una**, en orden del reporte. Para cada una:

1. **Mostrá el diff real.** Para `DIFIEREN`, mostrá un diff legible de las versiones (idealmente normalizadas para resaltar el cambio de fondo, indicando qué lado tiene cada línea). Sé concreto: "Drive agregó este párrafo", "local tiene este número, Drive otro".
2. **Preguntá qué hacer** (una sola pregunta, esperá respuesta):
   - `DIFIEREN` →
     - **Gana Drive (pull):** sobreescribí `data/.../<f>.md` con el Markdown del Doc (contenido fiel y completo).
     - **Gana local (push):** actualizá el Doc en sitio con `update_drive_file(file_id=<doc-id>, content="<.md completo>", source_format="md")` (preserva ID/link/comentarios).
     - **Merge manual:** mostrame ambos lados, ayudame a redactar el resultado final, y una vez confirmado escribilo **en los dos lados** (local + `update_drive_file`).
   - `SOLO EN DRIVE` → **bajar** (crear el `.md` local con el contenido del Doc) **o** borrar el Doc (solo si confirmo). Default: bajar.
   - `SOLO LOCAL` → **subir** (crear el Doc con `import_to_google_doc(file_name="<sin .md>", content="<.md completo>", folder_id="<ID-fase>")`, igual que el espejo normal) **o** borrar el `.md` (solo si confirmo). Default: subir.
   - `CARPETA SOLO LOCAL` / `CARPETA SOLO EN DRIVE` → crear el árbol faltante del lado que corresponda; si creás carpetas nuevas en Drive, **actualizá la tabla de mapeo en `CLAUDE.md`** con los IDs nuevos (igual que indica `CLAUDE.md`).
3. **Aplicá solo lo confirmado** y confirmá en una línea qué quedó (`✅ Bajado a data/.../validacion.md` · `✅ Doc actualizado desde local` · etc.).
4. Pasá a la siguiente.

> Si preferís resolver en lote (ej. "bajá todos los SOLO EN DRIVE", "para los DIFIEREN siempre gana Drive"), aceptá esa instrucción y aplicala, confirmando archivo por archivo en el resumen final.

## Al cerrar

- Mostrá un **resumen final**: qué bajó, qué subió, qué se creó/borró, qué quedó sin resolver (si dejaste algo pendiente).
- Si tocaste archivos locales, recordá que los cambios están en el working tree de git y se pueden revisar con `git diff data/` antes de commitear.
- Si creaste carpetas nuevas en Drive, confirmá que agregaste las filas correspondientes a la tabla de mapeo de `CLAUDE.md`.
- Tras un pull, los dos lados quedan idénticos (normalizado); un nuevo escaneo debería dar todo `EN SYNC`.
