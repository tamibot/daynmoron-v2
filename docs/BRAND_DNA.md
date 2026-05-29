# Brand DNA — Dylan Moron (daynmoron.com)

> **Este archivo es la fuente de verdad del diseño.**
> Antes de agregar, modificar o crear cualquier componente, consultar aquí.
> El objetivo es que todo lo nuevo se "sienta igual" al original.

---

## 1. Identidad & Personalidad

| Atributo | Valor |
|----------|-------|
| **Persona** | Director, DOP y Editor cinematográfico |
| **Origen** | Francia. Basado en Frankfurt |
| **Estilo** | Luxury editorial — cinematográfico, oscuro, sofisticado, europeo |
| **Propósito del sitio** | Portfolio visual de alto impacto — que las imágenes hablen |
| **Sensación buscada** | Como abrir un book de lujo: máximo visual, mínimo ruido de UI |

**Palabras clave del brand:** `bold` · `cinematic` · `dark` · `editorial` · `minimal` · `high-contrast`

---

## 2. Paleta de Colores

### Colores base (CSS Custom Properties)

```css
:root {
  --white-hsl:        0, 0%, 100%;       /* #ffffff */
  --lightAccent-hsl:  0, 0%, 89.02%;    /* #e3e3e3 */
  --accent-hsl:       0, 0%, 9.02%;     /* #171717 */
  --darkAccent-hsl:   240, 2.61%, 22.55%; /* #38383f */
  --black-hsl:        0, 0%, 0%;         /* #000000 */
}
```

### Colores con nombre y uso

| Token | Hex | HSL | Uso |
|-------|-----|-----|-----|
| White | `#ffffff` | `hsl(0,0%,100%)` | Fondos claros, texto sobre oscuro |
| Light Accent | `#e3e3e3` | `hsl(0,0%,89%)` | Fondos de secciones secundarias, muted |
| Accent (near-black) | `#171717` | `hsl(0,0%,9%)` | Color primario de marca, fondos oscuros |
| Dark Accent | `#38383f` | `hsl(240,2.6%,22.5%)` | Gris oscuro con tono azul sutil, overlays |
| Black | `#000000` | `hsl(0,0%,0%)` | Texto principal, bordes, íconos |
| **Deep Navy** ⭐ | `#030f18` | `hsl(201.6,80.65%,6.08%)` | Borde del header, color del site title |
| **Golden Amber** ⭐ | `#f5c842` | `hsl(40.13,96.32%,68.04%)` | Botón terciario, announcement bar — único acento cálido |

### Regla de color
- El sitio es **casi monocromático**: blanco, negro, grises.
- El **Golden Amber** (`#f5c842`) es el único acento de color — se usa con mucha moderación.
- El **Deep Navy** (`#030f18`) aparece solo en bordes del header y título del sitio.
- Overlays de portfolio: `hsla(var(--darkAccent-hsl), 0.68)` — muy sutil, casi transparente.
- **No inventar nuevos colores.** Si se necesita otro tono, usar variaciones de opacidad de los existentes.

---

## 3. Tipografía

### Familias

| Rol | Familia | Fuente | Fallbacks |
|-----|---------|--------|-----------|
| **Display / Heading** | `Clarkson` | Adobe TypeKit | `Helvetica Neue`, Helvetica, Arial, sans-serif |
| **Body** | `Helvetica Neue` | Sistema | Helvetica, Arial, sans-serif |
| **Icons (social)** | `social-icon-font` | Squarespace | — |

> **Clarkson** es la fuente de carácter del brand — serif editorial con personalidad cinematográfica. Es fundamental mantenerla en todos los headings.

### Escala tipográfica

