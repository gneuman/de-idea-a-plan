# Fase 8 — Modelo de datos

Ahora que features e integraciones están locked, propón el modelo de datos. Para un usuario no técnico, el framing es: **"esto es lo que tu app necesita recordar, y cómo se relaciona entre sí"**.

## Cómo proponer

Por cada entidad (modelo de datos):

1. **Nómbrala** — sustantivo singular (`Cotizacion`, `Cliente`, `Idea`, `Publicacion`). No verbos.
2. **Lista sus campos en lenguaje plano.** No "url: string indexed not null". Sí "url — el link guardado, único por usuario".
3. **Anota relaciones** en prosa: "cada Cotizacion pertenece a un Cliente; cada Cliente puede tener varias Cotizaciones."

## Formato sugerido (en chat)

```
Aquí va el modelo de datos. Estas son las "cosas" que tu app necesita recordar:

**Cliente**
- nombre — razón social o nombre del contacto principal
- email — único, usado para login y notificaciones
- whatsapp — opcional, para recordatorios de cobranza
- rfc — opcional, requerido si emite factura
- relación: un Cliente tiene muchas Cotizaciones

**Cotizacion**
- titulo — corto, qué se está cotizando
- monto_mxn — número, en pesos mexicanos
- estado — borrador / enviada / aceptada / rechazada / vencida
- fecha_vencimiento — 15 días default
- url_publica — tracking id único para compartir
- relación: una Cotizacion pertenece a un Cliente

**Pago**
- monto_mxn — número
- metodo — stripe / mercadopago / transferencia / efectivo
- fecha — cuándo entró
- relación: un Pago pertenece a una Cotizacion

¿Esto refleja lo que necesitas, o falta/sobra algo?
```

## Reglas para el modelo

- **3 a 8 entidades.** Si tienes 1–2, te falta pensar. Si tienes 10+, agrupa entidades chicas o saca features de scope.
- **Sin tablas join explícitas.** "Cada Bookmark puede tener varios Tags" basta — no propongas `BookmarkTags` aparte. El agente decide en plan mode.
- **Campos en español, no en inglés.** `nombre_cliente`, no `client_name`. La excepción es términos universales que se quedan en inglés (`url`, `email`, `slug`).
- **Sin tipos de columna.** Cero `string`, `integer`, `boolean`, `text`, `jsonb`. Eso es implementación.
- **Sí marca campos críticos como requeridos vs opcionales** — el cliente lo entiende.
- **Sí menciona enums** ("estado: borrador / enviada / aceptada") — afecta UX.

## AskUserQuestion

- **Se ve bien, lo bloqueo** — Avanza.
- **Casi, edito en chat** — Usuario describe cambios. Re-propón. Re-confirma.
- **Falta algo importante, lo describo** — Usuario describe entidad/campo faltante. Agrega. Re-propón.

## Casos comunes LATAM

Recuerda incluir cuando aplique:
- `rfc` (Cliente o Proveedor) — RFC mexicano, requerido para CFDI
- `regimen_fiscal` — código SAT del cliente
- `uso_cfdi` — código del uso de la factura
- `cfdi_uuid` — UUID del CFDI timbrado
- `whatsapp` — separado de teléfono, formato E.164 (`+521XXXXXXXXXX`)
- `moneda` — MXN default, USD posible
- `tipo_persona` — fisica / moral

## Bloquear

Guarda en memoria:
- `data_model` (array de `{entidad, campos[{nombre, descripcion, requerido}], relaciones}`)

Pasa a Fase 9.
