# Test protocol: Campus Café repair (EPA 2)

Pages: `menu.html` and `contact.html`, repaired from the starter kit (first commit = unchanged starter).
Live: https://zeltmanis.github.io/cm501-Edgars/epa2-campus-cafe/menu.html and …/contact.html
Target: WCAG 2.2 AA. The fixed 1100 px layout stays (responsive layout is EPA 3).

## C1 · Issue list

### menu.html

| # | Problem | WCAG SC | Fix |
|---|---|---|---|
| 1 | No `lang` on `<html>`: the screen reader guesses the voice | 3.1.1 | `<html lang="en">` (plus doctype and viewport) |
| 2 | Title "Home" on the menu page | 2.4.2 | "Menu · Campus Café" |
| 3 | No landmarks, everything is a `div` | 1.3.1 | `header`, `nav`, `main`, `footer` |
| 4 | No way to skip the navigation | 2.4.1 | Skip link to `#main` |
| 5 | Nav items are `div onclick`: not focusable, no link role | 2.1.1, 4.1.2 | Real `<a href>` links in a `<ul>`, `aria-current="page"` |
| 6 | Headings jump from h1 to h4 | 1.3.1 | Categories as `h2` |
| 7 | Layout table, obsolete `<font>`, items as `div` + `<br>` | 1.3.1 | Each category a `<ul>`; name, price, description as text |
| 8 | Today's special only as text inside a JPG | 1.1.1, 1.4.5 | Special as real text; image is decorative, `alt=""` |
| 9 | Images without `alt` | 1.1.1 | `alt=""` for decorative images |
| 10 | Social icons: `href="#"` and no text, announced only as "link" | 2.4.4, 4.1.2 | Real URLs, visually hidden names, SVG `aria-hidden="true"` |
| 11 | `* { outline: none !important }`: focus invisible | 2.4.7 | Removed; `:focus-visible` outline (blue on white 6.3:1, yellow on dark 8.3:1) |
| 12 | Low contrast: body text #b3b3b3 on white 2.1:1, prices 1.45:1, headings 1.66:1, nav 2.9:1 | 1.4.3 | Body #333 12.6:1, headings #6b4a36 7.9:1, nav/footer #f3e6d8 on #3b2a20 11.1:1 |

### contact.html

| # | Problem | WCAG SC | Fix |
|---|---|---|---|
| 13 | Same page frame problems as menu.html: no `lang`, title "Home", no landmarks, `div onclick` nav | 3.1.1, 2.4.2, 1.3.1, 2.1.1 | Same header, nav and skip link as menu.html |
| 14 | Phone and e-mail only inside an image without alt, in light grey | 1.1.1, 1.4.5 | `<address>` with `tel:` and `mailto:` links |
| 15 | Google Maps iframe without `title`; also loads Google before any consent | 4.1.2 (+ privacy) | Replaced by a plain link "Show the café on Google Maps" |
| 16 | "Newsletter & reservations" is a styled `div` | 1.3.1 | `<h2>` |
| 17 | Form fields with placeholder only, no labels | 1.3.1, 3.3.2 | `<label for>` on every field; required fields say "(required)" |
| 18 | All fields `type="text"`, no autocomplete | 1.3.5 | `type="email"`, `type="tel"`, `autocomplete` (name, email, tel), `required` |
| 19 | "Send" is a `div onclick`: no keyboard access | 2.1.1, 4.1.2 | `<button type="submit">` |
| 20 | Field text #bbb, button text #999, borders #eee / #ccc | 1.4.3, 1.4.11 | Text #333 / #3b2a20, field border #767676, button border 2px #3b2a20 |
| 21 | `method="get"` puts name, e-mail and phone in the URL; birthday collected without need | privacy | `method="post"`, birthday field removed (data minimisation) |

## C2 · Automated tests

