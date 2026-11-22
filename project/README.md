# Edgars Zeltmanis: AI, research and software

**What it is:** A website for everyone who wants to know what I do professionally, so that they might want to collaborate.
**Audience:** Anyone interested in AI and research (possible collaborators, classmates, teachers), mostly on a laptop or phone, to see who I am, what I work on and how to reach me.
**Pages:**
- **Home**: who I am and what I do, in short
- **Studies**: my software engineering studies at MUDT
- **AI Project**: Aura, my self-hosted AI project, with its roadmap; details on zeltmanis.com
- **Contact**: contact form, CV download, links to starit.lv and zeltmanis.com
**Live:** https://zeltmanis.github.io/cm501-Edgars/project/

**Changes over time:** Aura roadmap (e.g. starting conversations, web access), new projects and semester modules.

**Later:** rebuilt with Astro and Tailwind CSS (EPA 3 and 5).

## HTML baseline (Session 4 · prerequisite for EPA 3)

Fill in **where** each feature is used (file and element or line). Must items (M) are required; pick optional items (O) that fit your content.

| # | Feature | Where (file · element / line) |
|:--:|------------------------------------------------------------|------------------------------|
| M1 | `lang`, `charset`, `viewport`, unique `title` ("Page · Site"), `meta description`, favicon | all pages · `<html lang="en">`, charset, viewport, `<title>` "Home · Edgars Zeltmanis" etc., `meta description`, `favicon.svg` (index.html l. 5–13) |
| M2 | landmarks `header` `nav` `main` `footer`; skip link as first element | all pages · `header`, `nav`, `main id="main"`, `footer`; skip link is the first element in `body` (index.html l. 21–71) |
| M3 | navigation as a list, identical on all pages, `aria-current="page"` | all pages · `<nav aria-label="Main">` with `<ul>`, same 4 links, `aria-current="page"` on the current page (index.html l. 28–35) |
| M4 | one `h1` per page, no skipped heading levels | index.html · one `h1` (l. 40) → `h2` (l. 44) → `h3` (l. 48, 55); other pages one `h1` each |
| M5 | images: `alt` (or `alt=""`), `width`/`height`, `loading="lazy"` below the fold; one `figure` + `figcaption` | index.html · `figure` + `figcaption` with `img/edgars-caricature.jpg`, meaningful `alt`, `width`/`height` 600×900, `loading="lazy"` (l. 65–68) |
| M6 | lists for lists; `article`/`section` with headings where they fit | index.html · `section` "What I'm working on" with a `<ul>` of two `article`s (l. 43–62) |
| M7 | meaningful link texts; `<address>` with `tel:` / `mailto:` links | index.html · link texts "Read more about Aura", "See what I'm studying"; footer `<address>` with `mailto:` (l. 73–77); no phone on purpose (privacy) |
| M8 | `<time datetime="…">` for at least one date or time | index.html · `<time datetime="2026-11">`, `<time datetime="2026-10">` (l. 49, 56) |
| M9 | one form: visible labels, right `type`, `autocomplete`, "(required)" + `required`, real `<button>`; `fieldset`/`legend` for groups | contact.html · form: visible labels, `type="email"`, `autocomplete`, "(required)" + `required`, `fieldset`/`legend` for the topic radios, `<button>` "Send message" (l. 32–52) |
| M10 | W3C validator 0 errors · axe 0 violations · keyboard: everything reachable, focus visible | all 4 pages: W3C validator 0 errors, Lighthouse accessibility (axe) 100; keyboard: see Tests |
| O1 | responsive image: `srcset` + `sizes` or `<picture>` | |
| O2 | data table with `<caption>` and `<th scope>` | |
| O3 | `<details>` / `<summary>` (e.g. FAQ) | |
| O4 | `<dl>` for name–value pairs (e.g. opening hours, facts) | |
| O5 | `<blockquote>` with source, `<abbr>` with the expansion written out once | |
| O6 | icon-only link or button with `aria-label` and `aria-hidden="true"` on the icon | |
| O7 | `<iframe>` with `title` (map, video), privacy considered | |
| O8 | `lang` on a passage in another language (e.g. `<span lang="de">`) | |

**Tests:** validator: 2026-11-15, 0 errors on all 4 pages · axe (via Lighthouse 12.8.2 accessibility): 100 on all 4 pages, 0 violations · keyboard (2026-11-15, live site): every link, field and the button reachable with Tab; the topic radio group is one Tab stop and the options change with the arrow keys; focus outline visible at every stop; CV download works · screen reader: TODO

**AI use:** Claude (AI) suggested the texts and markup step by step and explained why; I typed the home page and the contact form, and Claude created the studies, AI project and contact page skeletons from the template, fixed my slips and ran the validator and Lighthouse.

## Design

The website is designed for recruiters, lecturers and people interested in my work on Aura. I wanted it to feel calm, precise and trustworthy, while combining a warm personal touch with a technical look. I chose a light, misty background, frosted-glass cards and black pill-shaped elements, with the shimmer card as the only colourful accent. The layout uses a system font for faster loading, and all design values are defined as CSS tokens in `:root`. I followed a mobile-first approach, using two breakpoints at 40rem and 64rem, with a two-column layout for pages that include an image.

I tested the website at 320, 768, 1280 and 1920px widths, as well as at 400% zoom. I checked colour contrast for every colour combination, validated the HTML with the W3C validator and tested keyboard navigation, including the skip link and visible focus outlines. AI (Claude) helped me understand CSS concepts, calculate contrast ratios, create colour previews and review and correct my code, but I made the design decisions and typed the CSS myself.
