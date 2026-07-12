# Fase 12 — Escribir archivos

Todo bloqueado. **Solo escribe.** Sin draft de aprobación — el usuario aprobó pieza por pieza durante la entrevista.

Todos los archivos salen a `_prd/` (editable en `[CUSTOMIZE]` → `salida_dir`).

## Qué se escribe, según formato

| Formato Fase 2 | Archivos generados |
|---|---|
| html | `_prd/prd.html` + `_prd/milestones/N-{slug}/prompt.md` |
| markdown | `_prd/prd.md` + `_prd/milestones/N-{slug}/prompt.md` |
| ambos | `_prd/prd.html` + `_prd/prd.md` + milestones |

**Reglas:**

- Los `prompt.md` de milestone son SIEMPRE markdown, sin importar el formato del PRD.
- Los `prompt.md` se generan siempre.

## Estructura final

```
_prd/
  prd.html                  # si HTML o ambos
  prd.md                    # si Markdown o ambos
  milestones/
    1-foundation/
      prompt.md
    2-integraciones/
      prompt.md
    3-pulido-publico/
      prompt.md
```

## Plantilla del PRD en HTML

Lee y sigue `references/prd-html-template.md` para el scaffold completo. Llena los placeholders con el estado locked en sesión.

Reglas adicionales del HTML:

- **Auto-flag de features que entraron con `auto: true`** — agrega badge "🤖 sugerido" o equivalente Lucide en la card.
- **Sección de Riesgos** — tabla con columnas Riesgo / Impacto / Mitigación.
- **Sección de Supuestos** — lista simple.
- **Footer:** marca de tiempo de generación + el `footer_credito` del bloque `[CUSTOMIZE]`.

## Plantilla del PRD en Markdown

```markdown
# {Nombre del proyecto}

> **Sobre este archivo:** Este PRD vive en `_prd/` y es **temporal**. Documentación y guía para el build inicial del codebase. No funcional. Ningún código, configuración, runtime, test o deploy debe importar, leer o depender de archivos en `_prd/`. Una vez completados los milestones, se puede borrar la carpeta.

## Qué estamos construyendo

{Propósito locked, expandido con 1–2 párrafos de contexto. Cierra con stack y cómo se estructuran los milestones.}

---

### Qué hace la app

{Bullets de las features locked en Fase 4, en lenguaje del usuario. 5–10 bullets.}

---

### Ya provisto por {starter name}

{Lista locked en Fase 6, lo que NO se re-especifica. Omite esta sección si el proyecto es desde cero.}

---

### Fuera de alcance (v1)

{Lista locked en Fase 5, formato: **Item** — razón en una línea.}

---

### Integraciones externas

{Por cada integración locked en Fase 7: nombre, para qué, credenciales que el usuario debe conseguir, costo si lo sabes.}

---

### Modelo de datos

{Por cada entidad locked en Fase 8: heading + bullet list de campos + nota de relaciones. Plain language, no tipos de DB.}

---

### Riesgos

| # | Riesgo | Impacto | Mitigación |
|---|---|---|---|
| R1 | ... | ... | ... |

### Supuestos

- Supuesto 1
- Supuesto 2

---

## Milestone 1 — {Nombre}

{Framing de 1–2 oraciones.}

### Qué se construye

{Bullets de in-scope user-facing.}

### Lo que NO incluye este milestone

{Bullets de out-of-scope explícito.}

### Done when

{1–2 oraciones de verificación, browser-testable.}

---

{Repetir por cada milestone}
```

## Plantilla del `prompt.md` por milestone

```markdown
# Milestone {N} — {Nombre}

Vas a entrar a plan mode para planear y luego construir el Milestone {N} del proyecto.

## Contexto

- Lee `@{PRD_PATH}` para el contexto completo: scope, modelo de datos, stack, integraciones.
- Lee los `milestone-log.md` de milestones previos (`@_prd/milestones/1-*/milestone-log.md`, etc) para entender qué ya se construyó. Si estás en milestone 1, no hay previos.

## Tu tarea

1. Planea la implementación SOLO del Milestone {N} como está definido en el PRD. No planees ni construyas nada de milestones posteriores.
2. Cuando confirme el plan, construye SOLO lo del scope de Milestone {N}.
3. Verifica contra el "Done when" del milestone.
4. Cuando termines, escribe un `milestone-log.md` en esta carpeta resumiendo:
   - Qué se construyó (archivos creados, modelos agregados, rutas, etc)
   - Decisiones tomadas durante la implementación que no estaban pre-especificadas
   - Qué necesita saber el siguiente milestone
   - Cualquier desviación del PRD y por qué

Pregúntame lo que necesites con `AskUserQuestion` para cerrar el plan de implementación de este milestone.
```

`{PRD_PATH}` se reemplaza con:
- HTML solo: `_prd/prd.html`
- Markdown solo o Ambos: `_prd/prd.md` (el agente lo parsea mejor)

## Nota a CLAUDE.md / AGENTS.md

Después de escribir los archivos en `_prd/`, agrega esta sección al final de `CLAUDE.md` (si existe) o crea `AGENTS.md`:

```markdown
## `_prd/`

`_prd/` contiene el PRD inicial y los prompts por milestone usados para scaffold del codebase en su fase inicial. Son archivos **temporales** — documentación y guía. **No funcional**: ningún código, config o runtime debe importar, referenciar o depender de nada en `_prd/`. Una vez completados los milestones, se puede borrar.
```

Si ya existe una sección `## _prd/`, actualízala en lugar de duplicar.

## Mensaje final al usuario

> Listo. Tres cosas:
>
> 1. Abre `_prd/prd.html` para revisar el plan visualmente.
> 2. Cuando arranques Milestone 1, abre `_prd/milestones/1-{slug}/prompt.md` y dile al agente "empieza por aquí".
> 3. Después de cada milestone, el agente escribe `milestone-log.md` en esa carpeta con qué se hizo.
>
> ¿Quieres mandar estos milestones a Linear como issues? Corre el skill `to-linear` (necesitas el MCP de Linear conectado).

## Bloquear

Una vez escritos los archivos, marca la sesión como completa y termina.
