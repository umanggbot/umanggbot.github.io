# FATHOM — project notes for Claude Code

## What this is
An independent finance-journalism site: **FATHOM — "Finance, made legible."**
Plain-English explainers on markets, macro, and personal money, written for
people who were never handed the glossary.

Owner/editor: Umang. She is not a developer — explain changes in plain
English, never assume terminal or code fluency, and do the work rather than
handing over instructions.

## Structure — read this before editing
The entire site is **one self-contained file: `index.html`.**
No build step, no npm, no framework, no dependencies to install.
CSS and JavaScript live inline in that one file.

Only two external things load from the internet: Google Fonts (Fraunces,
Inter, JetBrains Mono) and three.js r128 from cdnjs, used for the particle
background on the hero.

**Keep it one file.** Do not split it into separate .css/.js files, do not
add a bundler, and do not introduce a framework. The single-file design is
deliberate — it's what makes this site editable and deployable by one person.

## Where to make changes
Nearly everything the editor would want to change lives in a numbered block
at the top of the `<script>` tag near the bottom of the file:

1. **`CONFIG`** — brand name, tagline, eyebrow, headline, sub-headline, about
   text, accent colours (`accent` gold, `accent2` green), contact email,
   admin password fingerprint, AI proxy URL
2. **`RSS_FEEDS`** — live newsletter feeds; empty right now
3. **`SAMPLE_STORIES`** — the six placeholder stories shown while no feed is
   connected
4. **`TICKER`** — the scrolling market numbers (illustrative, not live data)
5. **`GLOSSARY`** + `DECODER_PICKS` — the finance dictionary; powers both the
   public "Decoder" cards and the site's built-in chatbot

Prefer editing these blocks over editing the HTML body or CSS directly. The
page reads from them on load.

## Known placeholders (not yet real)
- Contact email is still `hello@example.com` in `CONFIG.contact`
- `RSS_FEEDS` is empty, so "The Latest" shows `SAMPLE_STORIES`
- Ticker numbers are illustrative, not a live market feed
- `AI_PROXY_URL` is empty, so the on-site chatbot runs its offline
  "Local Brain" fallback rather than real Claude

## Admin studio
Hidden editor panel, reachable three ways: the small "✦ Studio" link in the
footer, adding `#admin` to the URL, or Ctrl/Cmd+Shift+A.

The password is not stored in the file — only its SHA-256 fingerprint, in
`CONFIG.adminPassHash`. Never write a plaintext password into this repo.
Note that studio edits save to the visitor's own browser (localStorage) only;
changes that should be permanent for all visitors must be committed to
`CONFIG` in this file.

## Testing a change
Open `index.html` in a browser and hard-refresh (Cmd+Shift+R). That's the
whole test loop. Always check the site still renders before committing —
because this is one file, a JavaScript syntax error can blank the page.

Check both a wide window and a narrow one; the layout is responsive.

## Deploying
Hosted on GitHub Pages from the `main` branch. Deployment is just:

```
git add -A && git commit -m "describe the change" && git push
```

The live site updates about a minute later. There is no other deploy step.

## Working style
- Make one change at a time and confirm it worked before moving on.
- Say what changed in plain English, not in diffs, unless asked.
- Never commit secrets, API keys, or plaintext passwords.
