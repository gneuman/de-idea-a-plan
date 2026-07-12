# Fase 10 — Milestones

Propón secuencia default basada en dependencias, más 2 alternativas a granularidades distintas. El usuario elige.

## Reglas para milestones

Cada milestone debe:

- **Entregar funcionalidad visible y usable** que el usuario puede ver y probar en el navegador.
- **Ser una sesión cerrada para un agente de código** — alcance de una sesión de plan + build.
- **Tener dependencias claras** — milestones posteriores construyen sobre anteriores.
- **Tener "Done when" verificable** — qué tiene que poder hacer el usuario para considerarlo terminado.

## Cómo proponer

### Default (recommended) — 3 milestones

1. **Foundation + CRUD core** — modelos básicos, pantallas para crear/leer/editar/borrar las entidades principales.
2. **Integraciones** — agrega los servicios externos (pagos, email, AI, etc).
3. **Pulido público** — landing, share público, edge cases, polish UI.

### Alternativa A — menos / más grandes (2 milestones)

1. **Foundation + CRUD + Integraciones** juntas
2. **Pulido público**

Tradeoff: sesiones más largas, más riesgo por sesión, menos checkpoints. Bueno si el proyecto es chico.

### Alternativa B — más / más chicas (5–6 milestones)

Una por feature mayor.

Tradeoff: más checkpoints, más lento en total, más context switching. Bueno si quieres revisar cada parte por separado o si tienes muchas integraciones distintas.

## Cómo presentar

```
Te propongo 3 opciones de cómo trocear el build. Cada milestone es una sesión cerrada que entrega algo que puedes probar en el navegador.

**Opción A (recomendada) — 3 milestones:**
1. Foundation + CRUD — {features que entrega}
2. Integraciones — {qué servicios se prenden}
3. Pulido público — {qué se ve afuera}

**Opción B — 2 milestones (sesiones más largas):**
1. Foundation + CRUD + Integraciones — todo junto
2. Pulido público

**Opción C — 5 milestones (más checkpoints):**
1. {Feature 1}
2. {Feature 2}
3. {Feature 3}
4. {Integración X}
5. {Pulido}

Tradeoff rápido: menos milestones = más riesgo por sesión pero más rápido. Más milestones = más checkpoints pero más context switching.

¿Cuál?
```

## AskUserQuestion

- **Opción A — 3 milestones (recomendada)**
- **Opción B — 2 milestones (más rápido)**
- **Opción C — 5 milestones (más control)**
- **Custom — te digo cómo dividir** — Texto libre. Usuario describe la división.

## Después de elegir

Para cada milestone confirma:

1. **Nombre corto** (ej: "Foundation", "Integraciones", "Pulido público")
2. **Slug en kebab-case** (ej: `foundation`, `integraciones`, `pulido-publico`) — se usa en el path `_plan/milestones/N-{slug}/`
3. **Framing de 1–2 oraciones** — qué entrega
4. **In-scope** — features visibles que entrega (sub-set de las features locked en Fase 4)
5. **Out-of-scope explícito** — qué un coder podría asumir que va en este milestone pero NO
6. **Done when** — verificación concreta, idealmente algo que el usuario hace en el browser

Presenta el resumen y AskUserQuestion para lockear:

- **Locked, listos para escribir archivos** — Avanza Fase 11.
- **Cambios — los hago en chat** — Itera.

## Bloquear

Guarda en memoria:
- `milestones` — array ordenado de `{n, nombre, slug, framing, in_scope[], out_of_scope[], done_when}`

Pasa a Fase 11.
