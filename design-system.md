# Case study design system

One set of tokens, used by every page (index, about and the four case studies). Each page is still self-contained: the same `/* ===== DS ===== */` block is pasted at the end of every page's `<style>`. Change a value there, then paste the block into the other three pages.

## Type scale (Albert Sans)

| Token | Value | Used for |
|---|---|---|
| --fs-h1 | 34 to 48px | Page title and the result number (max 22ch wide, 1.12 line height) |
| --fs-h2 | 26 to 32px | Section titles, with 01/02 eyebrow |
| --fs-h3 | 22px | Sub-sections inside a section |
| --fs-lead | 18 to 20px | Subtitle, result line, quote text |
| --fs-callout | 20 to 22px | Pulled-out decision lines (3px bar) |
| --fs-stat | 48px | Numbers in stat rows and result callouts |
| --fs-body | 18px / 1.65 | All paragraphs and lists (case studies and About) |
| --fs-ui | 16px | Fact values, stat labels, role names, footer label |
| --fs-small | 14px | Nav, captions, chips, card descriptions, back link |
| --fs-label | 12px caps | Fact labels, section numbers |

## Spacing (8-based scale, 8 / 16 / 24 / 32 / 40 / 48 / 64 / 96)
| Token | Value | Used for |
|---|---|---|
| --space-xs | 8px | Label to heading, caption to figure, list-item gaps |
| --space-s | 16px | Heading to its content, logo to subtitle |
| --space-m | 24px | Paragraph to paragraph, header stack |
| --space-l | 32px | Subtitle to facts, stat row top |
| --space-block | 40px (32 on phones) | Around callouts, quotes, figures, stat rows |
| --space-lead | 48px (40 on phones) | Hero to result, result to first section, sub-section (H3) top |
| --space-xl | 64px (48 on phones) | Top of Home |
| --space-section | 96px (72 on phones) | Between numbered sections |

Rules, checked against common layout practice:
- Proximity: gaps inside a group are always smaller than gaps between groups (caption 8, heading to text 16, paragraph 24, block 40, section 96).
- A heading sits closer to the text it introduces than to what came before it (96 above an H2, 16 below).
- The result block belongs to the hero, so it gets the 48px lead-in, not the 96px section gap.
- Every vertical gap on the site is one of the scale values. If you measure something else, it's a bug.
- Text column 680, image breakout 900, stat row 1000.

## Quotes (people other than me)
A quote is a card, not text: white surface, 1px --line border, 12px radius, 24px 32px padding (24px on phones), 40px (32 on phones) above and below. Inside: a curly opening mark (&ldquo;) in --accent-text at H2 size, the quote at --fs-lead in regular weight, 16px gap, then the source in 14px --ink-soft. There is no --fs-quote token any more.

How the three "voices" stay apart:
- Bare callout (3px bar): my narrative claim.
- Sparkle + label block: cited evidence, a stat or outcome.
- Quote card: someone else's words.
Never put a quote inside a callout, or style a callout like a quote.

## Color
- Text: --ink #1a1a1a, --ink-soft #5c5c5c (captions, subtitles). --muted #9a9a9a is for rules only, never text (2.46:1).
- Numbers and eyebrows use --accent-text, a per-page shade that passes 4.5:1 on the cream background.
- Callout bars and dots use --bar, the case-study color.

| Case study | --bar | --accent-text (light) | --accent-text (dark) |
|---|---|---|---|
| QBS | #4D56F2 | #4D56F2 (4.68:1) | #8d94ff |
| Client Portal | #FCB07F | #A24A0B (5.22:1) | #FCB07F |
| Magpie | #17D4E6 | #0A747E (4.82:1) | #17D4E6 |
| Bro'd Trip | #AC5BF7 | #8A3FD6 (4.89:1) | #C08CFB |

## Page anatomy (same order every time)
1. Back link (small, above the logo)
2. Logo, then H1, then lead subtitle
3. Facts strip: Company (or Project), Role, Timeline, Focus
4. Hero panel in the case color
5. Result block (label, display number, one line)
6. Numbered sections: H2, body, at most one callout per section, figures with a 14px caption
7. Stat row for results, then Reflection (one callout, the sentence that carries the decision)

## Rules
- One callout per idea. Pull the sentence out of the paragraph, don't repeat it.
- Callout rule: a sparkle plus label marks cited evidence only (a result, a proof point, field validation). A bare callout (3px bar, no sparkle, no label) is narrative voice. Never combine them.
- Captions describe what the figure is; never alt text.
- No tag pills. Domain and focus live in the facts strip.
- Never use opacity to dim text; use --ink-soft.

## Site-wide
- Home and About use the same H1 token as the case studies. Card titles use H3 (22px). Wordmark is body size (18px).
- Nothing on the site sits between steps of the scale: 12, 14, 16, 18, 20, 22, 24, 32, 48. If a size isn't on that list, it's a bug.
