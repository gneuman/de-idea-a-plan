# Catálogo de integraciones — LATAM

Fuente de verdad para Fase 7 (integraciones). Stack gringo vs equivalente LATAM, con credenciales y costo aproximado.

## Pagos online

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Charges one-shot online | Stripe México | Mercado Pago, Conekta, Clip, Openpay | Public key + secret key + webhook secret | Stripe es DX rey. Mercado Pago tiene más adopción en pyme. |
| Suscripciones recurrentes | Stripe Billing | Conekta Subscriptions | Mismas de Stripe + product/price IDs | |
| Pagos cara a cara (POS) | Clip | Mercado Pago Point, SrPago | Token API + terminal ID | Solo si el cliente cobra presencial. |
| Pagos OXXO / referencia | Stripe (PaymentMethod: oxxo) | Mercado Pago, Conekta | API keys de Stripe + activar OXXO en dashboard | OXXO es 30% del mercado mexicano informal. |

## Open finance (bancos)

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Leer movimientos bancarios | Belvo | Finerio, Prometeo | Client ID + secret + webhook URL | Caro pero único confiable en MX. |
| Categorización automática | Belvo Categorization | Finerio | Mismas | Servicio sobre los movimientos. |
| Cuentas conectadas (link flow) | Belvo Widget | Finerio Connect | Public token | Widget de UI ya hecho. |

## CFDI / SAT (México)

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Timbrado CFDI 4.0 | El PAC del cliente | Facturama, SW Sapien, Smarter | API key del PAC + RFC emisor + Sello (CSD) | NO timbres por el cliente — usa SU PAC siempre. |
| Lectura de CFDIs recibidos | SAT WS (SOAP) | Facturama API, Solucione | FIEL del cliente | Más complejo, certificados SAT. |
| Cancelación CFDI | El PAC del cliente | — | Mismas del timbrado | Rara vez en v1. |
| Validación de RFC | SAT LCO público | Validar API (PACs) | Ninguna | LCO está rate-limited. |

## Email

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Transaccional (notifs) | Resend | Postmark, SendGrid, Mailgun | API key + domain verificado | Resend tiene previews en dev. |
| Newsletter / marketing | ActiveCampaign | Beehiiv, Buttondown, ConvertKit | API key + list ID | Beehiiv es fuerte para newsletters modernas. |
| Catch-all / soporte | Helpscout | Front, Zendesk | API key | Solo si hay tickets de cliente. |

## WhatsApp Business

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Mensajes 1-a-1 | Z-API | WhatsApp Cloud API (Meta), 360dialog, Twilio | API key + número verificado | Z-API es más barato y rápido para pyme MX. |
| Templates pre-aprobados | WhatsApp Cloud (Meta) | 360dialog | Business ID + access token + template IDs | Para campañas masivas. Requiere aprobación Meta. |
| Cobranza automatizada | Z-API + lógica propia | WhatsApp Cloud | Igual | Por ley: solo a quien autorizó recibir. |

## SMS

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Transaccional / OTP | Twilio | LabsMobile, MessageBird | Account SID + auth token + número verificado | Caro vs WA pero universal. |

## IA generativa

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Razonamiento / agentes | Claude Sonnet 4.6 (Anthropic) | GPT-4 Turbo (OpenAI), Gemini Pro | API key Anthropic | Sonnet por default. Opus para tareas críticas. |
| Resúmenes baratos | OpenRouter (Gemini Flash 2.0 gratis) | Claude Haiku, GPT-3.5 | API key OpenRouter | Flash es gratis hasta cierto rate. |
| Embeddings (búsqueda semántica) | OpenAI text-embedding-3-small | Voyage AI, Cohere | API key OpenAI | Embeddings con OpenAI sigue siendo lo más barato. |
| Búsqueda web con cita | Perplexity API | Tavily, Brave Search API | API key Perplexity | Mejor para "lo más reciente". |
| Transcripción de audio | OpenAI Whisper API | Deepgram, AssemblyAI | API key OpenAI | Whisper barato y bueno en español. |
| Generación de imagen | DALL-E 3 / Replicate | Midjourney (no API), Stable Diffusion | API key | Replicate da más control. |

