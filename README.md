# PRD Creator

**Convierte una idea en un PRD listo para construir — y mándalo a Linear solo.**

Una skill gratis y open source para Claude Code que toma tu idea difusa y la vuelve una especificación cerrada: un PRD visual (HTML), milestones ejecutables por un agente, e issues en Linear. En español de México.

Inspirado en [PRD Creator de Builder Methods](https://github.com/buildermethods/bm-prd-creator). La diferencia: aquí el PRD sale **visual (HTML)** y los milestones se **suben a Linear** con un comando.

---

## Qué te llevas

Al terminar la entrevista con el agente, tienes tres cosas en tu repo:

1. **`_prd/prd.html`** — el PRD visual. Lo abres con doble click, se ve bien, lo compartes con quien sea (técnico o no).
2. **`_prd/prd.md`** — el mismo PRD en Markdown, para editar a mano o que lo lea un agente.
3. **`_prd/milestones/N-nombre/prompt.md`** — un prompt ejecutable por milestone, para que un agente de código construya de a poco sin perderse.

Y si conectas Linear: esos milestones se vuelven **issues + Project Milestones nativos** con el comando `/to-linear`.

> Mira un PRD de ejemplo ya generado en [`examples/ejemplo-prd.html`](examples/ejemplo-prd.html) (ábrelo en tu navegador).

---

## Por qué existe

Cuando le pides a un agente de IA que construya algo a partir de una idea vaga, improvisa. Inventa features que no pediste, se salta las que sí, y a la tercera sesión ya no sabes qué construyó.

Un PRD arregla eso: es la especificación cerrada contra la que el agente construye. Este skill te lo hace **conversando** — una decisión a la vez, siempre proponiendo un default con su razón, para que tú edites en vez de generar desde cero.

---

## Instalación

Necesitas [Claude Code](https://claude.com/claude-code).

### Opción A — como plugin

```bash
# Dentro de Claude Code, agrega este repo como plugin:
/plugin marketplace add gneuman/prd-creator-gnb
/plugin install prd-creator-gnb
```

### Opción B — copiar las skills a mano

```bash
git clone https://github.com/gneuman/prd-creator-gnb.git
cp -r prd-creator-gnb/skills/prd ~/.claude/skills/prd
cp -r prd-creator-gnb/skills/to-linear ~/.claude/skills/to-linear
```

Reinicia Claude Code y ya tienes `/prd` y `/to-linear`.

---

## Conectar Linear (opcional pero es lo bueno)

El skill `/to-linear` sube tus milestones a Linear. Para eso necesitas el MCP de Linear conectado:

1. Copia [`.mcp.json.example`](.mcp.json.example) a `.mcp.json` en tu repo (o agrégalo a tu config global de Claude Code).
2. Dentro de Claude Code corre `/mcp` y autentícate con tu cuenta de Linear.
3. Listo. Ahora `/to-linear` puede crear issues y milestones.

Sin Linear, el skill igual te genera el PRD y los prompts por milestone — solo no los sube.

---

## El flujo

Todo pasa conversando con el agente. Corres `/prd`, le cuentas tu idea, y él te guía por estas fases (una decisión a la vez, con defaults que puedes aceptar de golpe):

| # | Fase | Qué se decide |
|---|------|---------------|
| 1 | **Brain dump** | Cuentas la idea en tus palabras, sin formato. |
| 2 | **Formato** | HTML, Markdown o ambos. |
| 3 | **Propósito** | El qué-es en 1–3 oraciones. |
| 4 | **Features** | Las 4–8 cosas que la app hace (in-scope). |
| 5 | **Fuera de alcance** | Lo que NO va en v1 (igual de importante). |
| 6 | **Stack** | Detecta lo que ya tienes o recomienda uno. |
| 7 | **Integraciones** | Qué servicios externos y qué credenciales (con catálogo LATAM). |
| 8 | **Modelo de datos** | Qué recuerda la app, en lenguaje plano. |
| 9 | **Scope por feature** | In/out detallado de cada feature. |
| 10 | **Milestones** | Cómo trocear el build en sesiones cerradas. |
| 11 | **Riesgos y supuestos** | Qué puede tronar y qué se asume. |
| 12 | **Escribir** | Genera los archivos en `_prd/`. |

Luego, opcional:

```
/to-linear
```

...y tus milestones ya son issues en Linear, listos para que el equipo (o un agente) los tome.

---

## Cómo usar el output

- **Para revisar:** abre `_prd/prd.html` en el navegador.
- **Para construir con un agente:** arranca una sesión nueva, abre `_prd/milestones/1-*/prompt.md` y dile al agente "empieza por aquí". El agente planea y construye solo ese milestone, y al terminar escribe un `milestone-log.md` con lo que hizo. Repites por cada milestone.
- **Para el equipo:** corre `/to-linear` y trabaja desde Linear.

---

## Personalizarlo

Cada skill tiene un bloque `## [CUSTOMIZE]` al final con su config en YAML: idioma, marca del footer, carpeta de salida, stack default, labels de Linear. Edítalo al forkear para tu contexto.

Por ejemplo, para cambiar el idioma del PRD a español neutro o inglés, edita `idioma:` en `skills/prd/SKILL.md`.

---

## Créditos

- Flujo idea → PRD → milestones: [PRD Creator](https://github.com/buildermethods/bm-prd-creator) de Brian Casel / Builder Methods.
- Vertical slices / tracer bullets: [to-tickets](https://github.com/mattpocock/skills) de Matt Pocock (MIT).
- Adaptación al español, salida HTML y conexión Linear: [Gabriel Neuman / GNB Labs](https://gabrielneuman.com).

MIT. Úsalo, forkéalo, véndelo con tu marca.

---

## ¿Quieres que te lo enseñe en vivo?

Doy un workshop donde armamos tu primer PRD + Linear con este flujo, sobre una idea real tuya, en una sentada. Sales con el PRD hecho y el sistema instalado.

→ **[gabrielneuman.com/prd-creator](https://gabrielneuman.com/prd-creator/)**
