# Fase 4 — Features top-level (in scope)

Propón 4–8 features core que el app necesita para cumplir su propósito. Lista numerada en chat, una línea de explicación cada una. Después AskUserQuestion para decidir cuáles quedan.

## Cómo proponerlas

1. Lee el brain dump y el propósito locked.
2. Identifica las capacidades de **usuario** necesarias (no técnicas — features que se ven en pantalla).
3. Numéralas como lista en chat:

```
Para que esto funcione, propongo estas {N} features core:

1. **{Feature 1}** — {qué hace, en una línea desde la perspectiva del usuario}
2. **{Feature 2}** — {...}
3. **{Feature 3}** — {...}
...

¿Cuáles dejamos, cuáles cortamos, qué falta?
```

## Reglas para la lista

- **4 a 8 features.** Si tienes 3 o menos, la idea es demasiado simple (revisa propósito) o estás siendo muy abstracto. Si tienes 9+, estás incluyendo cosas que son sub-features — agrúpalas.
- **Desde la perspectiva del usuario, no del backend.** "Captura de ideas" ✅. "Endpoint POST /ideas" ❌.
- **Concretas, no aspiracionales.** "Calendario semanal de publicación" ✅. "Gestión inteligente del flujo de contenido" ❌.
- **Sin auth, signup, login básicos** — el starter los provee (Fase 6 lo confirma).
- **Sin features de admin a menos que el usuario las mencionó** — fácil meter "panel de admin" cuando nadie lo pidió.

## AskUserQuestion

- **Lista bien, sin cambios** — Bloquea.
- **Tengo cambios, los hago en chat** — Usuario describe en texto libre: qué quita, qué agrega, qué renombra. Re-propón la lista actualizada y vuelve a preguntar.
- **Empezamos de cero** — Vuelve a Fase 3 (propósito) — si las features no caben, el propósito no estaba claro.

## Profundidad

Aquí solo headlines + 1 línea por feature. El detalle por feature (in/out scope) se hace en Fase 9. Esta fase NO es per-feature scoping — solo se cierra la lista headline.

## Bloquear

Guarda en memoria:
- `features` (array ordenado de 4–8 features con label + descripción de una línea)

Pasa a Fase 5.
