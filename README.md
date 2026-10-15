# BrandBhai — Website v2

Static, dependency-light site. Open `index.html` or serve the folder with any static host (Netlify, Vercel, Cloudflare Pages, cPanel).

```
index.html  about.html  services.html  gallery.html  contact.html
assets/css/style.css   → the whole design system (tokens, components, pages)
assets/js/main.js      → all interactions; each module no-ops when its markup is absent
assets/js/scenes.js    → WebGL scenes (Three.js, lazy-loaded on Home, Services, Contact)
assets/img/            → logo marks (transparent, light + dark), favicon, OG image
```

**External:** Google Fonts (Bricolage Grotesque, Geist, Geist Mono, Instrument Serif), Lenis smooth scroll and Three.js r186 (jsDelivr), Unsplash imagery (same photos as v1).

## Before going live
1. **Form + newsletter backend.** In `assets/js/main.js` set `CONFIG.FORM_ENDPOINT` / `CONFIG.NEWSLETTER_ENDPOINT` (e.g. a Formspree URL). Empty = demo mode (success screen only). If the endpoint errors, the form falls back to opening a pre-filled email to hello@brandbhai.in.
2. **WhatsApp number.** `contact.html` links to `https://wa.me/` — add the number, e.g. `https://wa.me/919876543210`.
3. **Social links.** The footer points to instagram.com / linkedin.com — replace with your profile URLs.
4. **Imagery.** Swap Unsplash placeholders for your own work when ready (keep the `?w=` sizes).
5. **Domain.** Canonical URLs assume `https://brandbhai.in/`.

## Behaviour notes
- Theme: follows the OS, remembers the choice (`localStorage: brandbhai_theme`), no flash on load.
- Preloader shows once per browser session.
- `prefers-reduced-motion` disables smooth scroll, reveals and marquees.
- If JS fails to load, all content is still visible (3.5 s failsafe in `<head>`).
- Services → “Deploy …” buttons and the estimator pass `?service=ai,ads,…` to Contact, which pre-selects those disciplines.

## Signature concept — “Brand as Matter” (home)
- **Opening:** ~15,000 particles fly in and assemble the BrandBhai “B” (sampled from `assets/img/mark-dark.png`); the cursor pushes them like a force field.
- **Five Forces:** a pinned scroll chapter where the same matter morphs into a neural sphere (AI), growth bars + arrow (Ads), a lens (Cinema), stacked browser windows (Web) and a cut gem (Brand). Desktop uses a three-column layout — a rolling gold numeral with a vertical chapter list and progress line on the left, the chapter text (same height for every chapter, so nothing jumps) in the middle, and the shape on the right. On phones the shape floats above and the text sits just above a horizontal chapter bar.
- **Liquid type:** hero letters breathe on a wave and swell toward the cursor (variable `wght`/`wdth` axes).
- **Filmstrip:** Selected Work pins and scrolls sideways with 3D curvature and speed-based lean.
- **Deck:** testimonials are a card deck you drag and throw (arrows + keyboard too).
- **Curtain:** internal links sweep a gold liquid-edge curtain with the B mark between pages.

To change the logo the particles build, replace `mark-dark.png` (transparent PNG; yellow pixels become gold particles).
When you update CSS/JS, bump `?v=` on the asset URLs so returning visitors get the new files.

## Logo transition intro (first visit per browser session)
1. On black, “Beauty shapes every message” slides across with a glowing gold orb in a gap at the centre; a counter runs 000→100.
2. Molten gold pours down with drips and floods the screen.
3. The gold drains away (drips trailing upward) to reveal the BrandBhai **B** as a 3D chrome object — pearl-chrome body, gold-chrome accents, ~10 layers of metal thickness — spinning open from edge-on, with a light sweep, over a flowing outlined “Brandbhai” script.
4. The logo shrinks and flies into the header logo, the site appears and the particle B assembles.

