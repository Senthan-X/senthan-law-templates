# Senthan & Co — Law Firm Template Collection

Four single-file HTML templates for law firm websites, each built around a different practice area with its own visual identity. Built for Codester/ThemeForest-style resale and as standalone client-ready sites.

**[View the collection](index.html)**

## Templates

| Template | Practice Area | Theme Default | Signature Feature |
|---|---|---|---|
| [Whitfield & Cole](whitfield-cole-index.html) | Corporate & Business Law | Light | Interactive "defined term" glossary in the hero |
| [Redress Law](redress-law-index.html) | Personal Injury | Light | Animated Settlement Meter (offer vs. recovery) |
| [Kinfolk Family Law](kinfolk-family-law-index.html) | Family & Divorce Law | Light | 4-step "Path Forward" process stepper |
| [Voss Criminal Defense](voss-criminal-defense-index.html) | Criminal Defense | Dark | Flip-card "Know Your Rights" set |

## Shared architecture

Every template in this collection is a **single, dependency-free HTML file** — no build step, no external image folders, no CDN dependency.

- **Theming** — CSS custom properties drive a full dark/light mode, toggled via a header button and persisted to `localStorage`. Each firm has its own light and dark palette.
- **Internationalization** — 8 languages built in (English, Spanish, French, German, Portuguese, Arabic, Chinese, Swahili), including full right-to-left layout support for Arabic. Language selection persists across visits.
- **Images** — All photography is resized, re-encoded to WebP, and embedded directly as base64 data URIs, so the template works from a single file with no missing-asset risk. Typical total page weight is 200–320KB.
- **Motion** — Scroll-reveal animation via `IntersectionObserver`, with a `prefers-reduced-motion` fallback that disables animation entirely.
- **Resilience** — A defensive `localStorage` wrapper prevents crashes in private-browsing modes or environments where storage is blocked.
- **Accessibility** — Visible focus states, semantic landmarks, and keyboard support on interactive components (e.g. the flip cards in Voss Criminal Defense).

## Local preview

No build tools required. Clone the repo and open any `index.html` directly in a browser, or serve the folder locally:

```bash
git clone https://github.com/<your-username>/senthan-law-templates.git
cd senthan-law-templates
python3 -m http.server 8000
# visit http://localhost:8000
```

## Customizing for a client

Each template uses placeholder firm names, attorney names, addresses, and testimonials — all fictional. To adapt a template:

1. Replace the firm name (appears in the `<title>`, header brand, and footer).
2. Update the contact block (address, phone, email) in the Contact section.
3. Swap attorney names/bios and the monogram initials in the `.badge` elements.
4. Replace the embedded images (see below) with licensed photography.
5. Edit the `window.__XX_I18N__` object in the final `<script>` block to update copy — every visible string runs through this object, keyed by language.

### Replacing images

Images are embedded as `data:image/webp;base64,...` strings. To swap one out:

```bash
# convert and encode a new image
python3 -c "
from PIL import Image
im = Image.open('new-photo.jpg').convert('RGB')
im.save('new-photo.webp', 'WEBP', quality=78)
"
base64 -w0 new-photo.webp > new-photo.b64.txt
```

Then replace the base64 string inside the matching `<img src="data:image/webp;base64,...">` tag with the new file's contents.

## Licensing note

The public demos use photographs under the [Pexels License](https://www.pexels.com/license/). The [imagery ledger](LAW-IMAGERY.json) records each placement, photographer, source page, and embedded image digest. Senthan Commerce buyer downloads include editable photo slots and setup guides.

## Credits

Built by **Senthan & Co** — [hello@senthan-co.example](mailto:hello@senthan-co.example) · +256 700 000 000
