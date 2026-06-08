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

El nombre del Doc = el nombre del archivo local **sin la extensión `.md`** (ej. `idea`, `prevalidacion`, `validacion`, `validacion-campo` en `1-idea_phase/`; `plan-mvp` y `evaluacion-ia` en `2-build_phase/`). La idea queda identificada por la **carpeta** (`idea-NNN-<slug>/<fase>/`), no por el nombre del archivo; por eso el Doc dedup se busca **scopeado a la carpeta de fase de esa idea** (ojo: `plan-mvp` y `evaluacion-ia` se espejan en la carpeta espejo `2-build_phase/`, no en `1-idea_phase/`). Eso garantiza que las actualizaciones reencuentren el Doc existente y no creen copias.

1. **Buscá si ya existe** el Doc en la carpeta de fase **de esa idea**:
   `search_drive_files(query="name = '<nombre-sin-md>' and '<ID-carpeta-fase-de-la-idea>' in parents and trashed = false")`
2. **Si NO existe → crealo** convirtiendo el Markdown a Doc nativo, pasando el contenido inline (los tableros son chicos, no hace falta archivo intermedio):
   `import_to_google_doc(file_name="<nombre-sin-md>", content="<contenido completo del .md>", folder_id="<ID-carpeta-fase>")`
3. **Si YA existe → actualizalo en sitio** (preserva ID, link, comentarios y permisos), reemplazando el contenido con el `.md` completo y actualizado:
   `update_drive_file(file_id="<id-del-doc>", content="<contenido completo del .md>", source_format="md")`

> **Gotcha:** `import_to_google_doc` con `file_path` solo lee desde `~/.workspace-mcp/attachments` (`ALLOWED_FILE_DIRS`). Por eso, para espejar tableros, **pasá el contenido inline con `content=`** y evitás copiar archivos. No anuncies cada espejo como paso aparte: alcanza con el "📝 Guardado en el tablero" habitual (incluye el espejo en Drive).
