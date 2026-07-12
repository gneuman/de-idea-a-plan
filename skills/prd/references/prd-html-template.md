# Template HTML del PRD

Cuando el usuario eligió **HTML** o **Ambos** en Fase 2, escribe `prd.html` (en `_prd/`) usando este scaffold.

Archivo autocontenido — solo CDN de Tailwind, Google Fonts e íconos Lucide. Sin build step, sin imports locales.

## Scaffold base

Empieza cada `prd.html` con esto. Llena los `{{PLACEHOLDERS}}` y bloques de sección descritos abajo. NO renombres clases CSS — están escritas para Tailwind Play CDN.

```html
<!doctype html>
<html lang="es-MX">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>{{APP_NAME}} — PRD</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = { darkMode: 'class' };
  </script>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    html { font-family: 'Inter', system-ui, -apple-system, sans-serif; }
    body { font-feature-settings: "cv11", "ss01"; }
    @media print {
      html { background: white !important; color: black !important; color-scheme: light; }
      html.dark { color-scheme: light; }
      html.dark body, html.dark * { background: white !important; color: black !important; border-color: #d4d4d8 !important; }
      .no-print { display: none !important; }
      .print-card { break-inside: avoid; page-break-inside: avoid; }
      header.sticky { position: static !important; backdrop-filter: none !important; }
      main { padding-top: 0 !important; }
      a { color: black !important; text-decoration: none !important; }
    }
  </style>
</head>
<body class="bg-zinc-50 dark:bg-zinc-950 text-zinc-900 dark:text-zinc-100 antialiased">
  <header class="sticky top-0 z-10 backdrop-blur bg-zinc-50/80 dark:bg-zinc-950/80 border-b border-zinc-200 dark:border-zinc-800">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 py-3 flex items-center justify-between">
      <span class="text-sm font-medium text-zinc-500 dark:text-zinc-400">PRD · {{APP_NAME}}</span>
      <button id="theme-toggle" class="no-print inline-flex items-center justify-center w-9 h-9 rounded-md border border-zinc-200 dark:border-zinc-800 hover:bg-zinc-100 dark:hover:bg-zinc-900 transition" aria-label="Cambiar tema">
        <i data-lucide="sun" class="hidden dark:inline-block w-4 h-4"></i>
        <i data-lucide="moon" class="inline-block dark:hidden w-4 h-4"></i>
      </button>
    </div>
  </header>

  <main class="max-w-4xl mx-auto px-4 sm:px-6 py-10 sm:py-14 space-y-14">

    {{DISCLAIMER_BLOCK}}

    <!-- HERO -->
    <section>
      <h1 class="text-4xl sm:text-5xl font-bold tracking-tight">{{APP_NAME}}</h1>
      <p class="mt-5 text-lg sm:text-xl text-zinc-600 dark:text-zinc-400 leading-relaxed">{{PROPOSITO}}</p>
      <div class="mt-6 flex flex-wrap gap-2">
        {{TECH_STACK_BADGES}}
      </div>
    </section>

    <!-- QUÉ HACE LA APP -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="sparkles" class="w-3.5 h-3.5"></i>Qué hace la app
      </h2>
      <ul class="mt-5 grid grid-cols-1 sm:grid-cols-2 gap-3 list-none p-0">
        {{FEATURE_CARDS}}
      </ul>
    </section>

    <!-- YA PROVISTO -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="package-check" class="w-3.5 h-3.5"></i>Ya provisto por {{STARTER_NAME}}
      </h2>
      <ul class="mt-5 flex flex-wrap gap-2 list-none p-0">
        {{STARTER_PROVEE_PILLS}}
      </ul>
    </section>

    <!-- FUERA DE ALCANCE -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="minus-circle" class="w-3.5 h-3.5"></i>Fuera de alcance (v1)
      </h2>
      <ul class="mt-5 space-y-2.5 list-none p-0">
        {{FUERA_DE_ALCANCE_ITEMS}}
      </ul>
    </section>

    <!-- INTEGRACIONES (omitir bloque entero si no hay) -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="plug" class="w-3.5 h-3.5"></i>Integraciones externas
      </h2>
      <div class="mt-5 grid grid-cols-1 sm:grid-cols-2 gap-3">
        {{INTEGRACION_CARDS}}
      </div>
    </section>

    <!-- MODELO DE DATOS -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="database" class="w-3.5 h-3.5"></i>Modelo de datos
      </h2>
      <p class="mt-3 text-sm text-zinc-500 dark:text-zinc-400">Lo que la app necesita recordar.</p>
      <div class="mt-5 grid grid-cols-1 sm:grid-cols-2 gap-3">
        {{ENTIDAD_CARDS}}
      </div>
    </section>

    <!-- MILESTONES -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="route" class="w-3.5 h-3.5"></i>Milestones
      </h2>
      <div class="mt-5 space-y-5">
        {{MILESTONE_CARDS}}
      </div>
    </section>

    <!-- RIESGOS -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="alert-triangle" class="w-3.5 h-3.5"></i>Riesgos
      </h2>
      <div class="mt-5 overflow-hidden rounded-lg border border-zinc-200 dark:border-zinc-800">
        <table class="w-full text-sm">
          <thead class="bg-zinc-100 dark:bg-zinc-900">
            <tr>
              <th class="px-4 py-2 text-left text-xs font-semibold uppercase tracking-wide text-zinc-500">#</th>
              <th class="px-4 py-2 text-left text-xs font-semibold uppercase tracking-wide text-zinc-500">Riesgo</th>
              <th class="px-4 py-2 text-left text-xs font-semibold uppercase tracking-wide text-zinc-500">Impacto</th>
              <th class="px-4 py-2 text-left text-xs font-semibold uppercase tracking-wide text-zinc-500">Mitigación</th>
            </tr>
          </thead>
          <tbody class="divide-y divide-zinc-200 dark:divide-zinc-800 bg-white dark:bg-zinc-900">
            {{RIESGO_ROWS}}
          </tbody>
        </table>
      </div>
    </section>

    <!-- SUPUESTOS -->
    <section>
      <h2 class="text-xs font-semibold uppercase tracking-[0.18em] text-zinc-500 dark:text-zinc-400 flex items-center gap-2">
        <i data-lucide="check-square" class="w-3.5 h-3.5"></i>Supuestos
      </h2>
      <ul class="mt-5 space-y-2 list-none p-0">
        {{SUPUESTO_ITEMS}}
      </ul>
    </section>

    <footer class="pt-8 border-t border-zinc-200 dark:border-zinc-800 text-xs text-zinc-500 dark:text-zinc-400 flex items-center justify-between">
      <span>{{FOOTER_CREDITO}} · {{TIMESTAMP}}</span>
      <span class="hidden sm:inline">PRD de build</span>
    </footer>
  </main>

  <script>
    (function () {
      var html = document.documentElement;
      var stored = localStorage.getItem('prd-theme');
      var prefersDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
      var initial = stored ? stored : (prefersDark ? 'dark' : 'light');
      if (initial === 'dark') html.classList.add('dark');
      var btn = document.getElementById('theme-toggle');
      if (btn) {
        btn.addEventListener('click', function () {
          var isDark = html.classList.toggle('dark');
          localStorage.setItem('prd-theme', isDark ? 'dark' : 'light');
        });
      }
      if (window.lucide) window.lucide.createIcons();
    })();
  </script>
</body>
</html>
```

