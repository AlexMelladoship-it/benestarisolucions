# Benestari Solucions — Estat del projecte

## On ens vam quedar

**La web v2 està desplegada a GitHub + Netlify (push fet el 17/06/2026).**
Commit actual: `2ad5ca7` — "feat: afegir pàgines legals i actualitzar links footer"

Repo: `https://github.com/AlexMelladoship-it/benestarisolucions.git` (branch: `main`)

---

## Com fer el proper push

El repo ja té git inicialitzat, remote configurat i commits. Simplement:
```bash
git add .
git commit -m "descripció del canvi"
git push origin main
```
Netlify es redesplega automàticament en fer push.

---

## Estructura de fitxers (42 HTML)

| Fitxer | Descripció |
|--------|-----------|
| `Benestari Solucions.html` | **Pàgina principal v2** — hero, categories, qui som, serveis, blog, contacte, footer |
| `Descans.html` | Categoria descans (12 productes) |
| `Terapia.html` | Categoria teràpia (5 productes) |
| `Aigua-Aire.html` | Categoria aigua i tractament (11 productes) |
| `Llar.html` | Categoria llar (2 productes) |
| `producto-*.html` | 33 pàgines de producte individuals |
| `blog-qualitat-son.html` | Blog: qualitat del son |
| `blog-aigua-purificada.html` | Blog: aigua purificada |
| `blog-terapies-naturals.html` | Blog: teràpies naturals |
| `politica-privacitat.html` | **NOU** Política de privacitat (bilingüe CA/ES, RGPD) |
| `politica-cookies.html` | **NOU** Política de cookies (bilingüe CA/ES) |
| `index.html` | Redirect a `Benestari Solucions.html` |
| `design_v2_reference.html` | Referència del disseny v2 (NO és producció) |

---

## Carpetes d'imatges

```
IMAGENES WEB baners principales/   ← Imatges principals de la homepage
  cat-DESCANS.jpg                   ← Banner categoria Descans
  cat- TERAPIA FINAL.jpg            ← Banner categoria Teràpia
  cat-AIGUA.jpg                     ← Banner categoria Aigua
  cat- LLAR FINAL.jpg               ← Banner categoria Llar
  IMG_DESCASO BLOG.png              ← Imatge blog Descans
  IMG_AGUA BLOG.png                 ← Imatge blog Aigua
  IMG_TERAPIA BLOG.png              ← Imatge blog Teràpia
  IMG_sobre nosotros.jpg            ← Imatge secció "Qui som"
  IMG_HERO.png                      ← Hero principal (duplicat a uploads/)

uploads/
  logo_benestarisolucions.png       ← Logo oficial
  IMG_HERO.png                      ← Foto hero principal (Ken Burns)
  pasted-1781019749924-0.png        ← Foto antiga (ja no s'usa)

IMG_DESCANSO/                       ← Fotos productes Descans
IMG_TERAPIA/                        ← Fotos productes Teràpia
IMG_AGUA Y AIRE/                    ← Fotos productes Aigua
IMG_HOGAR/                          ← Fotos productes Llar
```

---

## Disseny v2 — Pàgina principal

### Tokens CSS
```css
--green:       oklch(0.62 0.22 136)   /* verd marca */
--green-mid:   oklch(0.50 0.20 136)   /* hover */
--green-dark:  oklch(0.32 0.14 136)   /* footer + serveis */
--green-light: oklch(0.95 0.05 136)   /* fons suau */
--green-pale:  oklch(0.98 0.02 136)   /* fons molt suau */
--white:       #FAFAF8
--text:        oklch(0.16 0.02 136)
--text-mid:    oklch(0.35 0.03 136)
--muted:       oklch(0.55 0.03 136)
--border:      oklch(0.89 0.025 136)
```
Fonts: **DM Sans** (cos) + **DM Serif Display** (títols) — Google Fonts.

