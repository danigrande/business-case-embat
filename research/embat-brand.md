# Embat — Branding y look & feel (embat.io)

> Fuente: análisis de la web pública de Embat (noviembre 2026). Usar para que
> los HTML generados (`/present`, `/demo`) parezcan producto oficial. La hoja de
> estilos vive en `templates/embat-theme.css` (se inlina en los HTML finales).

## Paleta

| Rol | Hex | Uso |
| --- | --- | --- |
| Navy (texto, hero, logo) | `#050B2C` | Texto principal, hero oscuro, fondo del logo |
| Navy profundo | `#080E2B` | Gradiente del hero |
| Fondo principal | `#FFFFFF` | Fondo de secciones |
| Fondo tarjeta | `#FBFBFC` | Tarjetas y contenedores |
| Fondo suave | `#F3F4F6` | Fondos secundarios, chips |
| Borde primario | `#E8E8ED` | Bordes finos de tarjetas |
| Borde secundario | `#D2D2DB` | Bordes más marcados |
| Texto secundario | `#6E707C` | Cuerpo de tarjetas |
| Texto terciario | `#42444C` | Texto de soporte |
| Azul de acción | `#3878F6` | Enlaces, estados activos, tabs |
| Púrpura (gradiente inicio) | `#C357EC` | Gradiente de marca |
| Púrpura medio | `#B565F3` | Gradiente de marca |
| Indigo (gradiente fin) | `#5C92FE` | Gradiente de marca |
| Éxito | `#08AB39` | Estados positivos |
| Warning | `#DFB631` | Avisos |
| Peligro | `#C2401F` | Rechazos, errores |

- **Gradiente de marca (firma):** `linear-gradient(275deg, #C357EC, #B565F3, #5C92FE)`.
- Variante vertical: `linear-gradient(180deg, #C357EC, #5C92FE)`.

## Tipografía

- Familia: **Haffer SQ XH** (Pangram Pangram). Pesos 400 y 500; el 600 reutiliza
  el 500.
- Assets: `https://www.embat.io/wp-content/themes/embat/assets/fonts/haffer-sqxh-400.woff2`
  y `haffer-sqxh-500.woff2` (embebidos en base64 dentro de
  `templates/embat-theme.css`; sin dependencias externas).
- Fallback: `-apple-system, 'Segoe UI', Arial, sans-serif`.

## Logo

- `https://www.embat.io/favicon.svg` (156×156, navy `#050B2C`, radio 40, tres
  trazos blancos). Se inlina en la topbar y la portada del deck.
- Wordmark: "embat" en minúscula; eslogan "Where Corporate Treasury meets
  Intelligence" (ES: "La inteligencia que impulsa tu tesorería").

## Estilo visual

- **Hero:** navy `#050B2C → #080E2B` con brillos radiales púrpura/indigo;
  secciones claras blanco/off-white.
- **Tarjetas:** radio 12px, borde 1px `#E8E8ED`, fondo `#FBFBFC`, sombras
  suaves (`0 1px 4px` y `0 8px 24px` con alpha ~0.06).
- **Botones:** pill o radio 8px; primario con gradiente de marca y texto
  blanco; secundario borde navy.
- **Chips/tags:** pills 999px, borde bajo contraste, fondo suave.
- **Mockups de producto:** ventanas blancas con barra superior gris `#F3F4F6`,
  tabs con subrayado azul, listados con bordes finos y estado seleccionado con
  borde izquierdo azul.

## Capturas de producto (SVG vectoriales, embat.io)

- Corporate Payments: `https://www.embat.io/wp-content/uploads/2025/11/Featured-card-05-EN.svg`
  (usada en el deck).
- Treasury: `.../Featured-card-01-EN.svg` · Risk: `.../Featured-card-02-EN.svg`
  · Reconciliation: `.../Featured-card-03-EN.svg`.
- Hero: `https://www.embat.io/wp-content/uploads/2026/01/home-hero-bg.webp`
  y vídeo `.../2026/02/Home-Hero-Video_EN-1.mp4`.

## Regla de uso en HTML generados

1. Copiar el contenido de `templates/embat-theme.css` dentro de `<style>`.
2. Todo en un solo archivo: sin `<link>`, sin `@import` y sin URLs remotas en
   el HTML final. Los assets (fuentes, SVG, capturas) se descargan ANTES
   desde sus URLs originales y se incrustan localmente (base64 o markup
   inline); las URLs de este documento son la fuente de descarga, no
   referencias del HTML final.
3. Componentes disponibles: `.eb-card`, `.eb-tag` (+ `.good/.bad/.warn/.blue/.brand`),
   `.eb-grid .g2/.g3/.g4`, `.eb-flow/.eb-step`, `.eb-alt/.eb-altrow`,
   `.eb-northstar`, `.eb-phases/.eb-phase`, `.eb-gatebar/.eb-pill`,
   `.eb-steps/.eb-stepx`, `.eb-chips`, `.mock` (bandeja de excepciones),
   `.slide.hero` (portada/cierre).
