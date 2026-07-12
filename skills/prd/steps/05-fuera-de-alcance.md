# Fase 5 — Fuera de alcance (top-level)

Propón proactivamente la lista de cosas que **podrían** estar pero **no están** en v1. Esto protege contra scope creep y deja al cliente sin sorpresas.

## Por qué importa

- En cotización: el cliente firma sabiendo qué NO incluye. Cero ambigüedad.
- En construcción: el agente no se desvía haciendo features que nadie pidió.

## Cómo proponer

Lista las exclusiones razonables basadas en el tipo de app. Explica brevemente la razón.

### Catálogo de exclusiones típicas

**Para casi cualquier app:**
- App móvil nativa — "v1 va web responsive; nativa duplica el alcance y costo"
- Extensión de navegador
- Features sociales / sharing público — "ruido en v1, agregable después si hay demanda"
- Búsqueda avanzada / filtros múltiples — "v1 va con filtro simple"
- OAuth / login de terceros (Google, Apple) — "v1 va con email + password del starter"
- Multi-tenant / equipos / roles — "v1 es single-user o single-team"
- Importar desde otras herramientas
- API pública — "v1 es UI únicamente"
- Internacionalización (i18n) — "v1 va solo en español de México"

**Para apps con pagos:**
- Suscripciones recurrentes / billing — "v1 va pagos one-shot, recurrente después"
- Reembolsos automáticos
- Multi-currency
- Cupones / descuentos

**Para apps con IA:**
- Selección de modelo (Opus vs Sonnet vs Haiku)
- Fine-tuning
- API keys por usuario
- Múltiples proveedores (Anthropic + OpenAI + Gemini)

**Para apps de contenido / CMS:**
- Archivado / favoritos / trash
- Páginas públicas / SEO
- Comentarios / reacciones
- Versiones / historial de cambios

**Para apps LATAM con SAT/CFDI:**
- Emisión de CFDI propia (usa el PAC del cliente o no aplica)
- Cancelación de CFDIs
- Complementos especializados (carta porte, comercio exterior)
- Conciliación bancaria automática con todos los bancos (limita a 2–3)

## Cómo presentar

```
v1 NO incluye estas cosas (que podrían parecer obvias pero las dejamos fuera a propósito):

- **{Item 1}** — {razón}
- **{Item 2}** — {razón}
- **{Item 3}** — {razón}
...

¿Algo de esto debe entrar a v1? ¿Hay algo más que quieras dejar explícitamente afuera?
```

## AskUserQuestion

- **Lista bien, todo eso queda fuera** — Bloquea.
- **Algo se queda adentro, te digo cuál** — Usuario indica en chat. Mueve de fuera-de-alcance a la lista de features (Fase 4). Re-propón.
- **Quiero agregar cosas a fuera de alcance** — Usuario lista. Agrega.

## Reglas

- **Mínimo 5 items.** Si tienes menos, no pensaste suficiente. Las exclusiones explícitas son MUY valiosas en cotizaciones — los clientes asumen que cosas están incluidas si no las niegas.
- **Una razón por item.** No solo "fuera". Da el por qué corto.
- **Sin sarcasmo.** "Por supuesto que no incluye Bitcoin" → fuera. Profesional.

## Bloquear

Guarda en memoria:
- `fuera_de_alcance` (array de `{item, razon}`)

Pasa a Fase 6.
