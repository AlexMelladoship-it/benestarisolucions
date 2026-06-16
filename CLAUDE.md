# Benestari Solucions — Estat del projecte

## On ens vam quedar

**Tota la web v2 està implementada i llesta per pujar a GitHub + Netlify.**
Només falta fer el push — l'usuari ha decidit no fer-lo encara.

---

## Com fer el deploy quan estiguis llest

1. **Inicialitza git i puja a GitHub:**
```bash
git init
git add .
git commit -m "v2 redesign complet"
git remote add origin https://github.com/AlexMelladoship-it/benestarisolucions.git
git push -u origin main
```
2. **Netlify** es redesplega automàticament en fer push al repo connectat.

---

## Estructura de fitxers (40 HTML)

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
--green-deep:  oklch(0.22 0.09 136)   /* footer + serveis (nou v2) */
--white:       #FAFAF8
```
Fonts: **DM Sans** (cos) + **DM Serif Display** (títols) — Google Fonts.

### Seccions homepage
1. **Nav** — fixed, transparent sobre hero → blanc amb blur en scroll (`.scrolled` a scrollY > 60). Dropdown desktop de Productes. Hamburger mòbil.
2. **Hero** — foto Ken Burns (`uploads/IMG_HERO.png`), overlay fosc, badge animat, h1 serif, botons CTA, stats animats (500+, 10+, 100%, 33).
3. **Marquee** — franja animada entre hero i categories.
4. **Categories** — grid 2×2, imatges de `IMAGENES WEB baners principales/`, número badge, fletxa rotativa al hover.
5. **Qui som** — layout 2 columnes (imatge + text). Imatge: `IMG_sobre nosotros.jpg`, `object-position: 65% 68%`. Targeta flotant "10+ anys".
6. **Serveis** — fons `--green-deep`, llista numerada (01–04).
7. **Blog** — 3 targetes, imatges de `IMAGENES WEB baners principales/`, links a blogs reals.
8. **Contacte** — email: `benestarisolucions@gmail.com` / tel: `+34 623 412 836`.
9. **Footer** — fons `--green-deep`, 4 columnes.

### Sistema bilingüe (CA/ES)
- `localStorage` key: `bs-lang`
- Català: `<span class="lca">text</span>`
- Castellà: `<span class="les">text</span>`
- CSS: `html[lang="ca"] .les { display: none }` i viceversa
- **IMPORTANT:** Mai afegir `style="display:none"` a elements `.les` — l'inline style sobreescriu el CSS i trenca el canvi d'idioma.

---

## Canvis realitzats a totes les pàgines

Tots els fitxers `.html` (excepte `Benestari Solucions.html`) tenen:
- **Dropdown de nav desktop** per a Productes (CSS + HTML) amb les 4 categories
- **`@media (min-width: 769px) { .nav-mobile-btn { display: none !important; } }`** — evita hamburger en escriptori
- **Mobile menu** sense `style="display:none"` als elements `.les`
- **Related products** — tots els productes eliminats del catàleg han estat substituïts per productes existents
- **Footer** — sense duplicats (bug del script original corregit)

---

## Fitxers de scripts (es poden eliminar)
- `fix_nav_dropdown.py` — ja executat, es pot esborrar
- `fix_related_products.py` — ja executat, es pot esborrar

---

## Pendent
- [ ] **Push a GitHub** (`https://github.com/AlexMelladoship-it/benestarisolucions.git`)
- [ ] **Deploi a Netlify** (automàtic un cop fet el push)
- [ ] Connectar formulari de contacte a un backend real (ara no envia emails)
- [ ] Substituir placeholder d'adreça "Barcelona, Catalunya" per l'adreça real
