---
name: to-linear
description: Toma la especificación generada por /especifica (o cualquier spec en la conversación) y crea sus milestones + issues en Linear. Cada milestone de la especificación se vuelve un Project Milestone nativo de Linear, y cada pieza de trabajo un issue colgado dentro. Use when "manda a Linear", "crea los issues", "sube la especificación a Linear", "/to-linear".
user_invocable: true
argument-hint: "[opcional: nombre o ID del proyecto de Linear]"
---

# To Linear

Convierte una especificación (el que generó `/especifica`, en `_especificaciones/especificacion.md`) en issues + Project Milestones de Linear. Es el puente entre "tengo el plan" y "el equipo ya lo puede tomar".

## Requisito: MCP de Linear conectado

Este skill usa las tools del MCP de Linear (`list_projects`, `list_milestones`, `save_milestone`, `save_issue`, etc.). Si no las tienes, conéctalo primero — ver el README del repo (`.mcp.json.example`). Sin el MCP, este skill no puede escribir nada.

## Proceso

### 1. Reúne la especificación

- Si existe `_especificaciones/especificacion.md` en el repo, léelo. Es tu fuente de milestones y scope.
- Si no, usa el spec/plan que esté en la conversación.
- Si el usuario pasó un nombre/ID de proyecto de Linear como argumento, úsalo. Si no, pregunta a cuál proyecto van los issues (`list_projects` para mostrar opciones).

### 2. Draftea las piezas de trabajo (vertical slices)

Rompe cada milestone de la especificación en issues **independientemente tomables**. Prefiere **vertical slices** (tracer bullets): cada issue entrega un camino completo aunque angosto por todas las capas (datos, API, UI), NO una tajada horizontal de una sola capa.

**Reglas de vertical slice:**
- Cada slice entrega algo demoeable o verificable por sí solo.
- Prefiere muchas slices delgadas sobre pocas gruesas.
- Marca cada una como **HITL** (necesita humano) o **AFK** (un agente la puede hacer solo). Prefiere AFK donde se pueda.

### 3. Confirma con el usuario

Presenta el desglose como lista numerada, **agrupado por milestone**. Para cada issue:

- **Título:** corto y descriptivo
- **Milestone:** a cuál pertenece
- **Tipo:** HITL / AFK
- **Bloqueado por:** qué otros issues deben terminar antes (si aplica)

Pregunta:
- ¿La granularidad se siente bien? (muy gruesa / muy fina)
- ¿Las dependencias son correctas?
- ¿Cada issue está en el milestone correcto?

Itera hasta que apruebe. **No escribas nada en Linear hasta tener el OK.**

### 4. Asegura los Project Milestones en Linear

Cada milestone de la especificación = un Project Milestone nativo de Linear; los issues viven dentro.

1. Detecta los milestones de la especificación (headings `## Milestone N — <nombre>` en `especificacion.md`).
2. `list_milestones` en el proyecto. Para cada milestone que NO exista, créalo con `save_milestone` (name = nombre del milestone; description = el framing del milestone de la especificación).
3. Guarda el nombre/ID de cada milestone para asignar los issues en el paso 5.

Si el trabajo es un solo cambio atómico sin milestones, sáltate este paso.

### 5. Publica issues en Linear

Para cada issue aprobado, créalo con `save_issue`, pasando `milestone: <nombre>` para colgarlo dentro de su Project Milestone. Usa el template abajo. Publica en orden de dependencias (bloqueadores primero) para poder referenciar IDs reales en "Bloqueado por".

## Template de issue

```markdown
## Qué construir

Descripción concisa de esta slice. Describe comportamiento end-to-end, NO implementación capa por capa.

## Criterios de aceptación

- [ ] Criterio 1
- [ ] Criterio 2

## Bloqueado por

- Referencia al ticket que bloquea (si aplica), o "Ninguno — puede empezar de inmediato".
```

## Labels (opcional)

Si tu Linear tiene labels, marca cada issue con lo que aplique. Un set útil (edítalo en `[CUSTOMIZE]`):

- Tipo: `Feature` / `Bug` / `Improvement`
- `HITL` (necesita humano) vs `AFK` (agente lo puede hacer)

Si tu workspace no tiene estos labels, omítelos — no fallan el flujo.

## Reglas

- **Cada issue va dentro de su Project Milestone.** Crea los milestones que falten; no dupliques uno existente.
- **Nada se escribe en Linear sin aprobación del usuario** (paso 3).
- Si el plan no rompe en vertical slices (es un solo cambio atómico), dilo y crea un solo issue.

## Crédito

El patrón de vertical slices / tracer bullets viene de [mattpocock/skills/engineering/to-tickets](https://github.com/mattpocock/skills/tree/main/skills/engineering/to-tickets) (MIT). Este fork lo adapta para arrancar desde la especificación de `/especifica` y publicar en Project Milestones nativos de Linear.

## [CUSTOMIZE]

```yaml
espec_path: _especificaciones/especificacion.md          # de dónde lee la especificación
labels_tipo: [Feature, Bug, Improvement]   # vacío para no usar labels
label_agente: AFK              # label para issues que un agente puede tomar; vacío para desactivar
label_humano: HITL             # label para issues que requieren humano
```
