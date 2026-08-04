---
name: landing-visual-system
description: Use when styling a landing page or web UI — choosing colors, typography, spacing, components, or making a layout work on both desktop and mobile. Trigger on "diseño", "estilos", "responsive", "que se vea bien en celular", "paleta", "tipografía", "Tailwind", "CSS", or when writing any HTML/JSX that needs visual design decisions.
---

# Sistema visual y responsive

Stack por defecto para landings: **HTML estático + Tailwind (CDN o CLI)**. Es lo más rápido, lo más liviano en móvil y no requiere build. Solo sube a Astro (contenido/blog) o Next.js (formularios, auth, dashboard) si el proyecto lo pide.

## Regla base: mobile-first, siempre

Escribe los estilos para 375px primero. Los breakpoints solo AGREGAN.

```html
<!-- Bien -->
<div class="flex flex-col gap-4 p-4 md:flex-row md:gap-8 md:p-12">

<!-- Mal: desktop primero y luego deshacer -->
<div class="flex flex-row p-12 max-md:flex-col max-md:p-4">
```

Breakpoints útiles: `sm:640` `md:768` `lg:1024` `xl:1280`. No uses más de dos por componente.

## Tokens

Define los tokens una vez, arriba del archivo, y no uses valores sueltos después.

```html
<style>
  :root {
    --color-bg:      #0d0d0d;
    --color-surface: #1a1a1a;
    --color-text:    #f5f5f5;
    --color-muted:   #a3a3a3;
    --color-accent:  #e63946;  /* 1 solo color de acento */
    --radius:        12px;
    --shadow:        0 4px 24px rgb(0 0 0 / .25);
  }
</style>
```

**Paleta:** 1 neutro base + 1 acento + blanco/negro. El acento se reserva para CTAs y nada más. Si todo destaca, nada destaca.

**Contraste:** mínimo 4.5:1 texto sobre fondo. Verifica el acento sobre el fondo antes de usarlo en texto.

## Tipografía

- **Dos familias máximo.** Una para títulos, una para texto. O una sola con dos pesos.
- Fuentes: system stack (`font-sans` de Tailwind) es lo más rápido. Si usas Google Fonts, solo 2 pesos y `display=swap` + `preconnect`.
- **Escala fluida** (evita ajustar tamaños por breakpoint):

```css
h1 { font-size: clamp(2rem, 5vw + 1rem, 3.5rem); line-height: 1.1; }
h2 { font-size: clamp(1.5rem, 3vw + .5rem, 2.25rem); line-height: 1.2; }
p  { font-size: clamp(1rem, 1vw + .8rem, 1.125rem); line-height: 1.6; }
```

- Ancho de línea: `max-w-[65ch]` en párrafos. Nunca texto de borde a borde en desktop.
- Mínimo 16px en móvil (menos causa zoom automático en iOS).

## Espaciado

Escala de 4px: `4 8 12 16 24 32 48 64 96`. Nada intermedio.

- Padding de sección: `py-16 md:py-24`
- Contenedor: `mx-auto w-full max-w-6xl px-4 md:px-8`
- Gap entre elementos relacionados: `gap-4`; entre bloques distintos: `gap-12`

**Proximidad:** lo que va junto se acerca, lo que no se separa. Más espacio arriba de un título que abajo.

## Componentes

**Botón primario**
```html
<a href="#" class="inline-flex items-center justify-center gap-2 rounded-xl bg-[var(--color-accent)] px-6 py-3.5 text-base font-semibold text-white transition hover:brightness-110 active:scale-[.98] focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2">
  Pedir ahora
</a>
```

Reglas de touch: **mínimo 44×44px** de área táctil en cualquier elemento clickeable. Botones full-width en móvil (`w-full sm:w-auto`).

**Card**: `rounded-xl bg-[var(--color-surface)] p-6 ring-1 ring-white/10`. Sombra O borde, no ambos.

**Grid de 3**: `grid gap-6 sm:grid-cols-2 lg:grid-cols-3` — nunca 3 columnas en móvil.

## Imágenes

```html
<img src="images/smash-burger-doble.jpg" alt="Smash burger doble con queso cheddar"
     width="800" height="600" loading="lazy" decoding="async"
     class="h-full w-full rounded-xl object-cover">
```

- `width`/`height` SIEMPRE (evita layout shift → penaliza en Google).
- La imagen del hero: `loading="eager"` + `fetchpriority="high"`. Todas las demás `lazy`.
- `object-cover` + contenedor con `aspect-[4/3]` para que no se deformen entre tamaños.

## Movimiento

Solo transiciones de `opacity` y `transform`. Duración 150–300ms. Respeta:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; }
}
```

## Checklist responsive

- [ ] `<meta name="viewport" content="width=device-width, initial-scale=1">`
- [ ] Sin scroll horizontal a 320px (`overflow-x-hidden` es un parche, busca la causa)
- [ ] Botones ≥44px de alto, full-width en móvil
- [ ] Texto ≥16px en móvil
- [ ] Hero legible sin scroll en pantalla de 667px de alto
- [ ] Imágenes con `width`/`height` y `alt` descriptivo
- [ ] Probado en 375px, 768px y 1440px
- [ ] Áreas seguras iOS si hay barra fija: `pb-[env(safe-area-inset-bottom)]`
