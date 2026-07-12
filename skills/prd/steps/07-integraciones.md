# Fase 7 — Integraciones externas y credenciales

Para cada feature in-scope, identifica si necesita servicio externo. Propón un proveedor por default. Lista las credenciales que el usuario debe conseguir.

## Por qué hay un catálogo LATAM

Las integraciones default del mundo gringo NO siempre aplican en México y LATAM. Stripe sí, pero Mercado Pago manda en muchos mercados. QuickBooks casi nadie lo usa — son Contpaqi, Aspel, Zoho Books. Para CFDI 4.0 hay que ir a un PAC mexicano. WhatsApp Business reemplaza email en muchos casos. Por eso `references/integraciones-latam.md` cubre proveedores que las guías en inglés ignoran. Úsalo si el proyecto es para México/LATAM; para otros mercados, propón el equivalente local.

## Cómo procesar

Para cada feature de la lista locked en Fase 4:

1. **¿Necesita servicio externo?** Si no, skip.
2. **Si sí**, explica en lenguaje plano qué hace el servicio externo:

   > "Para enviar email automático cuando pasa X necesitamos un proveedor de envío transaccional. Estos no son emails de marketing, son emails uno a uno disparados por el código de la app."

3. **Propón default con razón:**

   > "Default: **Resend**. Razón: buena relación precio/DX, funciona bien en LATAM."

4. **AskUserQuestion** para confirmar o cambiar:
   - Sí, {proveedor default}
   - Cambiamos a otro — digo cuál en chat
   - Quito esta integración (¿esto deja la feature sin soporte? — flag)

5. **Lista las credenciales** que el usuario debe conseguir ANTES de que el agente llegue a esa feature.

## Catálogo rápido por categoría

| Necesidad | Default | Alternativas |
|---|---|---|
| Pagos online | Stripe | Mercado Pago, Conekta, Clip, Openpay |
| Pagos cara a cara | Clip | Mercado Pago Point, SrPago |
| Suscripciones recurrentes | Stripe Billing | Conekta, Recurly |
| Email transaccional | Resend | Postmark, SendGrid, Mailgun |
| WhatsApp Business | WhatsApp Cloud API | Z-API, 360dialog, Twilio |
| SMS | Twilio | LabsMobile |
| CFDI 4.0 (timbrado MX) | Facturama | SW Sapien, Smarter, PAC del cliente |
| Bancos (open finance) | Belvo | Finerio, Prometeo |
| Contabilidad SaaS | Zoho Books API | Contpaqi (limitado), Aspel COI |
| AI generativa | Anthropic (Claude) | OpenAI, OpenRouter |
| AI búsqueda web | Perplexity API | Tavily |
| Storage / files | Cloudinary | S3, R2, Vercel Blob |
| Maps | Google Maps | Mapbox |
| Calendario | Google Calendar API | Microsoft Graph |
| Firma electrónica | Mifiel | DocuSign, PandaDoc |
| Nómina (MX) | Worky | Runa, Buk, Aspel NOI |
| CRM | Attio | HubSpot, Pipedrive |
| Comunicación interna | Slack | MS Teams, Discord |

## Plantilla por integración

Por cada integración locked, registra:

```
- Proveedor: {nombre}
- Para qué: {feature(s) que la usan}
- Razón del default: {1 línea}
- Credenciales que el usuario debe conseguir:
  - {credencial 1}
  - {credencial 2}
- Costo aproximado: {opcional, si lo sabes}
```

## Si el usuario no quiere setup

Si dice "no quiero crear cuenta de X", flag la feature que la usaba:

> "Sin {proveedor}, no podemos hacer {feature Y}. Opciones:
>
> 1. Conseguir credenciales después (bloquea solo esa parte)
> 2. Cambiar a proveedor alternativo (te recomiendo cuál)
> 3. Mover la feature a fuera-de-alcance v1"

## Reglas

- **No prescribir cómo se guardan las credenciales** (env vars, secrets manager, etc) — eso lo decide el agente en plan mode.
- **No prescribir librerías cliente** específicas — eso es implementación.
- **Sí prescribir el proveedor concreto** (Resend, no "algún email service").

## Bloquear

Guarda en memoria:
- `integraciones` (array de `{proveedor, para_que, razon, credenciales[], costo}`)

Pasa a Fase 8.
