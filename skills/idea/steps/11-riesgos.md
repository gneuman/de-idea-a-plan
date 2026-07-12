# Fase 11 — Riesgos y supuestos

Esta fase captura los **supuestos** (lo que un agente de código asume sin re-preguntar — si algo cambia, queda documentado por qué se decidió así) y los **riesgos** (qué puede tronar antes de que trones tú).

## Cómo proponer

Lee todo lo locked en fases anteriores (propósito, features, integraciones, modelo de datos, milestones). Genera 3–8 riesgos + 3–6 supuestos.

### Riesgos típicos

**Técnicos:**
- "El proveedor de pagos no cubre el país X que algunos usuarios necesitan" → mitigación: fallback / método alterno.
- "La API de WhatsApp Business tiene rate limits que pueden golpear envíos masivos" → mitigación: queue + cap diario.
- "El proveedor de AI puede caerse (503) y romper una feature crítica" → mitigación: degradar a entrada manual.

**De negocio / operación:**
- "Todavía no hay credenciales del proveedor Y, podría retrasar esa feature 2 semanas" → mitigación: dejar la feature oculta hasta tener credenciales.
- "El equipo no tiene un flujo definido para aprobar X" → mitigación: definirlo antes de Milestone 2.

**De adopción / UX:**
- "El equipo nunca ha usado una herramienta así, hay curva de aprendizaje real" → mitigación: capacitación breve + screencast.

### Supuestos típicos

- "Se provee logo + paleta de colores antes de Milestone 3"
- "Existe cuenta de Vercel (o se autoriza crear una)"
- "Los datos históricos no se migran — v1 arranca con base vacía"
- "Hay un punto de contacto único para decisiones de scope"

## Formato sugerido

```
**Riesgos**

| # | Riesgo | Impacto | Mitigación |
|---|---|---|---|
| R1 | {descripción} | alto/medio/bajo | {qué hacemos} |
| R2 | ... | ... | ... |

**Supuestos**

- {Supuesto 1}
- {Supuesto 2}
- {Supuesto 3}

¿Algo te suena mal o falta?
```

## AskUserQuestion

- **Lista bien, locked** — Avanza Fase 12.
- **Tengo cambios, los digo en chat** — Itera.
- **Saltar esta fase** — Solo si el proyecto es muy chico y de un solo milestone.

## Reglas

- **No riesgos genéricos.** "Cambio de scope" → fuera. "El usuario quiere agregar carrito de compras post-arranque" → adentro.
- **Mitigación concreta.** "Comunicación temprana" → fuera. "Feature oculta hasta tener credenciales del proveedor" → adentro.

## Bloquear

Guarda en memoria:
- `riesgos` (array de `{riesgo, impacto, mitigacion}`)
- `supuestos` (array de strings)

Pasa a Fase 12.
