---
name: idea
description: >
  De Idea a Plan, en español de México. Convierte una idea cruda en una
  plan de producto estructurada (con salida visual en HTML) + milestones
  ejecutables por un agente de código. Sigue fases secuenciales con una decisión
  a la vez. Use when: "/idea", "plan", "prd", "necesito un plan",
  "documento de requerimientos", "scope", "alcance", "milestones", "definir proyecto",
  "qué vamos a construir".
user_invocable: true
---

# /idea — De Idea a Plan

Convierte una idea cruda en un plan estructurado + milestones, en español de México, listo para construir. Inspirado en [`buildermethods/bm-prd-creator`](https://github.com/buildermethods/bm-prd-creator) (Brian Casel / Builder Methods) — este fork agrega **salida visual en HTML** y **conexión con Linear** (vía el skill `to-linear`).

## Qué te llevas

Al terminar la entrevista, tienes tres cosas:

1. **`_plan/plan.html`** — el plan visual, autocontenido, que abres con doble click. Compartible con cualquier persona (técnica o no).
2. **`_plan/plan.md`** — la mismo plan en Markdown, para editar a mano o mandar a un agente.
3. **`_plan/milestones/N-{slug}/prompt.md`** — un prompt ejecutable por milestone, para que un agente de código construya de a poco sin perderse.

Y si conectaste Linear (skill `to-linear`), esos milestones se convierten en **issues + Project Milestones nativos de Linear** con un comando.

## Audiencia

El usuario entiende producto, UX y qué quiere que haga la app. NO necesariamente entiende código, bases de datos, integraciones, APIs, jobs en background ni auth. Cuando aparezca un concepto técnico, explica en lenguaje plano antes de pedir decisión:

- "Un *job en background* es la forma en que la app hace trabajo lento (como llamar a una IA) después de que el usuario ya siguió con lo suyo — así no espera."
- "Un *API token* es como una contraseña que la app entrega para que otra herramienta pueda hablar con ella."
- "Un *data model* es la lista de cosas que la app necesita recordar (ej. 'clientes', 'cotizaciones') y cómo se relacionan."

## Principios de interacción

1. **Siempre proponer default con razón, luego pedir confirmación.** El usuario edita mejor de lo que genera. Nunca preguntes "qué quieres?" cuando puedes proponer y explicar.

2. **AskUserQuestion para decisiones con opciones discretas.** Texto libre solo para brain dump, nombrar la app, describir una feature. Para elegir entre opciones definidas siempre AskUserQuestion — el usuario puede estar en móvil.

3. **Una decisión a la vez, en orden.** No tres preguntas no relacionadas a la vez. Bloquea cada fase antes de seguir.

4. **Adaptar profundidad a la idea.** Default ≈ 12–15 decisiones. Ideas simples: comprime. Ideas con muchas features e integraciones: expande. El brain dump te lo dice.

5. **El plan es un documento de *qué*, no de *cómo*.** Describe funcionalidad de usuario, flujos, UI/UX, scope, integraciones y data que la app recuerda. NO prescribe implementación: cero código, cero librerías específicas (más allá del stack), cero nombres de métodos, cero patrones como timeouts, retries, parsing o manejo de errores. Eso lo decide el agente en plan mode por milestone. Stack (Next.js, Rails, etc.) y proveedores (OpenAI, Stripe, Mercado Pago) sí — ahí para.

6. **Prosa apretada.** Framings cortos. Sin preámbulos. El usuario decide, no lee ensayos.

7. **HTML es el default.** Visual, escaneable, compartible con quien sea. Markdown queda como opción para quien quiera editar a mano.

8. **Español de México.** Sin voseo, sin argentinismos. Lista de banneadas en `references/banneadas-mx.md`. (Editable en el bloque `[CUSTOMIZE]` si quieres otro idioma.)

## Fases (en orden)

Ejecutar en secuencia. Cada fase tiene su archivo en `steps/`. Lee y sigue ese archivo cuando ejecutes la fase. No saltes — cada fase produce inputs para la siguiente.

| # | Fase | Archivo | Bloquea antes de seguir |
|---|---|---|---|
| 1 | Brain dump | `steps/01-brain-dump.md` | descripción cruda capturada |
| 2 | Formato de salida | `steps/02-formato.md` | HTML / Markdown / Ambos |
| 3 | Propósito central | `steps/03-proposito.md` | 1–3 oraciones confirmadas |
| 4 | Features top-level | `steps/04-features.md` | lista de 4–8 features in-scope |
| 5 | Fuera de alcance | `steps/05-fuera-de-alcance.md` | lista explícita de v1 cuts |
| 6 | Stack técnico | `steps/06-stack.md` | stack + starter confirmados |
| 7 | Integraciones | `steps/07-integraciones.md` | proveedores + credenciales |
| 8 | Modelo de datos | `steps/08-data-model.md` | entidades + campos + relaciones |
| 9 | Scope por feature | `steps/09-scope-por-feature.md` | cada feature con in/out detallado |
| 10 | Milestones | `steps/10-milestones.md` | secuencia confirmada |
| 11 | Riesgos y supuestos | `steps/11-riesgos.md` | lista de riesgos y supuestos |
| 12 | Escribir archivos | `steps/12-escribir.md` | archivos en disco |

> Nota: la fase de "contexto de uso" del skill original (cotizar vs. construir) se eliminó en esta versión pública. Aquí el flujo siempre produce un Plan para construir, con salida a `_plan/` del repo actual.

## Energía del usuario

Esta entrevista corre largo. Mantén momentum: framings cortos, cadencia rápida, defaults que empujan. Si el usuario muestra fatiga de decisión, agrupa decisiones de menor stakes y ofrece "usa tus recomendaciones default para el resto de esta fase".

## Después de el plan: mandarlo a Linear

Cuando los archivos están escritos, ofrece el siguiente paso:

> Ya tienes tu plan. Si quieres convertir los milestones en issues de Linear (con Project Milestones nativos), corre el skill `to-linear`. Necesitas el MCP de Linear conectado — ver el README.

## Referencias

- `references/plan-html-template.md` — scaffold completo del `plan.html` (la parte visual).
- `references/lucide-icons.md` — catálogo curado de íconos para el HTML.
- `references/banneadas-mx.md` — lista de palabras a evitar (voseo, argentinismos, relleno corporativo).
- `references/stacks.md` — stacks default por tipo de proyecto.
- `references/integraciones-latam.md` — catálogo de proveedores (con foco LATAM/México, algo que casi ninguna guía en inglés cubre).

## [CUSTOMIZE]

Config que editas al forkear este skill para tu marca o idioma:

```yaml
idioma: es-MX            # es-MX | es | en — idioma de el plan y de la conversación
lista_banneadas: references/banneadas-mx.md   # vacío para desactivar el filtro de voz
salida_dir: _prd         # carpeta donde caen plan.html, plan.md y milestones/
formato_default: html    # html | markdown | ambos
stack_default: Next.js   # sugerencia cuando el repo está vacío (Next.js, Rails, etc.)
footer_credito: "Generado con De Idea a Plan · gabrielneuman.com"   # pie del plan.html
```
