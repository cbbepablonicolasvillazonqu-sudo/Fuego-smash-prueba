---
name: landing-structure-copy
description: Use when building, restructuring, or writing the content of a landing page. Defines section order, message hierarchy, headline/CTA formulas, and conversion-oriented copy. Trigger on "landing page", "página de aterrizaje", "hero", "sección de beneficios", "CTA", "copy de la landing", or when creating a single-page marketing site.
---

# Landing page: estructura y copy

Objetivo: una landing tiene UNA meta. Antes de escribir código, define:

1. **Acción única** (pedir, reservar, comprar, agendar, dejar email)
2. **Audiencia** (quién llega y desde dónde: Instagram, Google, QR físico)
3. **Objeción principal** que impide la conversión

Si el usuario no lo dio, pregúntalo antes de generar el HTML.

## Orden de secciones (mobile-first)

Escribe las secciones en este orden. Solo omite una si hay razón explícita.

| # | Sección | Función | Regla |
|---|---------|---------|-------|
| 1 | Header | Logo + 1 CTA | Sticky, máximo 4 links. En móvil: logo + botón, sin menú hamburguesa si hay ≤4 links |
| 2 | Hero | Promesa + acción | Debe verse completo en 100svh móvil. H1 + subtítulo + CTA + imagen real |
| 3 | Prueba social rápida | Bajar la guardia | Franja fina: reseñas, "+X clientes", logos, estrellas |
| 4 | Beneficios | Qué gana el usuario | 3 bloques. Beneficio como título, característica como apoyo |
| 5 | Producto / oferta | Qué es exactamente | Fotos reales, precios visibles, sin PDF ni carrusel obligatorio |
| 6 | Cómo funciona | Reducir fricción | 3 pasos numerados, verbos en imperativo |
| 7 | Testimonios | Confianza específica | Nombre + foto + resultado concreto. Sin testimonios genéricos |
| 8 | FAQ | Matar objeciones | 4–6 preguntas. Cada una responde una objeción real de venta |
| 9 | CTA final | Cerrar | Repite la promesa + botón + refuerzo de riesgo cero |
| 10 | Footer | Confianza legal | Dirección, teléfono clickeable, horarios, redes, links legales |

**Regla del CTA:** el mismo CTA aparece al menos 3 veces (hero, mitad, final). En móvil, además, barra fija inferior con el CTA principal.

## Fórmulas de copy

### H1 del hero
Elige una y adáptala. Máximo 10 palabras.

- **Resultado + tiempo:** "Tu hamburguesa artesanal en 25 minutos"
- **Para quién + qué:** "Smash burgers de verdad, para los que saben"
- **Contra la alternativa:** "La hamburguesa que no se parece a la del delivery"

Prohibido: "Bienvenidos a", "Somos una empresa dedicada a", "Calidad y servicio".

### Subtítulo
Una frase. Responde: qué es, para quién, por qué creerte.

### Botones
Verbo en primera persona o imperativo + resultado. Nunca "Enviar", "Click aquí", "Más info".
- Bien: "Pedir ahora por WhatsApp", "Ver el menú", "Reservar mi mesa"

### Beneficios
Formato `Beneficio (título corto) → cómo lo logras (1 línea)`.
- Mal: "Carne 100% vacuna" → Bien: "Sabor que se nota" / *Carne 100% vacuna molida cada mañana*

### Testimonios
Estructura: problema previo → qué cambió → resultado concreto. Con nombre real y ciudad.

### FAQ
Cada pregunta debe ser una objeción de compra, no información de relleno.
Sirve: precio, tiempo de entrega, zona de cobertura, formas de pago, devoluciones, alergias.

## Jerarquía de mensaje

Un visitante debe entender en 5 segundos, solo con lo visible sin scroll:
1. **Qué es** esto
2. **Para quién**
3. **Qué hago ahora**

Después de escribir el hero, valida los 3 puntos. Si alguno falla, reescribe antes de seguir.

## Checklist antes de entregar

- [ ] Un solo objetivo de conversión en toda la página
- [ ] El H1 no menciona el nombre de la empresa como protagonista
- [ ] Cada sección tiene un propósito distinto (sin repetir contenido)
- [ ] Cero lorem ipsum, cero imágenes de stock genéricas
- [ ] Teléfono, WhatsApp y dirección son clickeables (`tel:`, `https://wa.me/`, `maps`)
- [ ] La página se entiende leyendo solo los títulos
- [ ] Longitud total: 5–9 secciones. Más que eso, sobra
