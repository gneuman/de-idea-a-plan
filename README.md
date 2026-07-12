# De Idea a Plan

**De una idea difusa a un plan claro para construir tu app — y lo mandas a Linear solo.**

Una herramienta gratis y open source para [Claude Code](https://claude.com/claude-code). Le cuentas tu idea conversando, y en unos minutos tienes un plan visual de lo que se va a construir, partido en etapas, listo para que un agente de IA lo arme sin inventar cosas de más. En español de México.

---

## Qué te llevas

Al terminar de platicar con el agente, tienes en tu carpeta:

1. **`_plan/plan.html`** — el plan visual. Lo abres con doble click y lo entiende cualquiera, técnico o no.
2. **`_plan/plan.md`** — el mismo plan en texto, para editar a mano o dárselo a un agente.
3. **`_plan/milestones/…/prompt.md`** — una instrucción por etapa, para que un agente de código construya de a poco sin perderse.

Y si conectas Linear, esas etapas se vuelven **tareas y milestones** con el comando `/to-linear`.

> 👀 Mira un plan de ejemplo ya hecho: [`examples/ejemplo-plan.html`](examples/ejemplo-plan.html) (ábrelo en tu navegador).

---

## Por qué existe

Cuando le pides a un agente de IA que construya algo desde una idea vaga, improvisa. Inventa cosas que no pediste, se salta las que sí, y a la tercera sesión ya no sabes qué construyó.

Un plan cerrado arregla eso: es contra lo que el agente construye, sin inventar. Y este lo armas **conversando** — una decisión a la vez, con el agente proponiéndote un default y su razón, para que tú solo corrijas en vez de escribir desde cero. No necesitas saber de código.

---

## Instalación

### Como plugin (recomendado)

Dentro de Claude Code:

```
/plugin marketplace add gneuman/de-idea-a-plan
/plugin install de-idea-a-plan
```

### O copiando las skills a mano

```bash
git clone https://github.com/gneuman/de-idea-a-plan.git
cp -r de-idea-a-plan/skills/idea ~/.claude/skills/idea
cp -r de-idea-a-plan/skills/to-linear ~/.claude/skills/to-linear
```

Reinicia Claude Code y ya tienes `/idea` y `/to-linear`.

---

## Cómo se usa

1. Corre **`/idea`** y cuéntale tu idea como si me la contaras en una llamada.
2. El agente te lleva de la mano: propósito, qué hace la app, qué NO va en la primera versión, con qué se construye, qué recuerda, y en qué etapas se arma.
3. Al final escribe tu plan en `_plan/`.

Luego, con el plan listo:

- **Para construir:** abre `_plan/milestones/1-…/prompt.md`, arranca una sesión nueva y dile al agente "empieza por aquí". Construye solo esa etapa, deja nota de lo que hizo, y sigues con la siguiente.
- **Para el equipo:** corre **`/to-linear`** y todo queda como tareas en Linear.

---

## Conectar Linear (opcional)

`/to-linear` sube las etapas a Linear. Necesitas el conector (MCP) de Linear:

1. Copia [`.mcp.json.example`](.mcp.json.example) a `.mcp.json`.
2. En Claude Code corre `/mcp` y entra con tu cuenta de Linear.

Sin Linear, el plan y las instrucciones por etapa igual se generan — solo no se suben.

---

## Hazlo tuyo

Cada skill trae un bloque `## [CUSTOMIZE]` al final con su config: idioma, marca del pie de página, carpeta de salida, stack default. Edítalo al forkear. MIT — úsalo, forkéalo, véndelo con tu marca.

---

## Créditos

Hecho por [Gabriel Neuman / GNB Labs](https://gabrielneuman.com). Licencia MIT — ver [`LICENSE`](LICENSE) para las atribuciones del trabajo previo en que se apoya.

---

## ¿Quieres que te lo enseñe en vivo?

Doy un taller donde armamos tu primer plan + Linear con este flujo, sobre una idea real tuya, en una sentada. Sales con el plan hecho y el sistema funcionando.

→ **[gabrielneuman.com/de-idea-a-plan](https://gabrielneuman.com/de-idea-a-plan/)**
