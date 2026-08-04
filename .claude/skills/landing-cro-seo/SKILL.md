---
name: landing-cro-seo
description: Use when finishing, auditing, or optimizing a landing page — conversion rate optimization, page speed and Core Web Vitals, meta tags, Open Graph, schema.org structured data, accessibility, and event tracking. Trigger on "SEO", "que salga en Google", "optimizar", "velocidad", "meta tags", "conversión", "analytics", "accesibilidad", or before shipping any landing page.
---

# Conversión y SEO técnico

Se aplica DESPUÉS de que la estructura y el diseño estén listos. Auditar y corregir, no rediseñar.

## 1. Head mínimo obligatorio

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <title>Smash Burgers en Córdoba | Nombre — Pedí online</title>
  <meta name="description" content="Hamburguesas smash artesanales con carne molida del día. Delivery en 25 min en Córdoba capital. Pedí por WhatsApp.">
  <link rel="canonical" href="https://tudominio.com/">

  <!-- Open Graph: cómo se ve al compartir en WhatsApp/Instagram -->
  <meta property="og:type" content="website">
  <meta property="og:title" content="Smash Burgers en Córdoba">
  <meta property="og:description" content="Carne molida del día. Delivery en 25 min.">
  <meta property="og:image" content="https://tudominio.com/images/og.jpg">
  <meta property="og:url" content="https://tudominio.com/">
  <meta name="twitter:card" content="summary_large_image">

  <link rel="icon" href="/favicon.ico" sizes="any">
</head>
```

Reglas:
- `title`: 50–60 caracteres. Palabra clave + marca + beneficio.
- `description`: 140–160 caracteres. No posiciona, pero define el click.
- `og:image`: 1200×630px. Sin esto, el link compartido en WhatsApp se ve vacío — es la causa #1 de tráfico social perdido.
- `lang="es"` correcto. Nunca dejar `lang="en"` por defecto.

## 2. Datos estructurados (schema.org)

Elige el tipo correcto y ponlo en JSON-LD antes de `</body>`:

- Negocio físico → `LocalBusiness` (o `Restaurant`, `Store`, `HealthAndBeautyBusiness`)
- Servicio/SaaS → `Organization` + `Service`
- Producto → `Product` con `offers`
- Siempre que haya FAQ visible → `FAQPage`

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Restaurant",
  "name": "Nombre",
  "image": "https://tudominio.com/images/hero.jpg",
  "telephone": "+54 351 000 0000",
  "priceRange": "$$",
  "address": {"@type": "PostalAddress","streetAddress":"Calle 123","addressLocality":"Córdoba","addressCountry":"AR"},
  "openingHoursSpecification": [{"@type":"OpeningHoursSpecification","dayOfWeek":["Wednesday","Thursday","Friday","Saturday","Sunday"],"opens":"19:00","closes":"00:00"}],
  "servesCuisine": "Hamburguesas",
  "url": "https://tudominio.com/"
}
</script>
```

Validar en https://search.google.com/test/rich-results antes de publicar.

## 3. Velocidad / Core Web Vitals

Objetivos: **LCP < 2.5s · INP < 200ms · CLS < 0.1**

| Problema | Solución |
|---|---|
| LCP alto | Imagen del hero con `fetchpriority="high"`, `loading="eager"`, comprimida <200KB, en WebP |
| CLS | `width`/`height` en toda `<img>`; reservar altura para banners y embeds |
| JS pesado | Sin frameworks para una landing estática. Nada de jQuery. Vanilla JS o nada |
| Fuentes | `preconnect` a fonts.gstatic.com + `display=swap`; o system fonts (0 requests) |
| Tailwind CDN | Sirve para prototipo. Para producción, compilar con CLI (pasa de ~3MB a ~10KB) |

Conversión de imágenes:
```bash
# WebP con buena calidad, típicamente 60-80% menos peso
cwebp -q 80 images/hero.jpg -o images/hero.webp
```

Auditar: Chrome DevTools → Lighthouse → modo móvil. Meta: ≥90 en Performance y ≥95 en Accessibility.

## 4. CRO — puntos de fricción a revisar

- **Velocidad de acción:** ¿cuántos clicks hasta convertir? Objetivo: 1. Un link `wa.me` con mensaje pre-escrito convierte más que un formulario.
  ```html
  <a href="https://wa.me/5493510000000?text=Hola!%20Quiero%20hacer%20un%20pedido">Pedir por WhatsApp</a>
  ```
- **Formularios:** solo los campos que realmente usarás. Cada campo extra baja la conversión. Usa `type="tel"`, `type="email"`, `autocomplete` correcto (teclado adecuado en móvil).
- **CTA fijo en móvil:** barra inferior con el CTA principal, visible siempre.
- **Precio visible.** Ocultarlo genera abandono, no consultas.
- **Reducir riesgo** cerca del botón: "Sin tarjeta", "Cancelá cuando quieras", "Respuesta en 5 min".
- **Sin distracciones:** en una landing, cero links externos salvo el CTA y el footer.
- **Carga sobre la línea de flotación:** el CTA principal debe verse sin scroll en móvil.

## 5. Accesibilidad (y también es SEO)

- Un solo `<h1>` por página; jerarquía sin saltos (h1 → h2 → h3).
- `alt` descriptivo en imágenes con contenido; `alt=""` en decorativas.
- Landmarks: `<header> <nav> <main> <section> <footer>`.
- Foco visible en todo elemento interactivo (`focus-visible:outline-2`).
- Los botones que hacen algo son `<button>`; los que navegan son `<a>`.
- Contraste ≥4.5:1. Verificar el acento sobre fondo oscuro.
- Navegable solo con teclado (Tab) de principio a fin.

## 6. Tracking

Instrumenta los eventos que importan, no pageviews:

```html
<a href="https://wa.me/..." data-evt="cta_whatsapp">Pedir</a>
<script>
document.querySelectorAll('[data-evt]').forEach(el =>
  el.addEventListener('click', () => window.gtag?.('event', el.dataset.evt))
);
</script>
```

Eventos mínimos: click en CTA principal, click en teléfono/WhatsApp, envío de formulario, scroll al 75%.

## Checklist antes de publicar

- [ ] `title`, `description`, `canonical`, `og:image` completos
- [ ] JSON-LD válido en Rich Results Test
- [ ] Lighthouse móvil ≥90 performance, ≥95 accesibilidad
- [ ] Imágenes en WebP, hero <200KB
- [ ] Un solo `<h1>`, jerarquía correcta
- [ ] CTA visible sin scroll en móvil + barra fija
- [ ] Links `tel:` y `wa.me` funcionando
- [ ] `robots.txt` y `sitemap.xml` presentes
- [ ] HTTPS y dominio sin `www` duplicado
- [ ] Probado el link compartido en WhatsApp (preview correcto)