## Bloques por placeholder

### `{{DISCLAIMER_BLOCK}}`

Bloque amber (nota de "archivo temporal"):

```html
<div class="rounded-lg border border-amber-200 dark:border-amber-900/60 bg-amber-50 dark:bg-amber-950/30 p-4 text-sm text-amber-900 dark:text-amber-200">
  <p><strong class="font-semibold">Sobre este archivo:</strong> Todo en <code class="font-mono text-xs">_prd/</code> (este PRD y las carpetas de milestones) es un artefacto temporal de documentación para el build inicial. No es funcional — ningún código, configuración, runtime, test o deploy debe importar, leer o depender de archivos en <code class="font-mono text-xs">_prd/</code>. Cuando los milestones estén completos, se puede borrar la carpeta.</p>
</div>
```

### `{{APP_NAME}}`

Nombre del proyecto. Si no fue preguntado explícitamente, deduce del propósito y pregunta antes de escribir.

### `{{PROPOSITO}}`

El propósito locked en Fase 3 (1-3 oraciones).

### `{{TECH_STACK_BADGES}}`

Un badge por tecnología del stack locked en Fase 6. Solo las relevantes (framework, DB, hosting, libs clave).

```html
<span class="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-full bg-white dark:bg-zinc-900 border border-zinc-200 dark:border-zinc-800 text-xs font-medium text-zinc-700 dark:text-zinc-300">{{TECH_NAME}}</span>
```