### Seccions homepage
1. **Nav** — sticky, fons semitransparent amb blur. Dropdown desktop de Productes. Hamburger mòbil.
2. **Hero** — foto Ken Burns (`uploads/IMG_HERO.png`), overlay fosc, badge animat, h1 serif, botons CTA, stats animats (500+, 10+, 100%, 33).
3. **Marquee** — franja animada entre hero i categories.
4. **Categories** — grid 2×2, imatges de `IMAGENES WEB baners principales/`, número badge, fletxa rotativa al hover.
5. **Qui som** — layout 2 columnes (imatge + text). Imatge: `IMG_sobre nosotros.jpg`, `object-position: 65% 68%`. Targeta flotant "10+ anys".
6. **Serveis** — fons `--green-dark`, llista numerada (01–04).
7. **Blog** — 3 targetes, imatges de `IMAGENES WEB baners principales/`, links a blogs reals.
8. **Contacte** — email: `benestarisolucions@gmail.com` / tel: `+34 623 412 836`.
9. **Footer** — fons `--green-dark`, 4 columnes (Empresa, Productes, Legal). Links legals apunten a les pàgines reals.

### Sistema bilingüe (CA/ES)
- `localStorage` key: `bs-lang`
- Català: `<span class="lca">text</span>`
- Castellà: `<span class="les">text</span>`
- CSS: `html[lang="ca"] .les { display: none }` i viceversa
- **IMPORTANT:** Mai afegir `style="display:none"` a elements `.les` — l'inline style sobreescriu el CSS i trenca el canvi d'idioma.

---

## Canvis aplicats a totes les pàgines

Tots els fitxers `.html` (excepte `Benestari Solucions.html`) tenen:
- **Dropdown nav desktop** per a Productes (CSS + HTML) amb les 4 categories
- **`@media (min-width: 769px) { .nav-mobile-btn { display: none !important; } }`**
- **Mobile compact fix** — CSS al principi del primer bloc `@media (max-width: 768px)`:
  - `html, body { overflow-x: hidden; }` + `word-break: break-word`
  - `img, video, iframe { max-width: 100%; height: auto; }`
  - `.footer-grid { grid-template-columns: 1fr !important; }`
  - `.prod-trust { flex-direction: column !important; }`
  - Font sizes reduïts amb `clamp()` per a `.prod-info-name` i `.prod-price`
- **Gallery fix** (33 pàgines de producte):
  - `.gallery-thumbs { width: 100% !important; overflow-x: auto; }` — scroll horitzontal
  - `.gallery { overflow: hidden; }` — conté el scroll sense propagar-lo a la pàgina
- **Logo nav visible** — eliminat `.nav-logo-text { display: none; }` de categories, productes i blogs
- **Footer links legals** — tots apunten a `politica-privacitat.html` i `politica-cookies.html`
- **Related products** — productes eliminats substituïts per existents

### Dos formats de footer (important!)
- **Format nou** (26 pàgines: homepage, categories, blogs, alguns productes): columna "Legal" independent amb `<span class="lca/les">` dins de `<a href>`.
- **Format antic** (12 pàgines de producte): columna "Contacte" amb links legals afegits al final de la llista, usant `class="lca"` / `class="les"` directament a l'`<a>`.

---

## Pàgines legals (noves)

### `politica-privacitat.html`
- RGPD + LOPDGDD compliant
- Responsable: Benestar i Solucions S.L.
- Seccions: informació i consentiment, dades recollides, finalitat, base jurídica, conservació, tercers, drets (accés/rectificació/supressió/oposició/limitació/portabilitat), seguretat, modificacions, referència a cookies
- Bilingüe: bloc `<div class="lca">` i `<div class="les">` separats

### `politica-cookies.html`
- Cookie única: `bs-lang` (localStorage, tècnica, pròpia, persistent)
- Taula de cookies responsive (`.cookie-table-wrap { overflow-x: auto }`)
- Explicació de localStorage vs cookie HTTP
- Instruccions per gestionar cookies als 4 navegadors principals
- Bilingüe: bloc `<div class="lca">` i `<div class="les">` separats

---

## Fitxers de scripts (es poden eliminar)
- `fix_nav_dropdown.py`
- `fix_related_products.py`
- `fix_mobile_overflow.py`
- `fix_mobile_compact.py`
- `fix_gallery_and_logo.py`
- `fix_gallery_complex.py`
- `fix_logo_and_gallery_final.py`

---

## Pendent
- [ ] Connectar formulari de contacte a un backend real (ara no envia emails)
- [ ] Substituir placeholder d'adreça "Barcelona, Catalunya" per l'adreça real
- [ ] Crear `avis-legal.html` (si es vol completar la secció legal)
