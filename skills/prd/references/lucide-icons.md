# Íconos Lucide — catálogo curado para el PRD HTML

El `prd.html` usa [Lucide](https://lucide.dev) vía CDN (`lucide@latest`), inicializado con `lucide.createIcons()`. Cada ícono es `<i data-lucide="nombre"></i>`.

Usa este set curado para que el PRD se vea consistente. No inventes nombres: si dudas, verifica en lucide.dev/icons.

## Por sección del PRD

| Sección | Ícono (`data-lucide`) |
|---|---|
| Título / propósito | `target` |
| Qué hace la app (features) | `sparkles` |
| Ya provisto por el starter | `package-check` |
| Fuera de alcance (v1) | `circle-slash` |
| Integraciones externas | `plug` |
| Modelo de datos | `database` |
| Riesgos | `triangle-alert` |
| Supuestos | `list-checks` |
| Milestones | `flag` |
| Milestone individual | `milestone` |
| Done when / verificación | `circle-check-big` |
| Stack técnico | `layers` |
| Credenciales | `key-round` |
| Costo aproximado | `wallet` |

## Badges y estados

| Uso | Ícono |
|---|---|
| Feature sugerida por el agente (`auto: true`) | `bot` |
| Feature confirmada por el usuario | `check` |
| Bloqueado / pendiente de credencial | `lock` |
| Nota / advertencia inline | `info` |

## Categorías útiles por tipo de feature

| Tipo de feature | Ícono sugerido |
|---|---|
| Auth / usuarios | `user-round` |
| Pagos / facturación | `credit-card` |
| Mensajería / notificaciones | `bell` |
| Email | `mail` |
| WhatsApp / chat | `message-circle` |
| Dashboard / reportes | `chart-column` |
| Archivos / uploads | `upload` |
| Búsqueda | `search` |
| Configuración | `settings` |
| Calendario / agenda | `calendar` |
| Automatización / jobs | `workflow` |
| IA / generación | `wand-sparkles` |

## Snippet de inicialización (ya va en el template)

```html
<script src="https://unpkg.com/lucide@latest"></script>
<script>lucide.createIcons();</script>
```
