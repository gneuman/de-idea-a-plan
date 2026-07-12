# Fase 9 — Scope detallado por feature

Ahora revisita cada feature locked en Fase 4 **una por una** y cierra su scope detallado. Foco **solo en decisiones visibles al usuario** — qué ve, qué hace, qué experimenta. NO implementación (librerías, métodos, timeouts, parsing).

## Por qué una a la vez

Lotear features no funciona — el usuario no puede mantener contexto de 6 features a la vez. Una feature, decisión, lock, siguiente.

## Plantilla por feature

```
**Feature {N}/{total}: {Nombre}**

Lo que ESTÁ in-scope:

- {sub-feature 1 en términos de UI/UX}
- {sub-feature 2}
- {sub-feature 3}
- {qué pasa después de tomar la acción}
- {cómo se ve el output / recipient}

Lo que NO está in-scope (v1):

- {ambición razonable de v2}
- {edge case que no resolvemos}
- {advanced que viene después}

¿Esto cubre lo que tenías en mente?
```

## Nivel correcto de especificidad

### Ejemplo: feature "Compartir por email"

✅ **In-scope correcto:**
- Botón "Compartir" en cada item
- Form chico con: email del destinatario, asunto pre-llenado, body pre-llenado (editable)
- Acción de envío one-shot
- Destinatario recibe email legible con los detalles del item
- Confirmación visual al usuario que se envió

✅ **Out-of-scope correcto:**
- Tracking de aperturas / clicks
- Historial de qué se compartió
- Compartir a múltiples destinatarios a la vez
- Adjuntos
- Sends programados

❌ **MAL nivel (esto es implementación, no scope):**
- Usar Resend `sendBatch` API
- Retry con exponential backoff
- Template Handlebars vs MJML
- Background job vs sincrónico
- Validación del email format con regex específica

### Ejemplo: feature "Captura de idea con AI"

✅ **In-scope correcto:**
- Botón flotante "+ Nueva idea"
- Modal con un solo input grande (textarea)
- Usuario tipea texto crudo, click "Guardar"
- Loading state mientras AI procesa
- Muestra clasificación sugerida (plataforma + tipo) + tags propuestos
- Usuario confirma o edita antes de guardar
- Idea queda en estado "inbox"

✅ **Out-of-scope correcto:**
- Captura por voz
- Captura por foto / imagen
- Re-clasificación masiva de ideas viejas
- Sugerir ideas basadas en historial

❌ **MAL nivel (implementación):**
- Cuál prompt enviar a Claude
- Cuál modelo (Sonnet vs Haiku)
- Streaming vs no-streaming
- Cómo se valida el JSON de respuesta

## Cómo iterar

Para cada feature:

1. Pre-llena la lista in-scope y out-of-scope basado en tu mejor entendimiento del brain dump.
2. Preséntalo en chat con framing breve.
3. AskUserQuestion:
   - **Bien, locked** — Avanza a siguiente feature.
   - **Cambios — los hago en chat** — Re-propón con cambios. Re-pregunta.
4. Marca esa feature como locked. No regreses.

## Profundidad

In-scope detallado al nivel "lo que el usuario ve". Out-of-scope explícito (qué un coder podría asumir que va aquí pero NO). Sin detalles de UI píxel a píxel — eso lo decide el agente en plan mode.

## Fatiga del usuario

Si vas en feature 4 de 7 y el usuario empieza a contestar "como veas":

> Voy con mis defaults para las que quedan. Las marco con 🤖 en el Plan para que las revises antes de firmar. ¿Vamos?

Si dice sí: pre-llena las restantes y avanza a Fase 10. Marca cada una como `auto: true` para flag visual en el plan final.

## Bloquear

Guarda en memoria:
- `features_detalle` — para cada feature de Fase 4, agrega `in_scope[]`, `out_of_scope[]`, y opcional `auto: true`.

Pasa a Fase 10.