| Tool | menu.html before | menu.html after | contact.html before | contact.html after |
|---|---|---|---|---|
| W3C HTML validator (errors) | 14 | 0 | 2 | 0 |
| Lighthouse accessibility | 46 | 100 | 48 | 100 |
| WAVE errors / contrast errors / alerts | 5 / 38 / 5 | 0 / 0 / 0 | 9 / 8 / 4 | 0 / 0 / 0 |
| WAVE AIM score | 3.6 | 9.1 | 5.4 | 10 |

Screenshots for menu.html: `screenshots/`. Before = unchanged starter; after = live GitHub Pages version.
Lighthouse failures on contact.html before: color-contrast, frame-title, html-has-lang, image-alt, link-name.

contact.html after: WAVE (web version and browser extension) on the live page, 2026-11-15. The first extension run still showed 2 contrast errors that were not visible on the page. They were most likely the visually hidden footer link names (browser-blue text on the dark footer). After footer links got the light footer colour (`.foot a`) and the page was hard-reloaded, both WAVE variants showed 0 / 0 / 0.

## C3 · Manual tests

**Keyboard (menu.html):** Tab order is skip link → Menu → Contact → Facebook → Instagram. The focus outline is visible on every stop, and Enter opens the links. The menu content is not in the Tab order. That is correct, because it is not interactive.

**Keyboard (contact.html):** Tab order is skip link → Menu → Contact → phone → e-mail → map link → Name → E-mail → Phone → Message → Send → Facebook → Instagram. The focus outline is visible at every stop (2026-11-15).

**Screen reader:** VoiceOver (macOS) with Safari on menu.html, 2026-11-15. The rotor lists headings (Menu, Today's special, Coffee, Tea & more, Food), landmarks (banner, navigation "Main", main, footer) and links with meaningful names. In Chrome the rotor did not list the headings, so VoiceOver has to be tested in Safari.

**Zoom 200 %:** contact.html in Chrome at 200 %. All text stays readable and nothing overlaps. Because of the fixed 1100 px layout the nav is cut off on the right and needs horizontal scrolling (allowed for EPA 2, responsive layout is EPA 3).

## C4 · Peer test

**Tester:** Malsor (classmate), 15.11.2026, on the live pages with Narrator (Windows). Filled-in course peer test sheet: `peer-test/peer-test-protocol-malsor.pdf`.

**Tested:** keyboard (skip link, Tab reach, visible focus, order), screen reader (headings, landmarks, link names, images, form labels and "required"), zoom 200 %, WAVE and the W3C validator on both pages.

**Found:** all checks passed. WAVE showed 0 errors and 0 contrast errors and the validator showed 0 errors on both pages. Narrator read the form labels and "required", and today's special was read as text. One minor finding on both pages: at 200 % zoom the page is wider than the window, so you have to scroll sideways (1.4.10 Reflow, severity M).

**Changed afterwards:** nothing. The sideways scrolling comes from the fixed 1100 px layout, which the brief allows for EPA 2. Responsive layout is EPA 3, so I will fix 1.4.10 there. I had already noted the same thing in C3. Narrator on Windows also confirmed the VoiceOver result from C3 with a second screen reader.

## C5 · Limits of automated tools

Automated tools only check what can be measured in the code, not whether the result makes sense to a person. Lighthouse gave both pages 100. It still cannot tell whether `alt=""` on the special image is the right choice, whether the heading texts are meaningful, or whether a screen reader user can actually find today's special. The VoiceOver test showed that this depends on the browser too. No tool flagged the privacy problems on contact.html: the Google Maps iframe loading before consent, personal data in the URL with `method="get"`, and the unnecessary birthday field. Tools can also disagree. On menu.html, WAVE reported nav contrast errors that only appeared because its own icons pushed the nav off the dark header, while Lighthouse reported none.

## Use of AI

I used Claude (AI) to explain WCAG criteria, review my changes, run the validator and Lighthouse, and draft this protocol from my notes. I typed most changes myself. Claude applied some directly: it copied the header and footer from my menu.html into contact.html, removed duplicate lines left after my pastes, and finished two CSS lines. I can explain every change.
