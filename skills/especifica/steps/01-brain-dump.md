# Fase 1 — Brain dump

Capturar la descripción cruda del usuario en sus propias palabras. Sin estructura, sin AskUserQuestion, sin guiar.

## Caso A — el primer mensaje ya es brain dump

Si el primer mensaje del usuario ya describe sustantivamente la idea (más de 2 oraciones, menciona qué hace + para quién + problema que resuelve), úsalo como tu brain dump. Pasa directo a Fase 2.

## Caso B — el primer mensaje es vago

Si el mensaje fue genérico ("ayúdame con una especificación", "necesito un documento para un cliente"), pide brain dump en texto libre:

> Antes de empezar, descríbeme la idea como si me la estuvieras contando en una llamada. Tres cosas:
>
> 1. ¿Qué es? (en tus palabras, sin formato)
> 2. ¿Qué problema resuelve y para quién?
> 3. ¿Por qué ahora? (qué disparó esto)
>
> Escríbelo como te salga. Yo lo ordeno después.

## Qué guardar

Guarda el brain dump literal (cópialo a memoria de sesión). Las siguientes fases lo van a parafrasear y estructurar — pero el brain dump literal es la referencia para no inventar features que el usuario no dijo.

## Detección de complejidad

Después de capturarlo, calibra el tamaño del proyecto. Esto afina cuántas decisiones haces en fases siguientes:

| Señales de simple | Señales de complejo |
|---|---|
| Una sola feature core | 5+ features distintas |
| Sin integraciones externas | Múltiples APIs / SAT / pagos / WhatsApp |
| Sin auth o auth básica | Roles, permisos, multi-tenant |
| Sin datos sensibles | PII, datos financieros, CFDIs |
| Un solo tipo de usuario | Admin + cliente + interno + público |

Idea **simple** → comprime: 3–4 features, 1 milestone, sin integraciones, brain dump más corto.
Idea **balanceada** → default (12–15 decisiones).
Idea **compleja** → expande: más features, más milestones, riesgos detallados.

No le digas al usuario tu calibración. Solo úsala internamente para no abrumar (ideas simples) ni quedarte corto (ideas complejas).

## Bloquear

Pasa a Fase 2 con:
- Brain dump literal en memoria
- Calibración de complejidad: simple / balanceada / compleja