```
Viewport-relative (grandes títulos):
  8.5vmin  — Heading XL (portada, hero sections)
  6.6vmin  — Heading L
  6.0vmin  — Heading M (secciones principales)

Pixel-fixed:
  68px  — Extra display
  35px  — H1 grande
  32px  — H1
  30px  — H2
  28px  — H2 secundario
  26px  — H3
  24px  — H3 secundario
  22px  — H4
  21px  — H4 secundario
  18px  — H5 / label grande
  16px  — Body base / H6
  14px  — Body secondary
  13px  — Caption / meta
  12px  — Small
  11px  — XS / legal
  10px  — XXS
   9px  — Micro

rem-based (componentes):
  1.6rem — List item title
  1.5rem — List item description
  1.0rem — Button
  0.875rem — Body small
  0.75rem  — Caption small
```

### Pesos
- `100` / `200` — Display, headings grandes (muy ligeros, elegantes)
- `400` — Body, nav items
- `700` — Énfasis, CTA buttons (sparingly)

### Letter-spacing
- Headings display: negativo o `0` — condensado, editorial
- Nav items: `0` — sin tracking adicional
- Botones/labels: leve positive tracking cuando en caps

### Reglas tipográficas
- Los headings grandes van en **Clarkson** siempre — nunca reemplazar por Helvetica
- El body es limpio: `Helvetica Neue` sin adornos
- `text-transform: uppercase` se usa en nav items y labels pequeños
- Nada de mixed fonts raras — el contrast tipográfico lo da Clarkson vs Helvetica

---

## 4. Espaciado & Layout

### Grid system

```
Max site width:    1500px
Desktop gutter:    4vw
Mobile gutter:     6vw
Grid gap:          11px (columnas y filas)
Breakpoint:        768px
Desktop columns:   24 (fluid engine)
Mobile columns:    8  (fluid engine)
```

### Row height
```css
--row-height-scaling-factor: 0.0215;
--container-width: min(1500px, calc(100vw - 4vw * 2));
row-height: calc(container-width * 0.0215)  /* ≈ 30px en 1400px */
```

### Padding de secciones
```
Sections full-bleed:  padding: 6% 6% 6% 6%
Gap entre elementos:  11px (tight) / 20px (looser)
Padding inicial:      0vw en sección hero
```

### Reglas de layout
- El sitio respira: **mucho espacio en blanco**. No saturar.
- Las imágenes son protagonistas — los márgenes las sirven, no compiten.
- El fluid-engine grid es de 24 columnas en desktop — usar siempre columnas pares.

---

## 5. Navegación

### Estructura
```
Desktop nav:  Home · Work · Showreel · Photography · Shop · Contact
```

### Comportamiento del header
```
Estilo:         Dynamic (transparente al inicio, sólido al hacer scroll)
Layout desktop: navcenter (nav centrada)
Layout mobile:  logoleftnavright (logo izq, hamburger der)

Scroll-transparent:
  Background: transparent
  Nav color:  white (sobre fondo oscuro del hero)

Scroll-solid:
  Background: white (#ffffff)
  Nav color:  black (#000000)
  Border:     hsla(201.6, 80.65%, 6.08%, 1) → #030f18
```

### Hamburger (mobile)
```
Estilo:  triplelinehamburger (3 líneas horizontales)
Grosor:  3px por línea
```

### Overlay de menú (mobile)
```
Fondo:      Negro (#000000)
Animación:  Fade
Link color: var(--accent) = #171717 sobre negro → usar blanco
Font size:  Links grandes, tipo display
```

### Animaciones de nav
- Los items de nav tienen `data-animation-role="header-element"` → entrance animation al cargar
- Los links del header overlay usan la misma jerarquía visual que el content

---

## 6. Portfolio Grid

### Comportamiento
- Grid de imágenes/GIFs en formato fluid (se adapta al viewport)
- Los GIFs **autoplay en loop** — dan sensación de movimiento constante
- Hover: overlay oscuro con título del proyecto (`--darkAccent` a ~68% opacidad)
- Overlay title: **blanco**, fuente **Clarkson**, centrado

