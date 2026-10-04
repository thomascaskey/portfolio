# portfolio

A portfolio of my work 📱 — an interactive pixel-art Amsterdam canal at night.

- Each of the 8 canal houses opens a project card and has a shopfront for its app: RNZ record shop, 2degrees phone shop, TVNZ newsagent, Co-operative Bank, Drive Go garage, Sharesies exchange (after the Beurs van Berlage) and the Goodnotes school past the bridge.
- The houseboat is the professional About Me, the kiwi statue the personal one, and the clock tower has contact details.

## Preview locally

Serve this directory with an HTTP server, for example:

```sh
npx --yes http-server . -p 8080 -c-1
```

Open [localhost:8080](http://localhost:8080). Opening `index.html` directly as a file cannot load the JSON because of browser restrictions. The deployed site loads the same files without any build step.

## Edit content

All card content lives in `data/`; edit a JSON file, save it, and refresh the browser. Content is fetched on each page load without using the browser's cached copy.

| File | Content |
| --- | --- |
| `data/projects.json` | Project cards, ordered by canal house from left to right |
| `data/about.json` | Professional biography, facts, skills, experience, and links |
| `data/personal.json` | Personal biography, photos, facts, interests, and links |
| `data/contact.json` | Contact details and closing note |

Use double quotes and no comments or trailing commas. Arrays can contain as many paragraphs, skills, facts, experience entries, photos, or links as you need. Use `[]` to empty a list. The page shows a loading error if a file is missing, invalid JSON, or has an invalid list format.

### Projects

Each project has `title`, `label` (short house label), `slug` (URL), `kind`, `year`, `accent` (CSS color), `tagline`, `summary`, `role`, `platform`, `stack`, `links`, and `placeholder`.

There are eight houses and eight project entries. Replace the first "Coming soon" entry to feature another project, keeping its position in the array. Adding more than eight projects requires extending the canal scene in `index.html`. Set `placeholder` to `false` when its content is ready.

Keep slugs unique, using lowercase letters, numbers, and hyphens. `about`, `personal`, and `contact` are reserved. Keep an existing slug to preserve shared links. Link entries are `["Button label", "URL"]`; the first link is the primary button. A URL of `"#"` creates an inactive placeholder button.

```json
"stack": ["Swift", "SwiftUI", "Accessibility"],
"links": [
  ["App Store", "https://apps.apple.com/example"],
  ["Case study", "https://example.com/project"]
]
```

This is a fragment to copy into a project object, not a complete JSON file.

### About and personal

`about.json` contains `name`, `greeting`, `role`, `tagline`, `bio`, `facts`, `skills`, `experience`, `links`, and `accent`. `personal.json` contains `title`, `tagline`, `bio`, `photos`, `facts`, `interests`, `links`, `accent`, and `placeholder`.

- `bio`: an array of paragraph strings.
- `facts`: `["Label", "Value"]` pairs.
- `skills` / `interests`: arrays of strings.
- `experience`: `["Date range", "Role", "Company"]` entries.
- `photos`: `["Image URL or path", "Caption"]` pairs. An empty image path keeps a placeholder frame. Local paths, such as `photos/amsterdam.jpg`, are relative to the page directory; add the image there too.
- `links`: `["Button label", "URL"]` pairs.
- `placeholder`: set to `false` to hide the editing reminder (optional for professional About Me).

### Contact

`contact.json` contains `title`, `tagline`, `rows`, `note`, and `accent`. Each row is `["Label", "Visible text", "Link"]`:

```json
"rows": [
  ["Email", "you@example.com", "mailto:you@example.com"],
  ["Location", "Amsterdam, Netherlands", ""],
  ["LinkedIn", "Your profile", "https://www.linkedin.com/in/your-profile/"]
]
```

A `mailto:` link adds a Copy button and an Email me button. An empty link is plain text; `"#"` makes a grey placeholder row. Use an empty `note` to hide the closing note.

## Links

Every card has its own address: `/rnz`, `/2degrees`, `/tvnz`, `/co-operative-bank`, `/drive-go`, `/sharesies`, `/goodnotes`, `/coming-soon-1`, plus `/about`, `/personal` and `/contact`. Opening a link opens that card, and opening, switching or closing cards updates the address, so the back button works. On GitHub Pages, `404.html` sends a direct visit like `/portfolio/sharesies` back to the page. Include the `data/` directory when deploying. Local servers without the GitHub Pages redirect can open cards using `/?p=sharesies` or `/#sharesies`.
