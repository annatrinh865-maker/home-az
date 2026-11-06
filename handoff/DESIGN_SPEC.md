# Design spec — Home, A–Z

Everything here describes the site as it exists in this repository. Pixel values are for the 1440 px desktop layout.
Reference images: `handoff/previews/`. Those previews were rendered with substitute fonts (Inter and Poppins); the real site loads the fonts listed below.

## 1. Concept

- **Project:** a 30-day poster project. Each poster becomes an entry in **a dictionary that tries to define "home"**.
- **Site name:** Home, A–Z. **Headline:** A Dictionary of Home.
- **Audience:** the design community and anyone interested in the topic, browsing as a portfolio.
- **Language:** English.
- **Platform:** desktop first (1440 px). Layout uses flex-wrap so narrow screens stack, but there is no dedicated mobile design.
- **Owner:** Communication Design student, Department of Communication Design, Shih Chien University (Taiwan).
- **Poster source:** the owner's own posters, in four chapters:

| Chapter | Day | Posters | Idea |
| --- | --- | --- | --- |
| 01 Remembered | 9 | 5 child-style crayon drawings on colored crumpled paper (house, family, bed, TV show, clothes) | home as remembered by a child |
| 02 Address | 10 | 2 type-led posters ("Where? Where?" with Everywhere/Nowhere, and "Your Address") | home as a question with no address |
| 03 Body | 11 | 1 poster, a person inside a house made of flesh-colored pipes | home is part of me |
| 04 Shell | 12 | 7 posters, windows with people/pets set inside shell shapes, over a blue apartment facade | every shell carries a home |

## 2. Sitemap

| File | Title | Purpose |
| --- | --- | --- |
| `index.html` | Home, A–Z — A Dictionary of Home | hero, chapter overview, featured entry, quote, footer |
| `dictionary.html` | The Dictionary — Home, A–Z | project intro, how to read an entry, filter chips (visual only), 10 entries, 30-day grid |
| `about.html` | About — Home, A–Z | introduction, school, what I make, why this project, contact |

Nav (all pages): logo "Home, A–Z" → Home · Dictionary · About · pill "30-Day Poster Project". The current page has a 4 px red underline. There is no JavaScript.

## 3. Design tokens

### Colors

| Name | Hex | Used for | Text on it |
| --- | --- | --- | --- |
| Red | `#E8170F` | hero button, marquee, featured and entries sections, contact section | cream `#FDF1E0`, **large bold text only** |
| Blue | `#3F95F0` | hero, entry cards, chapter card, school card | ink `#111` |
| Yellow | `#FFD60A` | nav bar, buttons, quote section, entry cards | ink |
| Green | `#55BE5E` | chapters section, About hero, entry cards | ink |
| Pink | `#F78FB8` | project header, entry cards, skills card | ink |
| Cream | `#FDF1E0` | page background, cards, number badges | ink |
| Ink | `#111111` | all outlines, shadows, text, footer background | cream (in the footer) |

The five colors come from the child-drawing posters (Day 9). Cream is the door/window color of the red house drawing.
Section backgrounds use the classes `t-red`, `t-blue`, `t-yellow`, `t-green`, `t-pink` (paper texture + base color + default text color) and `t-cream` (flat cream).

### Typography (Google Fonts)

| Role | Font | Size / weight | Where |
| --- | --- | --- | --- |
| Display | **Archivo Black** | 96–120 px headline (line-height .95–.98), 64 px section titles, 52 px entry words, 104 px featured word, 22 px buttons | headings, buttons, logo-adjacent text |
| Hand | **Gochi Hand** | 22–30 px labels, 42 px logo text, 68 px quote | labels ("what's inside"), pronunciation, pills, the quote |
| Body | **Space Grotesk** 400 / 500 / 700 | 18–24 px, line-height 1.4–1.55 | paragraphs, definitions, nav |

Headline treatment `.sticker`: cream text with a hard black outline built from 8 `text-shadow` offsets (3–4 px). Used for the hero H1, "The Dictionary", About H1 and "Say hello."

### Shape, borders, shadows

- Borders: **3–4 px solid #111** on every card, button, pill and image.
- Corners: deliberately **irregular, hand-drawn** radii, e.g. cards `22px 30px 20px 34px / 30px 20px 32px 22px`, big cards `26px 36px 24px 40px / 36px 24px 38px 26px`, buttons `26px 16px 28px 14px / 16px 28px 14px 26px`. Pills use `30px`, number badges are circles.
- Shadows: hard offset, no blur: `6px 6px 0 #111` (buttons, contact pills), `8px 8px 0 #111` (cards, posters), `10–12px` for large cards.
- Tilt: a few elements are rotated 2–6° (hero posters, featured poster, "how to read an entry" card, photo frame).
- Button hover: color becomes ink and the button moves 2 px down-right (`.btn:hover`).

### Paper texture

- Each texture is made from the empty bottom margin of a Day 9 poster (the colored crumpled paper), **mirror-tiled** into a 2120 px wide image so it repeats without a seam.
- CSS: `background: <base color> url(../images/textures/tex-<color>.jpg) 0 0/1060px auto repeat;` (displayed at half the file size).
- Known side effect: large areas show a faint symmetric diamond pattern.

