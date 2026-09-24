# Wedding Seating Plan: Find Your Table

A single-page, mobile-first seating plan. Guests enter their table number
(1–20, VIP 1, VIP 2) and the ballroom map zooms to and highlights their table.

Plain HTML, CSS and JavaScript. No build step, no backend, no database,
no login, no cookies, no analytics, and no guest data collected or stored.

## Files

| File                   | Purpose                                              |
|------------------------|------------------------------------------------------|
| `index.html`           | The whole app (CSS, JS and the SVG floor plan inline) |
| `favicon.svg`          | Browser tab icon                                     |
| `favicon-32.png`       | Fallback tab icon                                    |
| `apple-touch-icon.png` | Icon when a guest adds the page to their home screen |
| `robots.txt`           | Asks search engines not to index the site            |
| `netlify.toml`         | Netlify headers and caching (ignored elsewhere)      |
| `vercel.json`          | Vercel headers and caching (ignored elsewhere)       |
| `.nojekyll`            | Makes GitHub Pages serve files as-is                 |

All paths are relative, so the site works at a domain root or in a subfolder
(e.g. `username.github.io/seating/`).

## Deploy

### Netlify (easiest)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You get a public URL straight away. Rename it under
   Site settings → Change site name, for example `ourwedding-seating.netlify.app`.

### Vercel
1. Put this folder in a GitHub repository (or run `npx vercel` inside it).
2. In Vercel: Add New → Project → import the repo.
   Framework preset: "Other". Leave the build command empty and the output directory as `.`
3. Deploy.

### GitHub Pages
1. Create a repository and upload all the files, including `.nojekyll`,
   to the root of the `main` branch.
2. Go to Settings → Pages → Source: "Deploy from a branch" → `main` / `(root)`.
3. The site appears at `https://<username>.github.io/<repo>/` within a minute or two.

## Linking from WooowInvites

Link to the site URL, for example:

    https://ourwedding-seating.netlify.app/

You can also link straight to a specific table. The page opens already zoomed
in on it:

    https://ourwedding-seating.netlify.app/?table=12
    https://ourwedding-seating.netlify.app/?table=VIP%201

The URL updates as guests search, so refreshing the page or sharing the link
keeps their table highlighted.

## Editing tables

Table positions live in the `TABLES` list near the top of the `<script>` in
`index.html`:

    { id:"table-12", n:"12", cx:810, cy:592 },

`cx` and `cy` are positions on a 1200 × 1320 map (the stage is at the top and the entrance at the bottom).
To add a table, copy a line and change the `id`, `n`, `cx` and `cy` values.

Note: tables 4 and 14 are not on the supplied floor plan, so they are not on the map yet.
Searching for them shows the "couldn't find that table" message.

## Privacy notes

- **Search engines:** the page tells them not to index it (`noindex` meta tag, header and `robots.txt`).
  Anyone who has the link can still open it.
- **Google Fonts:** fonts load from Google, which receives a visitor's IP address like any web request.
  To avoid this, download Instrument Serif and Geist from Google Fonts, add the files to the folder,
  and replace the `<link href="https://fonts.googleapis.com/...">` line with local `@font-face` rules.
  If the fonts ever fail to load, the page falls back to system fonts and still works.
