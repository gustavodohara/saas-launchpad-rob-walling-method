# Referencias de comandos

Material de conocimiento **estable** que consumen los comandos de `.claude/commands/`:
imágenes, PDFs, diagramas, plantillas visuales, screenshots de ejemplo, etc.

Esto se **versiona en git** (a diferencia de `data/` y `memoria/`, que están en `.gitignore`).
Es "parte del comando", no datos de una idea concreta.

> **Por qué vive en `.claude/assets/` y no en `.claude/commands/assets/`:** todo archivo `.md`
> dentro de `.claude/commands/` se registra como slash command. Si las referencias colgaran de
> ahí, cualquier `.md` (incluido este README) ensuciaría la lista de comandos. Por eso van en
> `.claude/assets/`, fuera de `commands/`.

> Material específico de una idea (un screenshot de SimilarWeb, la pricing page de un
> competidor, capturas de ads) **NO va acá**: va en
> `data/idea-NNN-<slug>/<fase>/assets/` y se espeja a Drive.

## Convención de carpetas

```
.claude/assets/
├── _compartido/                    # referencias usadas por varios comandos
├── <nombre_comando_sin_prefijo>/   # una carpeta por comando que tenga referencias
│   └── ...
```

El nombre de la subcarpeta = nombre del comando **sin su prefijo de familia `saas_<familia>_`**
(ej. el comando `saas_idea_campana_landing.md` → carpeta `campana_landing/`; el comando
`saas_build_mvp_5pasos.md` → carpeta `mvp_5pasos/`).

## Cómo referenciar desde un comando

Desde el `.md` del comando, usá la ruta del repo:

```
.claude/assets/<comando>/<archivo>
```

o absoluta:

```
/home/gustavohd/Workspace/saas-launchpad-rob-walling-method/.claude/assets/<comando>/<archivo>
```