## 4. Page layouts

All pages are a vertical stack of full-width sections inside `<div style="width:100%;display:flex;flex-direction:column">`. Sections use `min-height`, side padding `80px`, and a `4px solid #111` bottom border. Rendered full-page height at 1440 px: home ≈ 3650 px, dictionary ≈ 4160 px, about ≈ 2850 px.

### Shared

- **Nav** (yellow texture, min-height 96): logo = small red house SVG + "Home, A–Z" (Gochi Hand 42 px) on the left; links and the "30-Day Poster Project" pill on the right.
- **Footer** (ink background, min-height 280, padding 64 80): "Home, A–Z" (Archivo Black 56 px), credit line `A 30-day poster project by [YOUR NAME]`, `Department of Communication Design, Shih Chien University · 2026`, and page links + `[YOUR EMAIL]` on the right.

### index.html — Home

1. **Hero** (blue, min-height 860, padding 80): left column (max 700 px): yellow tilted tag "a 30-day poster project", H1 "A Dictionary of Home" (sticker, 96 px), intro paragraph (24 px), buttons "Open the dictionary →" (red) and "About me" (yellow). Right column (560 × 740, relative): three tilted poster cards 300–320 px wide with 4 px borders (`day09-house` at left 0 / top 40 / −6°, `day09-family` at left 250 / top 0 / +5°, `day12-woman-child` at left 130 / top 330 / −2°) and a yellow round sticker "selected days 9–12" (128 px, +10°).
2. **Marquee** (red texture, min-height 84): static row of words separated by ✶ — home, address, shell, window, nowhere, everywhere, mama, papa, me — Archivo Black 36 px, cropped by the screen edge (`overflow:hidden`, not animated).
3. **Chapters** (green, min-height 950, padding 100 80): label "what's inside", H2 "Four chapters, one word." Then four equal cards (flex, wrap, gap 32, 4:5 poster on top, chapter number in Gochi Hand, title in Archivo Black 30 px, text, "Day N →"): Remembered (pink), Address (yellow), Body (blue), Shell (cream). Each card links to `dictionary.html`.
4. **Featured entry** (red, min-height 800, padding 90 80): tilted poster `day12-woman-cat` (440 × 550, −3°) beside a cream entry card: label "entry of the day · day 12", headword **home** (104 px) with `/hoʊm/ · n.`, three numbered senses (red / blue / yellow circle badges), and "see also" pills (address pink, shell green, window yellow).
5. **Quote** (yellow, min-height 380): "Different shapes. Different stories. Still carrying home wherever they go." in Gochi Hand 68 px, centered, plus link "Read all entries →".
6. **Footer.**

### dictionary.html — The Dictionary

1. **Header** (pink, min-height 560): label "the project", H1 "The Dictionary" (sticker, 120 px), intro paragraph; on the right a cream tilted card (+2°) "how to read an entry" showing a sample entry (shell) with its parts: headword · pronunciation · sense · day · poster.
2. **Filter chips** (cream, min-height 120): "browse by" + chips All entries (selected: ink background), Day 9 · Remembered, Day 10 · Address, Day 11 · Body, Day 12 · Shell. Currently visual only.
3. **Entries** (red, min-height 2320, padding 80): two-column grid (flex-wrap, gap 40) of **10 entry cards**, min-height 400. Each card: colored paper texture, 4 px border, 8 px shadow; left a 236 × 295 poster thumbnail with 3 px border; right headword (Archivo Black 52 px), pronunciation/part of speech (Gochi Hand 24 px), definition (19 px), and a "Day N" pill pinned to the bottom.
4. **The whole month** (cream, min-height 700, padding 90 80): H2 "The whole month" and 30 tiles of 112 × 112 (gap 16), colors cycling red / blue / yellow / green / pink, each showing its day number (Archivo Black 40 px). Days 9–12 show the poster thumbnail with a small yellow day badge in the corner; other days are numbers only (placeholders until those posters exist).
5. **Footer.**

### about.html — About

1. **Hero** (green, min-height 780): left a 440 × 560 cream photo frame with a **dashed** border, tilted −3°, holding a yellow smiley and the text `[YOUR PHOTO]`; right: label "about me", H1 `Hi, I’m [YOUR NAME].` (sticker, 96 px), paragraph, yellow button "See the dictionary →".
2. **School and skills** (cream, min-height 560): blue card "school" — **Shih Chien University** / **Department of Communication Design** / Taiwan · coursework across interactive media, game development, illustration, motion graphics and brand identity; pink card "what I make" — pills: Illustration, Interactive media, Motion graphics, Brand identity, Game development, plus one line of text.
3. **Why this project** (yellow, min-height 640): label "why this project", H2 "Why a dictionary of home?", two paragraphs (the second ends with the `[YOUR OWN NOTE …]` placeholder); on the right three tilted Day 12 posters (`day12-couple`, `day12-dogs`, `day12-man`) in a 560 × 480 stack.
4. **Contact** (red, min-height 420): "Say hello." (sticker, 104 px) and three cream pills: `[YOUR EMAIL]`, `[YOUR INSTAGRAM]`, `[YOUR PORTFOLIO LINK]`.
5. **Footer.**

