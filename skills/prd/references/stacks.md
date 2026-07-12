# Stacks — defaults por tipo de proyecto

Defaults sensatos por tipo de proyecto. Estos son sugerencias para cuando el repo está vacío; si el repo ya declara un stack en `CLAUDE.md`/`package.json`/etc., respeta ese. Cambia el default en el bloque `[CUSTOMIZE]` del SKILL.

## Stack web full-stack (recomendado para la mayoría de apps)

| Capa | Tecnología | Razón |
|---|---|---|
| Framework | Next.js (App Router) + React | Server components, streaming, ecosistema enorme |
| Estilos | Tailwind + @tailwindcss/typography | Velocidad. No discutir colores. |
| UI components | shadcn/ui | Copy-paste, sin lock-in |
| DB | PostgreSQL o MongoDB | Postgres si hay relaciones fuertes; Mongo si el schema es flexible |
| Auth | NextAuth / Auth.js | Email + password + magic link |
| Deploy | Vercel | Cron + Edge + previews automáticas |
| Email | Resend | Buena DX, precios razonables |
| Storage | Cloudinary / S3 / R2 | Transformaciones on-the-fly (Cloudinary) o barato (R2) |
| AI | Anthropic SDK | Claude Opus/Sonnet/Haiku |

### Qué suele proveer un starter moderno

Muchos starters (create-t3-app, etc.) ya traen:
- Signup / login / reset password
- User model
- App shell autenticado (sidebar + topbar + responsive)
- Settings + perfil
- Dark mode toggle
- Email transaccional con preview en dev

Si tu starter ya trae esto, NO lo re-especifiques en el PRD. Si arrancas desde cero, esas piezas SÍ entran al PRD.

## Stack Rails (alternativa full-stack)

Para equipos con preferencia Ruby.

| Capa | Tecnología |
|---|---|
| Framework | Rails 8 |
| Frontend | Inertia + React, o Hotwire |
| Estilos | Tailwind + shadcn |
| DB | PostgreSQL |
| Jobs | Solid Queue |
| Auth | Devise / Rodauth |
| Deploy | Render / Fly.io / Kamal |

## Stack ligero (microsites / landings)

Para proyectos sin backend.

| Capa | Tecnología |
|---|---|
| Framework | Astro (o Next.js si necesitas SSR) |
| Estilos | Tailwind |
| Hosting | Vercel / Cloudflare Pages |
| Forms | Formspree / Resend |
| Analytics | Plausible / Vercel Analytics |

## Stack mobile-first (PWA, no nativa)

Para apps que se usan en celular pero NO requieren tienda de apps.

Stack full-stack + extras:
- `next-pwa` para hacerla instalable
- IndexedDB para offline (Dexie.js cuando crece)
- Web Push API (Notifications)

## Cuándo respetar otro stack

- El equipo solo sabe Django / Laravel / etc. — respeta lo que dominan.
- App real-time multiplayer de baja latencia — considera Phoenix LiveView / Elixir.
- Requisito legal de on-prem — Rails/Django empacan más fácil que un stack serverless.
- El cliente tiene contrato con un cloud específico (Azure/AWS/GCP) — adáptate.

## Tabla de decisión rápida

| Tipo de proyecto | Stack default |
|---|---|
| CRM / dashboard / herramienta interna | Next.js full-stack |
| Facturación / ops financieras | Next.js full-stack + integraciones locales |
| Landing con formularios | Astro (ligero) |
| App móvil (sin tienda) | Next.js + PWA |
| App con flujos legales complejos | Rails |
| Microsite single-purpose | Astro |
| Side project para aprender | Lo que quieras probar |