### `{{FEATURE_CARDS}}`

Una `<li>` por feature de "Qué hace la app" (las locked en Fase 4). Ícono Lucide apropiado.

```html
<li class="print-card rounded-lg border border-zinc-200 dark:border-zinc-800 bg-white dark:bg-zinc-900 p-4">
  <div class="flex items-start gap-3">
    <div class="shrink-0 mt-0.5 w-8 h-8 rounded-md bg-zinc-100 dark:bg-zinc-800 flex items-center justify-center">
      <i data-lucide="{{LUCIDE_ICON}}" class="w-4 h-4 text-zinc-700 dark:text-zinc-300"></i>
    </div>
    <div>
      <p class="font-medium text-zinc-900 dark:text-zinc-100">{{FEATURE_LABEL}}</p>
      <p class="mt-1 text-sm text-zinc-600 dark:text-zinc-400 leading-relaxed">{{FEATURE_DESCRIPCION}}</p>
    </div>
  </div>
</li>
```

Si la feature entró con `auto: true` (Fase 9 fatigue), agrega badge antes del label:

```html
<span class="inline-flex items-center gap-1 px-1.5 py-0.5 rounded text-[10px] font-medium bg-indigo-100 dark:bg-indigo-900/40 text-indigo-700 dark:text-indigo-300 mr-1.5">
  <i data-lucide="bot" class="w-3 h-3"></i>auto
</span>
```

### `{{STARTER_PROVEE_PILLS}}`

Un pill por capacidad del starter (Fase 6).

```html
<li class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded-md bg-white dark:bg-zinc-900 border border-zinc-200 dark:border-zinc-800 text-sm text-zinc-700 dark:text-zinc-300">
  <i data-lucide="check" class="w-3.5 h-3.5 text-emerald-600 dark:text-emerald-400"></i>{{ITEM}}
</li>
```

### `{{FUERA_DE_ALCANCE_ITEMS}}`

Una entrada por item de Fase 5.

```html
<li class="flex items-start gap-3">
  <i data-lucide="x" class="w-4 h-4 mt-1 shrink-0 text-zinc-400 dark:text-zinc-600"></i>
  <span class="text-zinc-700 dark:text-zinc-300"><span class="font-medium">{{ITEM}}</span><span class="text-zinc-500 dark:text-zinc-400"> — {{RAZON}}</span></span>
</li>
```

### `{{INTEGRACION_CARDS}}`

Una card por integración locked en Fase 7. Si no hay integraciones, **omite la sección completa** (todo el `<section>` del HTML scaffold).

```html
<div class="print-card rounded-lg border border-zinc-200 dark:border-zinc-800 bg-white dark:bg-zinc-900 p-5">
  <div class="flex items-center gap-2">
    <i data-lucide="plug" class="w-4 h-4 text-zinc-500 dark:text-zinc-400"></i>
    <h3 class="font-semibold text-zinc-900 dark:text-zinc-100">{{PROVEEDOR}}</h3>
    <span class="ml-auto text-xs text-zinc-500 dark:text-zinc-400">{{PARA_QUE}}</span>
  </div>
  <p class="mt-3 text-sm text-zinc-600 dark:text-zinc-400 leading-relaxed">{{EXPLICACION_PLANA}}</p>
  <p class="mt-4 text-[11px] font-semibold uppercase tracking-[0.16em] text-zinc-500 dark:text-zinc-400 flex items-center gap-1.5"><i data-lucide="key" class="w-3 h-3"></i>Credenciales que conseguir</p>
  <ul class="mt-2 space-y-1.5 list-none p-0">
    <!-- repetir por credencial -->
    <li class="flex items-center gap-2 text-sm text-zinc-700 dark:text-zinc-300"><i data-lucide="key-round" class="w-3.5 h-3.5 text-zinc-400 dark:text-zinc-500"></i>{{CREDENCIAL}}</li>
  </ul>
</div>
```

