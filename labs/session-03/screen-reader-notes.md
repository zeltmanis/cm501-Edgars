# S3 homework: get to know your screen reader

Task: 10 minutes of VoiceOver (Mac, Cmd+F5) or NVDA (Windows): headings, landmarks, links list.
Then read MDN "HTML: A good basis for accessibility" (15 min).

## VoiceOver keys used
| Action | Keys |
|---|---|
| Turn on/off | Cmd+F5 |
| Rotor (headings, landmarks, links lists) | VO+U, then Left/Right to switch list |
| Next heading | VO+Cmd+H |
| Read next item | VO+Right |
| Click / activate | VO+Space |

VO = Ctrl+Option.

## My run
Page tested: my repaired EPA 2 menu page, https://zeltmanis.github.io/cm501-Edgars/epa2-campus-cafe/menu.html (VoiceOver + Safari) · Date: 2026-11-15

| List | What I found | Was it useful? |
|---|---|---|
| Headings | Menu (h1), Today's special, Coffee, Tea & more, Food (h2) | Yes: the fastest way to jump to a menu section |
| Landmarks | banner, navigation "Main", main, footer (contentinfo) | Yes for the page frame; the menu sections are not landmarks (a plain `<section>` needs a name to count) |
| Links | Skip to main content, Menu, Contact, Campus Café on Facebook, Campus Café on Instagram | Yes: every link name makes sense on its own, the icon links read their hidden text |

What surprised me:

- Moving with Tab (or the Links list) jumps from Menu and Contact straight to the footer and skips the whole menu. Tab only reaches things you can click; screen reader users reach the content through the Headings list or VO+Right.
- First try was in Chrome: the rotor's Headings list did not show the menu headings. In Safari all five appeared. VoiceOver is built for Safari (NVDA pairs with Firefox/Chrome), so test with the matching browser.
- So without real headings the menu would be almost unreachable quickly. The `<h2>`s I added in the repair are what make it navigable.

## MDN: three things I took away

1. Use the correct HTML elements: semantic HTML (`<button>`, `<nav>`, `<header>`) instead of generic `<div>`s.
2. Make content understandable: clear headings, simple language, descriptive links, image alt text and labelled forms.
3. Support everyone: keyboard navigation, screen readers, a logical page structure and accessible tables.

Main idea: build accessibility into the HTML from the beginning, not as an afterthought.
