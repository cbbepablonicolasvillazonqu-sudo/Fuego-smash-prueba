# Prompt para Claude Code — Landing Page Smash Burgers

Actuá como desarrollador front-end + copywriter especializado en landing pages de conversión para negocios de comida. Vas a construir una landing page completa para un negocio de smash burgers, usando las skills `landing-structure-copy`, `landing-visual-system` y `landing-cro-seo` que ya están cargadas en este proyecto.

## Contexto
- Proyecto vacío, con una carpeta `images/` que contiene fotos del producto (smash burgers).
- Stack: HTML + Tailwind estático (vía CDN), sin build. Es la opción más liviana para este caso y funciona bien tanto en compu como en celular.
- Si en algún punto el proyecto necesita rutas, blog, multi-idioma o algo que HTML estático no resuelve bien, avisame antes de migrar a Astro o Next.js — no lo decidas por tu cuenta.

## Orden de trabajo (aplicá las skills en este orden)

### 1. `landing-structure-copy`
- Definí el orden de secciones (hero, propuesta de valor, productos/menú destacado, prueba social, ubicación y horario, FAQ, CTA final, footer).
- Aplicá la jerarquía de mensaje: promesa principal en el H1, sub-promesa de apoyo, CTA primario y uno secundario.
- Usá las fórmulas de H1 / CTA / FAQ que trae la skill, adaptadas a smash burgers (sabor, ingredientes, rapidez, experiencia).
- Copy en español, tono cercano e informal.

### 2. `landing-visual-system`
- Diseño mobile-first.
- Usá los tokens de color y tipografía de la skill (o generá una paleta coherente con una marca de smash burgers).
- Tipografía fluida (clamp/rem), sin saltos bruscos entre mobile y desktop.
- Todos los targets táctiles (botones, links, CTAs) de mínimo 44x44px.
- Usá las fotos de `images/` con aspect-ratio fijo (width/height explícitos o `aspect-ratio` en CSS) para que no haya layout shift.

### 3. `landing-cro-seo`
- Meta tags completos (title, description, viewport, etc.).
- OG image y OG tags para que se vea bien al compartir en WhatsApp/redes.
- Schema.org apropiado (Restaurant / LocalBusiness / FAQPage según corresponda).
- Optimización de Core Web Vitals: lazy loading en imágenes fuera del viewport inicial, sin render-blocking innecesario.
- Accesibilidad: alt text en todas las imágenes, contraste adecuado, orden de foco lógico.
- Dejá preparados los puntos de tracking (clicks en CTA, WhatsApp, llamada) aunque todavía no se conecte ningún pixel.

## Restricciones
- Sin frameworks ni build step: HTML estático + Tailwind por CDN.
- El mínimo de archivos necesario (idealmente un solo `index.html`).
- No inventes datos del negocio (nombre, dirección, horario, redes, precios, WhatsApp) — si falta algo, preguntame antes de seguir.

## Primer paso
Antes de escribir código, mostrame el plan de secciones y el copy del hero (H1, sub-H1, CTA) para que lo revise.