### `{{ENTIDAD_CARDS}}`

Una card por entidad de Fase 8. Campos en plain language en tabla.

```html
<div class="print-card rounded-lg border border-zinc-200 dark:border-zinc-800 bg-white dark:bg-zinc-900 p-5">
  <div class="flex items-center gap-2">
    <i data-lucide="box" class="w-4 h-4 text-zinc-500 dark:text-zinc-400"></i>
    <h3 class="font-semibold text-zinc-900 dark:text-zinc-100">{{ENTIDAD_NAME}}</h3>
  </div>
  <table class="mt-4 w-full text-sm">
    <tbody class="divide-y divide-zinc-100 dark:divide-zinc-800">
      <!-- repetir por campo -->
      <tr>
        <td class="py-2 pr-4 font-mono text-xs font-medium text-zinc-700 dark:text-zinc-300 align-top whitespace-nowrap">{{CAMPO_NAME}}</td>
        <td class="py-2 text-zinc-600 dark:text-zinc-400 leading-relaxed">{{CAMPO_DESCRIPCION}}</td>
      </tr>
    </tbody>
  </table>
  <p class="mt-4 text-xs text-zinc-500 dark:text-zinc-400"><span class="font-semibold uppercase tracking-[0.14em] text-[11px]">Relaciones</span> · {{RELACIONES}}</p>
</div>
```

### `{{MILESTONE_CARDS}}`

Una card por milestone de Fase 10.

```html
<article class="print-card rounded-lg border border-zinc-200 dark:border-zinc-800 bg-white dark:bg-zinc-900 overflow-hidden">
  <header class="flex items-center gap-3 p-5 border-b border-zinc-100 dark:border-zinc-800">
    <span class="shrink-0 w-8 h-8 rounded-full bg-zinc-900 dark:bg-zinc-100 text-zinc-50 dark:text-zinc-900 flex items-center justify-center text-sm font-semibold">{{N}}</span>
    <h3 class="font-semibold text-lg text-zinc-900 dark:text-zinc-100">{{MILESTONE_NAME}}</h3>
  </header>
  <div class="p-5">
    <p class="text-zinc-600 dark:text-zinc-400 leading-relaxed">{{MILESTONE_FRAMING}}</p>
    <div class="mt-5 grid grid-cols-1 md:grid-cols-2 gap-5">
      <div>
        <h4 class="text-[11px] font-semibold uppercase tracking-[0.16em] text-zinc-500 dark:text-zinc-400 flex items-center gap-1.5">
          <i data-lucide="check-circle-2" class="w-3.5 h-3.5 text-emerald-600 dark:text-emerald-400"></i>Qué se construye
        </h4>
        <ul class="mt-3 space-y-2 text-sm text-zinc-700 dark:text-zinc-300 list-none p-0">
          <!-- repetir -->
          <li class="flex items-start gap-2"><i data-lucide="check" class="w-3.5 h-3.5 mt-0.5 shrink-0 text-emerald-600 dark:text-emerald-400"></i><span>{{IN_SCOPE_ITEM}}</span></li>
        </ul>
      </div>
      <div>
        <h4 class="text-[11px] font-semibold uppercase tracking-[0.16em] text-zinc-500 dark:text-zinc-400 flex items-center gap-1.5">
          <i data-lucide="x-circle" class="w-3.5 h-3.5 text-zinc-400 dark:text-zinc-500"></i>NO en este milestone
        </h4>
        <ul class="mt-3 space-y-2 text-sm text-zinc-500 dark:text-zinc-400 list-none p-0">
          <!-- repetir -->
          <li class="flex items-start gap-2"><i data-lucide="minus" class="w-3.5 h-3.5 mt-0.5 shrink-0"></i><span>{{OUT_OF_SCOPE_ITEM}}</span></li>
        </ul>
      </div>
    </div>
    <div class="mt-5 rounded-md border-l-4 border-emerald-500 bg-emerald-50 dark:bg-emerald-950/30 p-4 text-sm text-emerald-900 dark:text-emerald-200">
      <p class="flex items-start gap-2"><i data-lucide="flag" class="w-4 h-4 mt-0.5 shrink-0"></i><span><span class="font-semibold">Done when:</span> {{DONE_WHEN}}</span></p>
    </div>
  </div>
</article>
```