## 5. Components (quick reference)

| Component | Recipe |
| --- | --- |
| Poster card | `<img>` with `border:4px solid #111`, `box-shadow:8px 8px 0 #111`, `object-fit:cover`, optional rotate |
| Chapter / entry card | texture class (`t-*`) + `padding 20–24px`, `border:4px solid #111`, irregular radius, `box-shadow:8px 8px 0 #111` |
| Button | Archivo Black 22 px, `padding:18px 34px`, border 4 px, irregular radius, `6px 6px 0 #111` shadow |
| Pill / tag | border 3 px, radius 16–30 px, bold 16–22 px, colored fill |
| Number badge | 36 px circle, 3 px border, bold 18 px |
| Day tile | 112 px square, 4 px border, radius `16px 22px 14px 24px / 22px 14px 24px 16px`, `4px 4px 0 #111` shadow |
| Sticker headline | class `sticker` (cream fill + 8-direction black `text-shadow`) |

## 6. Content

- All dictionary entries and chapter text are in `content/entries.json` (the pages currently contain the same text as static HTML; the JSON is not loaded by the pages).
- Entries (in page order): house · family · bed · show · chosen · address · nowhere (also: everywhere) · body · shell · window.

| Headword | Part of speech | Day | Poster file | Card color |
| --- | --- | --- | --- | --- |
| house | n. | 9 | `day09-house.jpg` | blue |
| family | n. | 9 | `day09-family.jpg` | yellow |
| bed | n. | 9 | `day09-bed.jpg` | pink |
| show | n. | 9 | `day09-show.jpg` | green |
| chosen | adj. | 9 | `day09-chosen.jpg` | blue |
| address | n. | 10 | `day10-address.jpg` | yellow |
| nowhere | adv. | 10 | `day10-where.jpg` | pink |
| body | n. | 11 | `day11-body.jpg` | green |
| shell | n. | 12 | `day12-shells-home.jpg` | blue |
| window | n. | 12 | `day12-grandma.jpg` | yellow |

- Posters that appear outside the entry list: `day12-woman-child` (hero collage) and `day12-woman-cat` (featured entry) on the home page; `day12-couple`, `day12-dogs` and `day12-man` on the About page. `day09-house`, `day09-family`, `day10-where`, `day11-body` and `day12-shells-home` also appear as chapter cards and day tiles.
- Tone of the copy: short, concrete, a little poetic; senses are numbered like a real dictionary. Pronunciations are IPA written by hand (check them if accuracy matters).

## 7. Accessibility

- Contrast: ink on blue/yellow/green/pink/cream passes 4.5:1. Cream on red is about 3.9:1, so it is used only for large bold text. Do not put small text directly on red.
- Every poster `<img>` has descriptive `alt` text. Decorative icons and the ✶ separators use `aria-hidden="true"`.
- Links are real `<a href>` elements. The filter chips are plain `<span>`s because they do nothing yet; if they become interactive, make them `<button>`s.

## 8. Fonts, performance and hosting

- Fonts come from Google Fonts (`Archivo Black`, `Gochi Hand`, `Space Grotesk`); the site needs internet for them. Fallbacks are the generic `sans-serif` / `cursive`.
- Poster images in `images/posters/` are 720 × 900 JPEGs (about 75–210 KB each); textures are about 270–480 KB each. The owner keeps the full-size 1080 px originals; they are not part of this package (ask for them if a re-crop or a larger size is needed).
- Hosting: GitHub Pages from the repository root. Paths are relative; there is no build step.

## 9. Known issues and open decisions

1. **Texture symmetry:** the mirror-tiled paper shows a faint diamond pattern in large areas. Option: use unmirrored, larger crops of real paper.
2. **Hand font:** Gochi Hand is a stand-in for the owner's handwriting; the owner may want a more child-like hand font (Patrick Hand was another candidate).
3. **Poster typo:** the Day 10 poster image reads "Adress". The web text spells "address". The owner decides whether to fix the poster itself.
4. **Placeholders:** `[YOUR NAME]`, `[YOUR EMAIL]`, `[YOUR INSTAGRAM]`, `[YOUR PORTFOLIO LINK]`, `[YOUR PHOTO]`, and the personal note on the About page.
5. **30-day grid:** only days 9–12 have posters.
6. **Filter chips** are visual only (they do not filter). The "see also" pills, chapter cards and "Read all entries" link all go to `dictionary.html` without an anchor to a specific entry.
7. **Markup:** inline `style` attributes are repeated across elements (the markup was exported from a design tool). It can be moved into classes without changing the look.
8. **No mobile layout** beyond wrapping. The nav pill, hero collage (fixed 560 px wide) and 4-up chapter cards will need rules if mobile matters.
9. **Marquee** is static and cropped by design; it is not animated.
