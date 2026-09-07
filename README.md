# Future Links

Built by **[Jack Abraham](https://jackabraham.studio)** — [GitHub](https://github.com/Jackalackalack) · [LinkedIn](https://www.linkedin.com/in/jackcabraham/)

A one-page, tag-searchable index of links for a music-business course. Drawn as a blueprint: every link is a "sheet" in the index, tagged with one or more topics, and each sheet lists which other sheets it connects to by shared tag.

**This repo is a static mirror.** The live, editable version lives on Claude — search, tag filtering and "connected sheets" all work here exactly the same, but the Submit flow that adds new links only works on the Claude-hosted copy, since it depends on Claude's own publish capability. This page detects that it's running outside Claude and disables Submit accordingly, with a message pointing back to the live version.

## Workflow

1. Add and edit links on the live Claude version.
2. When you want this static copy to catch up, ask Claude for the current `index.html` and replace this repo's copy with it (or hand Claude this repo directly and ask it to update the file).
3. Commit and push — GitHub Pages redeploys automatically.

## What it does

1. Search — a query box filters every link by title, note, URL and tags at once (matches all your words anywhere in a link, not just an exact phrase).
2. Filter by tag — click any tag in the legend to narrow the index; click again to clear it.
3. Connected sheets — each link card lists the other links that share at least one tag, so students can follow a thread across the collection.
4. Full archive — the front page starts as a search/browse prompt rather than a full list; "See full archive" reveals everything at once for anyone who wants to scroll instead of search.

## How it's built

A single self-contained HTML file (`index.html`):

- All data (tags + links) lives in one `STATE` object embedded in the page's own script.
- The page renders itself from `STATE` on load and after every interaction — no backend, no build step.
- On Claude, saving calls the page's own publish capability to write a new version of itself, so the update is live for every open viewer immediately. Outside Claude, that capability isn't present, so the page falls back to a read-only static view.
- Styling is a hand-drawn "blueprint" theme: graph-paper grid, ruler edges, registration marks, and cards framed like technical-drawing insets.

## Running it locally

Open `index.html` directly in a browser, or serve the folder with any static file server. Search, tag filtering and "connected sheets" all work offline; Submit will show a message explaining it's read-only here.

## Deploying to GitHub Pages

1. Push this repo to GitHub:
   ```
   git init
   git remote add origin https://github.com/Jackalackalack/future-links.git
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git push -u origin main
   ```
2. In the repo's **Settings → Pages**, set the source branch to `main` and the folder to `/ (root)`.
3. Your site will be live at `https://jackalackalack.github.io/future-links/` (or your chosen repo name) within a minute or two. Add a custom domain in the same Settings → Pages screen if you want it under `jackabraham.studio` instead.

GitHub requires a personal access token as the password over HTTPS, not your account password, when `git push` asks you to authenticate.

## License

MIT — see [LICENSE](LICENSE). Free to use, modify and share, including for teaching; just keep the copyright notice attached to any copies.