### `{{RIESGO_ROWS}}`

Una fila por riesgo. Color del impacto: alto = rose, medio = amber, bajo = emerald.

```html
<tr>
  <td class="px-4 py-3 align-top text-xs font-mono text-zinc-500">R{{N}}</td>
  <td class="px-4 py-3 align-top text-zinc-700 dark:text-zinc-300">{{RIESGO}}</td>
  <td class="px-4 py-3 align-top"><span class="inline-flex px-2 py-0.5 rounded text-xs font-medium {{IMPACT_COLOR_CLASSES}}">{{IMPACT}}</span></td>
  <td class="px-4 py-3 align-top text-zinc-600 dark:text-zinc-400">{{MITIGACION}}</td>
</tr>
```

Para `{{IMPACT_COLOR_CLASSES}}`:
- alto → `bg-rose-100 dark:bg-rose-900/40 text-rose-700 dark:text-rose-300`
- medio → `bg-amber-100 dark:bg-amber-900/40 text-amber-700 dark:text-amber-300`
- bajo → `bg-emerald-100 dark:bg-emerald-900/40 text-emerald-700 dark:text-emerald-300`

### `{{SUPUESTO_ITEMS}}`

```html
<li class="flex items-start gap-2 text-sm text-zinc-700 dark:text-zinc-300">
  <i data-lucide="check-square" class="w-4 h-4 mt-0.5 shrink-0 text-zinc-400"></i>
  <span>{{SUPUESTO}}</span>
</li>
```

### `{{TIMESTAMP}}`

Fecha local en formato `YYYY-MM-DD`.

### `{{FOOTER_CREDITO}}`

El valor de `footer_credito` del bloque `[CUSTOMIZE]` del SKILL. Default: `"Generado con PRD Creator · gabrielneuman.com"`.

## Íconos Lucide — pista rápida

| Sección | Default | Alternativas |
|---|---|---|
| Hero | (sin ícono) | — |
| Features | `sparkles` | `zap`, `wand-2` |
| Starter | `package-check` | `box`, `archive` |
| Fuera de alcance | `minus-circle` | `slash` |
| Integraciones | `plug` | `cable`, `link` |
| Modelo de datos | `database` | `box` |
| Milestones | `route` | `flag`, `map` |
| Riesgos | `alert-triangle` | `shield-alert` |
| Supuestos | `check-square` | `clipboard-check` |
| Card individual feature | depende del feature | usa `lucide-icons-cheatsheet.md` |

### Sugerencias por tipo de feature

- Auth: `user`, `user-plus`, `shield`, `lock`, `log-in`
- Data/storage: `database`, `box`, `archive`, `folder`
- AI/automation: `wand-2`, `sparkles`, `bot`, `cpu`
- Comunicación: `mail`, `send`, `message-square`, `phone`
- Dinero/billing: `credit-card`, `dollar-sign`, `receipt`
- Búsqueda: `search`, `filter`
- Tiempo/calendario: `calendar`, `clock`
- Contenido: `file-text`, `image`, `video`, `mic`
- Compartir: `share-2`, `link`, `external-link`
- Acción: `play`, `pencil`, `eye`, `download`, `upload`

**Si dudas, usa `circle-dot`. NUNCA inventes nombres de íconos** — Lucide solo renderiza los que existen.

## Reglas finales del HTML

- **Prosa apretada.** Las cards pierden valor si están infladas. Una línea label + una oración descripción por feature card.
- **No agregues scope.** El HTML es presentación pura. Nunca inventes features, entidades o milestones para "llenar" un grid. Si la sección está corta, renderiza menos cards — espacio en blanco está OK.
- **Sin emoji.** Solo Lucide.
- **Sin IDs de sección.** Single-page, scroll-only — sin TOC, sin anchor links.
- **Omite secciones vacías.** Si no hay integraciones, borra todo el `<section>` de integraciones (no la dejes vacía).
- **El contenido es el mismo que el markdown.** Si se generan ambos, deben describir el MISMO scope locked. HTML es presentación distinta, no plan distinto.