### Aspect ratios
- Los items del portfolio usan aspect ratios variables según el contenido
- No hay grid rígida de thumbnails — es un collage fluido con jerarquía visual

### Estilo de imágenes
```css
/* Logo del sitio — invierte color según contexto */
.header-title-logo img {
  filter: invert(100%);
}

/* Overlay portfolio */
--portfolio-grid-overlay-title-color: hsla(var(--white-hsl), 1);
--portfolio-grid-basic-title-color: hsla(var(--darkAccent-hsl), 0.68);
```

---

## 7. Animaciones & Motion

### Principios
- Las animaciones son **sutiles y cinematográficas** — no playful, no bouncy
- Los easing son suaves: nada de `bounce` o `elastic`
- `cubic-bezier` preferido sobre `ease-in-out` estándar

### Animaciones clave identificadas

```css
/* Clip reveal — usado en secciones de imagen */
@keyframes clipAnimation {
  0%   { clip-path: polygon(0 0, 10% 0, 0 100%, 0 100%); }
  100% { clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%); }
}

/* Form field highlight trace */
@keyframes animation-form-field-fx-highlight-trace {
  /* Trace suave alrededor del campo */
}
```

### Efectos de imagen disponibles (Squarespace imageFluid)
- `parallax` — scroll parallax
- `film-grain` — ruido de película ⭐ (muy on-brand)
- `liquid` — efecto líquido
- `refracted-circles` — círculos refractados
- `refracted-lines` — líneas refractadas

### Motion guidelines para v2
- Entrada de secciones: **fade + slight translate Y** (hacia arriba), duración 0.6-0.8s
- Hover en imágenes: **overlay fade** 0.3s ease
- Transición de página: **fade** 0.4s
- Parallax: sutil, máx 20% de desplazamiento
- No usar `scale` en hover de imágenes — el sitio no tiene eso

---

## 8. Componentes UI Clave

### Botones
```
Primario:    fondo negro (#000000), texto blanco, sin border-radius prominente
Terciario:   fondo Golden Amber (#f5c842), texto negro
Ghost/Outline: border negro, fondo transparente
Font-size botón: 1rem
```

### Logo / Site Title
```
Texto:   "Dylan Moron" (sitio oficial) → adaptable al proyecto
Color:   Deep navy #030f18 en modo claro, blanco en modo oscuro
Filter:  invert(100%) para la imagen del logo según contexto
```

### Social links (footer/header)
```
Shape:   "none" (sin borde)
Style:   "outline"
Thickness: 1px
```

### Announcement bar
```
Fondo:  Golden Amber #f5c842
Texto:  Negro
```

---

## 9. Voz & Contenido

- Copy en **inglés** (sitio bilingüe, francés/inglés)
- Títulos cortos, impactantes — el visual hace el trabajo pesado
- Descripción profesional: *"France-born Director, DOP and Editor specializing in high-energy commercials, brand content and short documentaries. Over 8 years of experience working with global brands like Puma, Adidas, Salomon. Based in Frankfurt, available worldwide."*
- Sección de contacto: `#àpropos` (anchor link)

---

## 10. Checklist antes de tocar cualquier cosa

- [ ] ¿El color nuevo está en la paleta de este doc?
- [ ] ¿La fuente es Clarkson (headings) o Helvetica Neue (body)?
- [ ] ¿El espaciado respeta el grid de 11px gap / 4vw gutter?
- [ ] ¿La animación es sutil y cinematográfica (no bouncy)?
- [ ] ¿El componente se siente como parte de un portfolio de lujo?
- [ ] ¿Hay demasiado texto? Reducir — las imágenes hablan.
- [ ] ¿El contraste blanco/negro es suficiente? El sitio vive del contraste.

---

*Extraído el 2026-05-29 directamente del CSS fuente de daynmoron.com*
*Archivos analizados: `site_nocustom=true.css` (CSS vars), `static.css` (framework), `index.html` (105 style blocks inline)*
