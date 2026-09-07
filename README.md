# Terminal Value

**[umanggbot.github.io](https://umanggbot.github.io)** — *What it's worth when the noise stops.*

An independent column on markets, money and the companies quietly running your
life. About 1,800 words, twice a week. Written and edited by Umang.

Seventeen pieces, July–August 2026 — [the archive](https://umanggbot.github.io/archive.html) ·
[RSS](https://umanggbot.github.io/feed.xml)

---

This repository is the published site. It is hand-written HTML with inline CSS
and JavaScript — no framework, no bundler, nothing to install — plus one page
per piece under `/p/`, generated from markdown masters that live outside this
repo.

```
index.html          the front page, including the earnings simulator
archive.html        the archive, with a reader and full-text search
p/<slug>/           one page per piece — the prose is in the HTML source
data/archive.json   every piece, the file both pages read
feed.xml            RSS, full text
admin/              the writing desk (Decap CMS, GitHub sign-in)
```

Two things worth knowing if you're reading the source. Nothing invented ever
renders: the market ticker hides a data source rather than show a stale number,
the archive shows an honest empty state, and the contact link stays hidden until
there's an inbox behind it. And the earnings simulator is labelled a teaching
model, not a forecast — its weights are illustrative and deliberately simple.
