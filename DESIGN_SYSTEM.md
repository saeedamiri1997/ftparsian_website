# FTParsian website design system — "Modern Bright Corporate-Tech"

> **Direction change (round 3).** This revision replaces the round-1/round-2 flat-industrial
> language (flat 1px-border cards, warm gray tints, no shadows, angled clip-path cuts) with the
> modern bright corporate-tech system specified below. The previous version is preserved in this
> file's git history. This document supersedes `design_brief.md` and remains the single source of
> truth for every page of the plain HTML marketing website.

## 1. Brand, audience, and voice

- **Brand:** فرا تهویه پارسیان (Fara Tahvieh Parsian)
- **Domain:** `https://ftparsian.ir`
- **Service base:** کرمان and surrounding areas. Larger projects elsewhere in Iran are accepted only when the client covers crew travel and lodging costs.
- **Audience:** builders, project managers, industrial and commercial owners, consulting engineers, facility teams, and clients of specialist residential projects.
- **Voice:** engineering-grade, precise, trustworthy, direct, and transparent. Do not invent history, certifications, projects, or competitive claims.
- **Font:** Vazirmatn loaded from Google Fonts and used throughout the page, including forms, buttons, navigation, and metadata-facing content.
- **Visual register:** bright, spacious, professional — a well-funded tech/SaaS product site (Linear/Stripe/Vercel feel), not a brochure. White-dominant, soft light-blue tints, generous whitespace, confident large typography, soft layered shadows, pill buttons, rounded cards, subtle hover motion. Still fully RTL Persian.

## 2. Design tokens

Use this exact `:root` block in every page. The logo reference uses blue `#018ED3` and magenta-pink `#D60757`; the interface uses the refined CTA accent below for contrast.

```css
:root {
  --primary: #018ED3;
  --primary-dark: #0C447C;
  --primary-50: #EAF6FC;   /* light tint wash for alternating sections */
  --primary-100: #D3ECF8;  /* icon-chip backgrounds, subtle borders */
  --accent: #C81E3A;
  --accent-hover: #A32D2D;
  --success: #3B6D11;      /* still QC/guarantee-only, unchanged */
  --text-primary: #1B1B1A; /* slightly deeper than before for stronger headline contrast */
  --text-secondary: #5F5E5A;
  --bg-main: #FFFFFF;
  --bg-alt: #F7FBFD;       /* cooler, techier than the old warm tint */
  --border: #E7EEF3;
  --radius-md: 12px;
  --radius-lg: 20px;
  --radius-pill: 999px;
  --shadow-sm: 0 2px 8px rgba(1, 68, 124, 0.06);
  --shadow-md: 0 8px 24px rgba(1, 68, 124, 0.10);
  --shadow-lg: 0 20px 48px rgba(1, 68, 124, 0.14);
  --ease: cubic-bezier(0.4, 0, 0.2, 1);
  --font-family: 'Vazirmatn', -apple-system, BlinkMacSystemFont, sans-serif;
}
```

`--success` is reserved for QC, guarantee, and checkmark indicators only. Text must use `--text-primary` or `--text-secondary` rather than pure black.

## 3. Typography and layout

- All documents use `<html lang="fa" dir="rtl">`.
- Hero H1: `2.75–3.5rem` on desktop / `2rem` on mobile; weight 800–900; tight line-height.
- Section H1 (inner pages): `2.25rem` desktop / `1.75rem` mobile; bold or extra-bold.
- H2: `1.75rem` desktop / `1.35rem` mobile; semi-bold or bold.
- Body: `1rem`, regular weight, line-height `1.75`.
- Secondary and metadata text: light weight and smaller size.
- Mobile-first layouts must remain usable at 360px, 768px, 1024px, and 1440px.
- Strict CSS grid and flex layouts, generous whitespace, alternating `--bg-main` / `--primary-50` full-bleed section washes. No `clip-path` angled cuts.

## 4. Components

- **Buttons:** pill-shaped (`border-radius: var(--radius-pill)`), generous horizontal padding. Primary = `--accent` fill + `--shadow-sm`; hover = `translateY(-2px)` + `--shadow-md` + `--accent-hover` background, 250ms `var(--ease)`. Secondary = white fill with `--border` outline (or `--primary` outline), same hover lift.
- **Cards:** `border-radius: var(--radius-lg)`, white background, `--shadow-sm` at rest; hover = `--shadow-md` + `translateY(-4px)`, 250ms `var(--ease)`. The old flat 1px-border-only card style is retired.
- **Icons:** the round-2 inline SVG sprite set is kept as-is (not redrawn). Every icon now sits inside a circular chip: `--primary-100` background circle, icon in `--primary`, ~48–56px chip. This replaces the bare-icon-on-white pattern.
- **Section backgrounds:** alternate `--bg-main` / `--primary-50`. One or two large, very-low-opacity blurred circular gradient blobs (`radial-gradient`, `filter: blur(60–100px)`, opacity 0.15–0.25, `--primary`/`--accent` tones) may sit as absolute-positioned decorative background elements behind the hero and at most one other section. This is the only place a gradient is allowed: purely ambient background glow, never on text-bearing surfaces, buttons, or interactive elements, and never where it could harm contrast.
- **Header:** sticky. A scroll listener (in the existing inline page script) toggles a class past ~40px adding `--shadow-sm` plus `background: rgba(255,255,255,0.92)` with `backdrop-filter: blur(8px)`. This restrained scroll-blur is intentional in this language; it stays on the header only.
- **Hero:** two-column split. Copy side: eyebrow label, large bold H1, supporting paragraph, two pill CTAs side by side, trust-bar mini stats inline below (icon chip + number pattern, small). Visual side: the round-2 ductwork illustration (strokes/fills retinted to the new tokens) in front of one blurred gradient blob, plus 1–2 small floating stat-chip cards overlapping the illustration edges (white, `--shadow-md`, `--radius-lg`). The `REPLACE WITH REAL PROJECT PHOTO` comment stays: the illustration+blob+chip composition is what a real photo drops into later.
- **Trust bar / stats band:** `--primary-50` band with bigger, bolder numbers (2–2.5rem, weight 800) and the icon-chip treatment.
- **Footer:** solid `--primary-dark` background, white text, columns (about / quick links incl. Blog / services / contact). Links get underline-on-hover. No shadow/card treatment — the dark anchor grounds the page.
- **Forms/inputs:** `--radius-md`, `--border` outlines, `--primary` focus rings that meet contrast on the new tints.