## Storage / Files

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Imágenes con transformaciones | Cloudinary | imgix, ImageKit | Cloud name + API key + secret | Optimizaciones on-the-fly. |
| Files generales | Vercel Blob | S3, R2 (Cloudflare) | Vercel token | Más barato para volumen bajo. |
| Videos | Mux | Cloudflare Stream, Bunny | API key | Mux es plug-and-play. |

## Calendario

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Google Calendar 2-way sync | Google Calendar API | Microsoft Graph | OAuth client ID + secret + scopes | Requiere consent screen Google. |
| Booking (Calendly-like) | Cal.com self-hosted | Calendly API | Cal.com instance / API key | Cal.com OSS. |
| Reuniones con video | Zoom | Google Meet, Whereby | API key + account ID | Zoom para LATAM clientes. |

## Firma electrónica

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Firma simple cliente | Docuseal (self-hosted) | Mifiel, DocuSign | URL instance + JWT | Docuseal es open source, se autohospeda. |
| Firma con efectos legales MX | Mifiel | NOM 151 PSC certificados | API key + RFC | Mifiel está certificado SAT. |
| Contratos comerciales internacionales | DocuSign | PandaDoc, HelloSign | API key | Solo si cliente exige. |

## CRM / Marketing

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| CRM ligero | Attio | Pipedrive, HubSpot Free | API key + workspace ID | Attio es moderno y rápido. |
| Marketing automation | ActiveCampaign | HubSpot Marketing, Customer.io | API key + list IDs | AC tiene buen balance precio/potencia. |
| Pipeline ventas | HubSpot CRM (free) | Pipedrive, Salesforce | API key | Solo si el cliente lo pide. |

## Nómina (México)

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Cálculo nómina + IMSS + ISR | Worky | Runa, Buk, Aspel NOI | API key | Solo si entras a nómina, raro en v1. |
| Recibos nómina CFDI | El PAC del cliente | — | Igual que timbrado normal | Complemento Nómina. |

## Contabilidad

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Contabilidad SaaS | Zoho Books | Contpaqi i (limitada), Aspel COI | API key + organization ID | Zoho tiene la mejor API. |
| Catálogo de cuentas SAT | (local) | — | — | Tabla pública SAT, NO requiere API. |

## Comunicación interna

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Notifs equipo | Slack | MS Teams, Discord | Bot token + channel IDs | Slack sigue siendo el estándar en tech. |
| Notifs personales urgentes | Telegram Bot | Pushover, Discord | Bot token + chat ID | Para alertas oncall. |

## Mapas / Geolocalización

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Mapa interactivo | Google Maps JS | Mapbox, Leaflet + OpenStreetMap | API key | Mapbox es más barato si volumen alto. |
| Geocoding (dirección → coordenadas) | Google Geocoding | Mapbox Geocoding | API key | |
| Códigos postales MX | API SEPOMEX | (varios) | Free | Lista pública SEPOMEX. |

## Logística / Envíos (México)

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Cotización paqueterías | Mienvio | Skydropx, ShipFast | API key | Mienvio agrega Estafeta, DHL, FedEx. |
| Tracking | Mienvio | Skydropx | Igual | |

## Analytics

| Necesidad | Default | Alternativas | Credenciales | Notas |
|---|---|---|---|---|
| Web analytics | Plausible (paid) | Vercel Analytics, Posthog, GA4 | Site ID | Plausible es privacy-first. |
| Product analytics | Posthog | Mixpanel, Amplitude | API key | Posthog tiene OSS option. |

## Reglas de elección

1. **Default LATAM cuando aplique.** No "Stripe siempre" — Mercado Pago tiene 60% mercado MX.
2. **Más barato gana, ceteris paribus.** Resend < Postmark si DX es comparable.
3. **DX prevalece sobre precio para herramientas de equipo.** Slack > Discord para B2B aunque cuesta más.
4. **OSS / self-hosted cuando seguridad/control es crítico.** Docuseal > DocuSign para firmas internas.
5. **Lock-in mínimo.** S3-compatible (R2) > S3 propietario si el costo es similar.
