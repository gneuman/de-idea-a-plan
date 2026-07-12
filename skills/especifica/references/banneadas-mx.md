# Banneadas — Español de México

Lista de patrones prohibidos en la especificación generada, en la conversación durante la entrevista, y en los `prompt.md` por milestone. Esta lista se aplica además de las reglas globales de `skills/voz-gnb/`.

## Voseo y argentinismos

Prohibido absoluto. Reemplaza:

| Banneado | Usar en su lugar |
|---|---|
| vos / tenés | tú / tienes |
| acá | aquí |
| allá (cuando significa "ahí") | ahí |
| ¿viste? | ¿ves? / ¿entendiste? |
| grabás / pedís / hacés | grabas / pides / haces |
| che | (omitir) |
| dale | sí / OK / listo |
| sos | eres |
| podés | puedes |
| querés | quieres |
| listo (al inicio) | OK / perfecto |
| pibe / piba | persona / chavo |
| laburo | trabajo / chamba |
| boludo / boluda | (nunca usar) |
| copado / re-copado | bueno / muy bueno |
| chamuyar | convencer / vender |
| mate (refresco) | café (en México) |

## Fluff corporativo

Cero tolerancia. Reemplaza:

| Banneado | Razón / Usar |
|---|---|
| solución integral | vacío — describe qué hace |
| ecosistema digital | vacío — nombra la plataforma |
| transformar la industria | aspiracional vacío — di qué cambia para el usuario |
| revolucionario | nunca |
| innovador | nunca |
| de vanguardia | nunca |
| disruptivo | nunca |
| sinergias | nunca |
| robusto y escalable | describe el caso real |
| world-class | nunca |
| best-in-class | nunca |
| customer-centric | (cualquier customer-X) — sé concreto |
| stakeholders | usuarios / equipo / cliente |
| accionables | que se pueden ejecutar |
| empoderar | habilitar / dar |
| líder en el mercado | nunca (es opinión) |
| solución end-to-end | de inicio a fin |
| seamless | sin fricción / fluido |

## Anglicismos innecesarios

Reemplaza cuando exista equivalente claro en español:

| Banneado | Usar |
|---|---|
| dashboard | tablero |
| feature | feature (queda — es término técnico claro) |
| feedback | retroalimentación / comentarios |
| login | inicio de sesión / login (queda en UI) |
| signup | registro / signup (queda en UI) |
| onboarding | inducción / onboarding (queda en UI) |
| workflow | flujo de trabajo |
| insights | hallazgos / patrones |
| roadmap | hoja de ruta / roadmap (queda en plan) |
| stakeholder | involucrado / interesado |
| deliverable | entregable |
| timeline | calendario / cronograma |
| kickoff | arranque / kickoff (queda en agenda) |
| milestone | hito / milestone (queda en build plan) |
| brief | brief (queda — es término del oficio) |
| commitment | compromiso |

**Regla:** términos técnicos del oficio (feature, prompt, API, branch, deploy, milestone) se quedan en inglés porque cambiar los nombres confunde. Anglicismos generales (dashboard, deliverable, timeline) van a español.

## Anti-patrones de especificaciones

Frases que delatan especificación genérica de ChatGPT — prohibidas:

- "Esta plataforma busca..." → di qué hace
- "Es importante destacar que..." → solo afirma
- "En el contexto actual..." → fuera
- "Brindar una experiencia..." → di qué pasa
- "El usuario podrá disfrutar de..." → di qué hace
- "Garantizar la mejor experiencia..." → fuera
- "Optimizar los procesos..." → di cuáles, cómo

## Para el agente

Si vas a escribir algo en la especificación y dudas si pasa el filtro:

1. ¿Una persona real lo diría hablando? Si no, fuera.
2. ¿Lo puedes reemplazar con un sustantivo concreto o un verbo de acción? Hazlo.
3. ¿Aporta información nueva? Si no, borra.