## 5. Motion and interaction

- Scroll-reveal fade-up stays, with a slight stagger (60–100ms delay increments) between sibling cards in a grid.
- Hover lifts use 250ms `var(--ease)`; nothing bouncy, nothing longer than ~350ms.
- Respect `prefers-reduced-motion` by disabling reveal transitions, stagger delays, and smooth scrolling.

## 6. Technical and SEO rules

- Every deliverable is a complete, self-contained HTML file with inline `<style>` and no build step or bundler.
- Keep a clearly delimited `HEAD-ONLY SEO BLOCK` comment at the very top of each file. It contains the title, description, canonical URL, Open Graph URL, Google Fonts link, and JSON-LD so it can be copied into Yoast or Rank Math later.
- Each page has exactly one H1 and uses semantic HTML5 landmarks: header, nav, main, section/article, and footer.
- Every page contains appropriate schema.org JSON-LD. Use `HVACBusiness` / `LocalBusiness` for company context and `Service` for service pages.
- Use the URL map below for all internal links and canonical metadata. The client panel and the WordPress blog are external links only (no local files).
- The common header, navigation, footer, and mobile contact bar markup is copied byte-for-byte between all pages. Only the active navigation class differs per page.
- Contact numbers are final: `۰۹۱۳۵۳۹۳۹۸۶` and `۰۹۱۳۷۸۴۶۶۲۵`. No third number.
- Instagram is a placeholder until its URL is confirmed. WhatsApp and Telegram use the two confirmed phone numbers.

## 7. URL map

| Page | File | Canonical URL |
| --- | --- | --- |
| Home | `Website/index.html` | `https://ftparsian.ir/` |
| About us | `Website/about-us.html` | `https://ftparsian.ir/about-us` |
| Services hub | `Website/services.html` | `https://ftparsian.ir/services` |
| Copper piping | `Website/services/copper-piping.html` | `https://ftparsian.ir/services/copper-piping` |
| HVAC installation | `Website/services/hvac-installation.html` | `https://ftparsian.ir/services/hvac-installation` |
| Maintenance & support | `Website/services/maintenance-support.html` | `https://ftparsian.ir/services/maintenance-support` |
| Polyurethane ducts | `Website/services/polyurethane-ducts.html` | `https://ftparsian.ir/services/polyurethane-ducts` |
| Projects / portfolio | `Website/projects.html` | `https://ftparsian.ir/projects` |
| Request inspection | `Website/request-inspection.html` | `https://ftparsian.ir/request-inspection` |
| Contact us | `Website/contact-us.html` | `https://ftparsian.ir/contact-us` |
| Blog | external (WordPress), no local file | `https://ftparsian.ir/blog` |
| Client panel | external, no local file | `https://panel.ftparsian.ir` |

## 8. Content guardrails

Use the confirmed company story: Mr. Karimian entered the trade in ۱۳۹۲, worked through design, supervision, execution, warehousing, sales, and technical assessment until ۱۳۹۴, became independent in ۱۳۹۴, held official Mitsubishi Electric representation in ۱۳۹۶–۱۳۹۷, began pre-insulated polyurethane duct work with ۸۰-micron aluminum from ۱۳۹۷, moved to trained specialist copper-piping crews from ۱۳۹۸, and began licensing processes in ۱۳۹۶.

Use the confirmed service categories: copper piping using Bahonar, Babak, Ghaem, and Mehr brands; HVAC unit installation of all types; maintenance, repair, and technical support; and pre-insulated polyurethane ducts with ۸۰-micron aluminum.

Use the six confirmed advantages without embellishment: optimized engineering design, fast execution including a ۵۰۰m² project completed in one day, pressure and quality testing before handover, buyback of unused pipe including unwelded full rolls, free technical assessment with floor-plan marking and a detailed material list, and issue resolution under ۲۴ hours (often under ۱۲) with a free six-month guaranteed support contract and paid annual renewal option.
