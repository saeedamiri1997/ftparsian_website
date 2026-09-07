# FTParsian website design system

This document supersedes `design_brief.md` and is the single source of truth for every page of the plain HTML marketing website.

## 1. Brand, audience, and voice

- **Brand:** فرا تهویه پارسیان (Fara Tahvieh Parsian)
- **Domain:** `https://ftparsian.ir`
- **Service base:** کرج and surrounding areas. Larger projects elsewhere in Iran are accepted only when the client covers crew travel and lodging costs.
- **Audience:** builders, project managers, industrial and commercial owners, consulting engineers, facility teams, and clients of specialist residential projects.
- **Voice:** engineering-grade, industrial, precise, trustworthy, direct, and transparent. Do not invent history, certifications, projects, or competitive claims.
- **Font:** Vazirmatn loaded from Google Fonts and used throughout the page, including forms, buttons, navigation, and metadata-facing content.

## 2. Corrected color system

Use this exact palette in every page. The logo reference uses blue `#018ED3` and magenta-pink `#D60757`; the interface uses the refined CTA accent below for contrast.

```css
:root {
  --primary: #018ED3;        /* logo blue - header, links, icons */
  --primary-dark: #0C447C;   /* hover/active state of primary */
  --accent: #C81E3A;         /* refined CTA red - deeper/less saturated than raw logo magenta, better contrast */
  --accent-hover: #A32D2D;
  --success: #3B6D11;        /* used ONLY for QC/guarantee/checkmark indicators, never decoratively */
  --text-primary: #2C2C2A;   /* near-black charcoal, not pure #000 */
  --text-secondary: #5F5E5A;
  --bg-main: #FFFFFF;
  --bg-alt: #F1EFE8;         /* warm light gray for alternating sections */
  --border: #E5E3DC;
  --font-family: 'Vazirmatn', -apple-system, BlinkMacSystemFont, sans-serif;
}
```

Use flat, single-color surfaces from `--bg-main` and `--bg-alt`. `--success` is reserved for QC, guarantee, and checkmark indicators. Text must use `--text-primary` or `--text-secondary` rather than pure black.

## 3. Typography and layout

- All documents use `<html lang="fa" dir="rtl">`.
- H1: `2.25rem` on desktop and `1.75rem` on mobile; bold or extra-bold.
- H2: `1.75rem` on desktop and `1.35rem` on mobile; semi-bold.
- Body: `1rem`, regular weight, line-height `1.75`.
- Secondary and metadata text: light weight and smaller size.
- Mobile-first layouts must remain usable at 360px, 768px, 1024px, and 1440px.
- Use strict CSS grid and flex layouts, generous whitespace, thin dividers, and alternating `--bg-main` / `--bg-alt` sections.
- Buttons have a flat fill or outline, `border-radius` no greater than 8px, and a hover state limited to a slight color change and `scale(1.02)`.
- Cards may use one flat `0 1px 3px rgba(0, 0, 0, 0.08)` shadow at most; a `1px solid var(--border)` is preferred.
- Use outline, single-color symbols or simple text labels. Do not use multi-color decorative illustrations.

## 4. Motion and interaction

- Allowed motion is limited to subtle scroll reveal fade/slide-up and button/card hover scale `1.02`.
- Transitions must be between 150ms and 250ms with ordinary ease-in-out timing. Do not use bounce, elastic, parallax, particle, mesh, blob, or other heavy effects.
- Respect `prefers-reduced-motion` by disabling reveal transitions and smooth scrolling.

## 5. Technical and SEO rules

- Every deliverable is a complete, self-contained HTML file with inline `<style>` and no build step or bundler.
- Keep a clearly delimited `HEAD-ONLY SEO BLOCK` comment at the very top of each file. It contains the title, description, canonical URL, Open Graph URL, Google Fonts link, and JSON-LD so it can be copied into Yoast or Rank Math later.
- Each page has exactly one H1 and uses semantic HTML5 landmarks: header, nav, main, section/article, and footer.
- Every page contains appropriate schema.org JSON-LD. Use `HVACBusiness` / `LocalBusiness` for company context, `Service` for service pages, and `FAQPage` for the FAQ page.
- Use the URL map below for all internal links and canonical metadata. The client panel is external and is link-only.
- The common header, navigation, footer, and mobile contact bar markup is copied byte-for-byte between all pages. Only the active navigation class differs per page.
- Real contact numbers are `۰۹۱۳۵۳۹۳۹۸۶` and `۰۹۱۳۷۸۴۶۶۲۵`. A third number beginning `۰۹۱۳۹۸۴` is not published until confirmed.
- Instagram is a placeholder until its URL is confirmed. WhatsApp and Telegram use the two confirmed phone numbers.

## 6. URL map

| Page | File | Canonical URL |
| --- | --- | --- |
| Home | `index.html` | `https://ftparsian.ir/` |
| About us | `about-us.html` | `https://ftparsian.ir/about-us` |
| Services hub | `services.html` | `https://ftparsian.ir/services` |
| Copper piping | `services/copper-piping.html` | `https://ftparsian.ir/services/copper-piping` |
| HVAC installation | `services/hvac-installation.html` | `https://ftparsian.ir/services/hvac-installation` |
| Maintenance & support | `services/maintenance-support.html` | `https://ftparsian.ir/services/maintenance-support` |
| Polyurethane ducts | `services/polyurethane-ducts.html` | `https://ftparsian.ir/services/polyurethane-ducts` |
| Projects / portfolio | `projects.html` | `https://ftparsian.ir/projects` |
| Request inspection | `request-inspection.html` | `https://ftparsian.ir/request-inspection` |
| FAQ | `faq.html` | `https://ftparsian.ir/faq` |
| Contact us | `contact-us.html` | `https://ftparsian.ir/contact-us` |
| Client panel | external, no local file | `https://panel.ftparsian.ir` |

## 7. Content guardrails

Use the confirmed company story: Mr. Karimian entered the trade in ۱۳۹۲, worked through design, supervision, execution, warehousing, sales, and technical assessment until ۱۳۹۴, became independent in ۱۳۹۴, held official Mitsubishi Electric representation in ۱۳۹۶–۱۳۹۷, began pre-insulated polyurethane duct work with ۸۰-micron aluminum from ۱۳۹۷, moved to trained specialist copper-piping crews from ۱۳۹۸, and began licensing processes in ۱۳۹۶.

Use the confirmed service categories: copper piping using Bahonar, Babak, Ghaem, and Mehr brands; HVAC unit installation of all types; maintenance, repair, and technical support; and pre-insulated polyurethane ducts with ۸۰-micron aluminum.

Use the six confirmed advantages without embellishment: optimized engineering design, fast execution including a ۵۰۰m² project completed in one day, pressure and quality testing before handover, buyback of unused pipe including unwelded full rolls, free technical assessment with floor-plan marking and a detailed material list, and issue resolution under ۲۴ hours (often under ۱۲) with a free six-month guaranteed support contract and paid annual renewal option.
