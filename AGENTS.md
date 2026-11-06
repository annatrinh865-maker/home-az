# AGENTS.md — instructions for AI coding agents and collaborators

This repository is the static portfolio site **Home, A–Z — A Dictionary of Home** (a 30-day poster project).
It is already a working site. Your job is to continue it, not to redesign it.

## Read in this order

1. `README.md` — folder map, how to preview, how to deploy to GitHub Pages.
2. `handoff/DESIGN_SPEC.md` — design tokens, page layouts, components, copy, known issues.
3. `handoff/previews/*.jpg` — what each page should look like (1440 px desktop).
4. `index.html`, `dictionary.html`, `about.html`, `css/style.css` — the current implementation.
5. `content/entries.json` — the dictionary entries and chapter text as data.

## Hard rules

- **Keep it a plain static site.** HTML + CSS, no framework, no build step, no package manager. It must work when `index.html` is opened directly and on GitHub Pages under a sub-path (`/<repo>/`), so use **relative paths only**.
- **Keep the visual style.** Palette, thick black borders, irregular rounded corners, hard offset shadows, paper textures and the three fonts are the identity of the project. Do not swap in a different look. Details: `handoff/DESIGN_SPEC.md`.
- **Do not invent personal facts.** Anything in `[YOUR …]` brackets is a placeholder for information the owner has not provided yet (name, email, Instagram, portfolio link, photo, personal note). Leave the brackets in place until the owner gives the real value. Do not make up links, dates, awards or biography.
- **Do not rewrite the dictionary copy or the poster images** unless asked. The 10 entries (`content/entries.json`) and the poster files are the owner's content. Do not edit, crop, recolor or re-encode files in `images/posters/`; if a different size is needed, make a copy with a new name. The full-size poster originals are not in this repository (they were left out to keep the package small); ask the owner if you need them.
- **Keep text readable.** Body text must be `#111` on blue, yellow, green, pink and cream. On red, only large bold text (24 px and up) may be cream; put smaller text inside a cream or colored card. Keep `alt` text on every `<img>`.
- **Keep all three pages in sync.** The nav, footer and the CSS classes (`t-red`, `t-blue`, `t-yellow`, `t-green`, `t-pink`, `t-cream`, `sticker`, `btn`) are shared by every page.

## Working with the owner

- The owner is a design student who wants to **discuss before anything is built** and then confirm step by step. For any new design direction, propose first and wait for a yes.
- When something looks wrong, **list the possible causes and what could be changed**, and ask what feels off. Do not change many things at once.
- Separate **observable problems** (contrast, alignment, overflow) from **taste**, and say which one a suggestion is. Do not call a style bad just because another style is more common.
- If you have questions, **ask them all in one message**.
- When you tell the owner to change a setting in any tool, name the exact menu, tab and field.

## Suggested next tasks (ask before starting any of them)

1. Replace the `[YOUR …]` placeholders once the owner provides real values (see the table in `README.md`).
2. Add the remaining poster days to the 30-day grid in `dictionary.html` and, if wanted, new dictionary entries.
3. Move the repeated inline `style="…"` attributes into named classes in `css/style.css` (the markup came out of a design tool and is verbose). The rendered result must not change.
4. Add a mobile layout (the pages currently only wrap; they were designed for 1440 px desktop).
5. Replace the mirror-tiled paper textures (they show a visible symmetric pattern in large green/blue areas) with less repetitive paper, if the owner agrees.

## Acceptance checklist before you hand back

- [ ] Every page opens from `file://` and from `python3 -m http.server`, with no broken images and no 404s in the browser console.
- [ ] All links work between `index.html`, `dictionary.html` and `about.html`, and the current page is highlighted in the nav.
- [ ] No unexpected text overflow or clipped content at 1440 px width.
- [ ] Placeholders are either still in `[YOUR …]` form or replaced with values the owner gave you.
- [ ] You listed what you changed, in plain words, and what you left alone.
