# Fase 6 — Stack técnico y starter

Primero **detecta** lo que ya hay. Luego **confirma**. Si no hay nada, **recomienda** un default.

## 1. Detectar (sin preguntar)

Sin abrir AskUserQuestion, lee del repo actual:

1. **Archivos de instrucciones:** `CLAUDE.md`, `AGENTS.md` — suelen declarar el stack y convenciones.
2. **Configs raíz:** `package.json`, `Gemfile`, `composer.json`, `requirements.txt`, `pyproject.toml`, `go.mod`, `Cargo.toml`.
3. **Estructura de carpetas:** `app/` + `config/` + `db/migrate/` → Rails. `app/` + `pages/` → Next.js. `src/components/` + `package.json` con next → Next.js App Router.

## 2. Detectar el contexto del repo

| Tipo de repo | Qué hacer |
|---|---|
| Repo con `CLAUDE.md`/`AGENTS.md` que declara stack | Usa lo que declara. No lo cambies sin preguntar. |
| Repo Rails existente | Confirma versión + qué starter |
| Repo Next.js existente | Confirma App Router vs Pages |
| Repo fresco / vacío | Recomienda el `stack_default` del bloque `[CUSTOMIZE]` (Next.js por defecto) |

## 3. Summary al usuario

```
Lo que detecté:

- Framework: {Next.js / Rails / etc}
- DB: {PostgreSQL / MongoDB / etc}
- Auth: {NextAuth / Devise / etc}
- Deploy: {Vercel / Render / Fly.io / etc}
- Starter ya incluye: {signup, login, app shell, dark mode, etc}

¿Vamos con este stack o cambiamos algo?
```

## 4. Si la detección fue vacía

Si el repo está vacío o ambiguo, **recomienda** y deja override. AskUserQuestion:

- **Usar el default recomendado ({stack_default})** — Recommended. Ver `references/stacks.md`.
- **Otro stack — lo digo en chat** — Texto libre.
- **No sé, explica mis opciones** — Lee `references/stacks.md` al usuario, después vuelve a preguntar.

## 5. Confirmar qué provee el starter

Pregunta qué viene ya construido en el starter (para NO re-especificar después). Casi todos los starters modernos (Rails 8, Next.js con auth, etc.) ya incluyen algo como:

```
El starter ya provee:

- Signup / login con email + password
- Reset password por email
- Modelo de User
- App shell autenticado (sidebar + topbar)
- Pantallas de settings y perfil
- Dark mode toggle
- Email transaccional (preview en dev)
- Job queue / cron

¿Confirmas que esto NO se re-especifica en el PRD, o quitamos algo?
```

Ajusta la lista a lo que el usuario diga que su starter incluye. Si no usa starter (proyecto desde cero), esta lista va vacía y esas features SÍ entran al PRD.

## 6. Bloquear

Guarda en memoria:
- `stack` (array de tecnologías: `["Next.js", "React", "Tailwind", "PostgreSQL", "Vercel"]`)
- `starter_name` (nombre del starter o "custom" / "desde cero")
- `starter_provee` (array de capacidades ya construidas, NO se re-especifican)

Pasa a Fase 7.

## No hagas

- ❌ No prescribas librerías específicas más allá del stack base (no decidas `date-fns` vs `dayjs`).
- ❌ No prescribas patrones internos (estado, routing, etc).
- ❌ No prescribas testing framework (eso es decisión del agente en plan mode).
- ❌ No incluyas hosting/deploy details si no son críticos.
