# Repository guidance

## Project overview

This is Thomas Caskey's static portfolio: an interactive pixel-art Amsterdam canal at night. It uses plain HTML, CSS, JavaScript, and JSON, with no framework, build step, or package manifest.

- `index.html` contains the canvas scene, styles, content loader, card rendering, and routing.
- `404.html` redirects GitHub Pages card URLs back to the entry page with a `?p=slug` parameter.
- `data/projects.json` contains the eight project cards in house order, left to right.
- `data/about.json` contains the professional About Me content shown by the houseboat.
- `data/personal.json` contains the personal About Me content shown by the kiwi statue.
- `data/contact.json` contains the contact content shown by the clock tower.
- `README.md` documents content fields, local previews, and deployment behavior.

## Content changes

Edit the JSON files for portfolio copy, facts, skills, experience, photos, and links. Keep content out of JavaScript data blocks. Preserve existing information and placeholders unless the request changes them; do not invent professional claims, dates, results, or contact details.

Use UTF-8, two-space indentation, double quotes, and valid JSON without comments or trailing commas. Keep list fields present; use `[]` for an empty list.

The current loader requires exactly eight projects, matching the eight houses. Replace the first "Coming soon" entry when filling the unused slot. Changing the number of projects also requires updating the scene, its house mapping, and the loader's count validation.

Preserve existing project slugs to keep shared links working. New slugs must be unique lowercase letters, numbers, and hyphens; `about`, `personal`, and `contact` are reserved. A project's `label` is its short house label, separate from its card `title`.

List formats:

| Field | Entry format |
| --- | --- |
| `bio`, `stack`, `skills`, `interests` | Strings |
| `facts` | `["Label", "Value"]` |
| `experience` | `["Date range", "Role", "Company"]` |
| `photos` | `["Image path or URL", "Caption"]` |
| `links` | `["Button label", "URL"]` |
| Contact `rows` | `["Label", "Visible text", "Link"]` |

The first card link is the primary button. A `"#"` URL is an inactive placeholder; an empty contact link is plain text. Contact `mailto:` rows add an email Copy button. Personal photo paths are relative to the page directory, and an empty path keeps a placeholder frame. Set `placeholder` to `false` when a card's placeholder content is ready.

When adding or changing content fields, update the loader validation, card rendering, relevant JSON files, and README together.

## Implementation changes

Follow the existing plain JavaScript and CSS style and keep changes focused. Avoid adding frameworks, dependencies, or a build pipeline for routine work.

Preserve the canvas scene's pixel-art appearance and its 640×360 drawing coordinates with crisp scaling. Keep house indexes aligned with project entries and keep the professional, personal, and contact scene objects distinct from projects.

Preserve keyboard navigation, dialog focus handling, close behavior, responsive canal panning, reduced-motion support, and scene shortcuts. Render JSON copy as text with `textContent` rather than inserting it as HTML.

Keep JSON loading relative to the page directory so both root hosting and a GitHub Pages project subdirectory work. Preserve clean card URLs, the `404.html` redirect, `?p=slug` entry links, and browser back/forward navigation. Include `data/` when deploying; there is no generated output directory.

## Preview and verification

Use an HTTP server; opening `index.html` through `file://` cannot load the JSON. From the repository root:

```sh
npx --yes http-server . -p 8080 -c-1
```

Open `http://localhost:8080/`. On a local server without the GitHub Pages redirect, use `/?p=sharesies` or `/#sharesies` to open a card directly.

Scale verification to the change:

- For content edits, parse the edited JSON and check the affected card in the browser.
- For loader or schema changes, check successful loading and readable errors for missing files, invalid JSON, and invalid list formats.
- For routing changes, check direct entry links, switching and closing cards, back/forward navigation, and hosting under a subdirectory.
- For scene or layout changes, check desktop and narrow screens, keyboard controls, focus, and reduced motion.
- Run `git diff --check` before finishing. Do not introduce a test framework for documentation or simple copy edits.

Report what changed and the checks actually performed. Keep these instructions and README aligned with the implementation when repository conventions change.
