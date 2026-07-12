# Fase 2 — Formato de salida

Bloquea qué archivo(s) se escriben al final. Las decisiones de scope son las mismas en todos los formatos — solo cambia la presentación. Los `prompt.md` por milestone son SIEMPRE markdown (los consume un agente, no el usuario).

## Framing corto

> ¿En qué formato quieres el plan? La decisión es visual, no de scope — el contenido es el mismo. HTML es el recomendado: lo abres en navegador, se ve bonito, es compartible con quien sea.

## AskUserQuestion

- **HTML (Recommended)** — Archivo `plan.html` autocontenido. Lo abres con doble click. Responsive, modo oscuro/claro, íconos Lucide. Ideal para mostrar a alguien o revisar de un vistazo.
- **Markdown** — Archivo `plan.md` plano. Lo editas a mano, pegas secciones donde sea, va a Linear, GitHub o Notion sin problema.
- **Ambos** — Genera `plan.html` y `plan.md`. Recomendado si vas a construir: el agente lee el `.md`, tú revisas el `.html`.

## Default

Si el usuario dice "el que recomiendes", usa **Ambos** — el agente lee el markdown mejor, y tú tienes el HTML para revisar. (Editable en `[CUSTOMIZE]` → `formato_default`.)

## Bloquear

Guarda en memoria de sesión:
- formato: `html` | `markdown` | `ambos`

Esto lo consulta Fase 12 (escribir archivos). Los `prompt.md` por milestone se generan siempre, sin importar el formato de el plan.

Avanza a Fase 3.