**Skip intro** (top right) or **Esc** ends it instantly; it never shows twice in one session and is skipped entirely for reduced-motion visitors. The header logo also turns in 3D as you scroll. Masks: `assets/img/mark-mask*.png`.

## Editorial motion layer (every page)
- **Blueprint grid:** faint architectural column lines run behind the whole site and draw themselves in on load.
- **Drawn rules:** a gold-to-grey hairline draws across above each section heading as it scrolls into view; some labels carry a ruled meta tag (e.g. “How we operate —— 04 principles”).
- **Dot + ring cursor** (desktop): a precise gold dot with a trailing ring that fills over links and reads “DRAG” on draggable areas.
- **Molten-gold page transition:** gold pours down with dripping edges between pages, then drains away with trailing drips.
- **Manifesto bar:** *Beauty + Intelligence + Revenue* sits along the bottom of the screen, crosses spinning with scroll (hidden over the hero, pinned chapters and finale, and on phones).
- **Filmstrip cards:** large italic serif numerals, and captions whose words blur-stagger in on hover.
- **Gallery — Wander the archive:** an infinite field of projects you can drag in any direction (it also drifts on its own); tiles tilt in 3D around the centre, and clicking opens the project.

Note for hosting: set HTML files to `Cache-Control: no-cache` (CSS/JS/images are already versioned with `?v=`) so returning visitors always get new page markup.

## Advanced layer
- **Capabilities index (Services):** giant discipline rows; hovering one sweeps it gold, dims the rest, and floats a preview image that follows and tilts with the cursor. Rows jump to each discipline.
- **Image curtain reveals:** photos unveil behind a rising edge and settle from a slight zoom as they enter.
- **Decode labels:** eyebrow labels and small tags scramble through random glyphs and resolve into the real words.
- **Letter-roll links:** header and footer links roll their letters upward one by one on hover.
- **Kinetic footer:** an outlined “Let’s build something unforgettable ✦” marquee tops every footer, leans with scroll speed and fills gold on hover (links to Contact).
- **Magnetic headlines:** section titles drift slightly toward the cursor.

## Finale (every page)
The page ends with the official BrandBhai logo (B mark + serif “Brandbhai” name) rising into place: it lifts, un-tilts and scales in as you reach the bottom, while gold light rays, a halo and a floor glow come up behind it, the wordmark fills with gold, and a signature line draws across. Once it arrives it floats gently, a light sweep passes across it (clipped to the image's own shape), and it tilts toward the cursor.

**Logo files:** `assets/img/logo-full-light.webp/.png` is the official logo made transparent for dark backgrounds (black → warm white, gold kept, arrow see-through); `logo-full-dark.webp/.png` is the original colours for light backgrounds. To swap, replace the light files, keep the `width`/`height` and `.finale__stage` `aspect-ratio` in step, and bump `?v=`.

## 3D & motion layer
| Where | What | Tech |
|---|---|---|
| Home | Particle “B” → five discipline forms (see above) | WebGL shader |
| Services hero | 5 discipline shapes with studio reflections; hover to highlight, click to jump | Three.js PBR |
| Contact hero | Dotted globe with Delhi / Mumbai / Dubai markers and live arcs; drag to spin | WebGL |
| About | 3D logo coin that spins with scroll and tilts under the cursor | CSS 3D |
| Gallery | Infinite drag field of all projects with 3D lens tilt; drag / arrow keys, click opens the lightbox | CSS 3D |
| Everywhere | Tilt + glare cards, image parallax, 3D scroll entrances, cursor ring, page cross-fades | CSS + vanilla JS |

Performance guards: scenes load only when near the viewport, pause off-screen and in background tabs, cap pixel ratio, and use lighter geometry on phones. No WebGL → CSS fallback; reduced motion → a single still frame, no tilt/parallax/cursor. Page transitions use the gold curtain (skipped for reduced motion and for new-tab/modifier clicks).
