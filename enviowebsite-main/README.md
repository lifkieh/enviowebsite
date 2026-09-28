# PT Envio Kompound Indonesia — B2B Website

A static, premium B2B website for PT Envio Kompound Indonesia (compostable biopolymer &
bioplastic compounding manufacturer). No build tools or server required — plain HTML/CSS/JS.

## Structure

```
envio-kompound-website/
├── index.html            Home
├── about.html             About Us / Vision & Mission / Why Choose Us / Industries Served / Environmental & Quality
├── products.html          Core Products & Services / PLA Compounds / Natural Resource Compounds (photo gallery)
├── contact.html           Contact Information + Form Inquiry (WhatsApp / Email)
├── css/style.css          Shared stylesheet (brand colors, layout, components)
├── js/main.js             Nav (mobile menu, dropdowns), scroll reveal, sub-nav active state
├── js/contact-form.js     Inquiry form logic (WhatsApp + Email routing)
└── assets/images/
    ├── logo/               Logo extracted from LOGO ENVIO.pdf (color + white variants, favicon)
    └── products/           Natural Resource Compound gallery images (see products/README.md)
```

## Viewing the site

No server needed — just open `index.html` directly in a browser. For local development with
correct relative paths, you can also run a simple static server from this folder, e.g.:

```
python -m http.server 8080
```

then visit `http://localhost:8080`.

## Replacing the Natural Resource Compound photos

The gallery on `products.html` (section "Natural Resource Compounds") currently uses styled
placeholder visuals. Replace them with real product photography by overwriting these exact
files (same filename, ideally similar 4:3 aspect ratio, at least 1200×900px):

- `assets/images/products/coffee-powder-compound.jpg`
- `assets/images/products/wood-chip-compound.jpg`
- `assets/images/products/cellulose-compound.jpg`
- `assets/images/products/cassava-compound.jpg`
- `assets/images/products/sugarcane-compound.jpg`
- `assets/images/products/pla-compound.jpg` (used on Home + PLA Compounds section)

Once real photos are dropped in with the same filenames, no HTML/CSS changes are needed.
See `assets/images/products/README.md` for details, and remove the placeholder disclaimer
line in `products.html` (the `<p class="gallery-note">…</p>` element) once real photos are live.

## Configuring the Inquiry Form (WhatsApp & Email)

Edit the two constants at the top of `js/contact-form.js`:

```js
var WHATSAPP_NUMBER = "628561151431"; // international format, no + or spaces
var CONTACT_EMAIL   = "marketing@enviocompound.com";
```

The form has no backend — clicking **Send via WhatsApp** opens `wa.me` with the form data
pre-filled as a message; **Send via Email** opens the visitor's email client (`mailto:`) with
the same content pre-filled as the subject/body. Nothing is stored or sent automatically.

If you later want submissions to also land in a spreadsheet/CRM/inbox without the visitor's
own WhatsApp or email client, that requires a small backend or a form service (e.g. Formspree,
Google Sheets via Apps Script, or a custom endpoint) — not included here since it wasn't part
of the original brief, but the form markup in `contact.html` (`#inquiry-form`) is ready to be
wired to one if needed.

## Brand assets

- `assets/images/logo/logo-color.png` — full color logo (leaf mark + "ENVIO" wordmark), used on light backgrounds.
- `assets/images/logo/logo-white.png` — white silhouette version, used on dark backgrounds (footer).
- `assets/images/logo/favicon-256.png` — square leaf mark only, used as the browser tab icon.

All three were extracted from the client-supplied `LOGO ENVIO.pdf`.

## Deployment

This is a fully static site — it can be deployed as-is to any static host (Hostinger, Netlify,
Vercel, GitHub Pages, etc.) by uploading the contents of this folder. No environment variables,
database, or build step required.
