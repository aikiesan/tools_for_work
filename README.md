# Tools for Work

A curated reference of tools that help our work, mostly ones that give Claude (and us) something it can't do well on its own: real assets, design judgement, data and specialised workflows.

Each entry says what the tool is, how it helps, how to use it, and anything to watch out for.

## Contents

- [Media and assets](#media-and-assets)
  - [Openverse](#openverse)
- [Design and UI](#design-and-ui)
  - [unslop](#unslop)

---

## Media and assets

### Openverse

**Link:** <https://openverse.org> · **Type:** Search engine and API · **Cost:** Free · **Tags:** `audio` `images` `sound-effects` `music` `video-editing`

A search engine for openly licensed media (Creative Commons and public domain), covering both images and audio: sound effects, whooshes, hits and music tracks.

**Why it helps:** Claude can't listen to an edit, so when it picks sounds for a video it is guessing. Openverse gives it a large library of real, licensed sounds to choose from and cite, instead of paying for sound packs.

**How to use:**
- Search on the site and use the license filters (for example "use commercially" and "modify or adapt") to keep only what we can publish.
- There is also a public API (<https://api.openverse.org>) that Claude can query directly to find and fetch candidates.

**Watch out:** Licenses vary per file. Check each one before posting and add the attribution that CC BY and similar licenses require.

---

## Design and UI

### unslop

**Link:** <https://github.com/heydamir/unslop> · **Type:** Claude Code skill (plugin) · **Cost:** Free (CC BY 4.0) · **Tags:** `web-design` `ui` `claude-skill` `frontend`

A skill for Claude Code (also Codex and Google Antigravity) that turns AI-looking, "vibecoded" UI into a designed interface. It first finds the tells (purple gradients, glows, emoji labels, shouty copy, uneven spacing), then sets a direction from the product and fixes the screen pass by pass, like a designer's redline review.

**Why it helps:** Visitors spot generic AI sites quickly. This keeps the existing site and its stack (Next.js, React, Vue, Svelte, Tailwind or plain HTML/CSS) and gives it its own character. It works on dashboards, apps, landing pages and even a live site from its link.

**How to use:**

```bash
claude plugin install unslop --marketplace heydamir/unslop
```

On an older Claude Code: `claude plugin marketplace add heydamir/unslop` then `claude plugin install unslop@heydamir`. Start a new session (or `/reload-plugins`) and run `/unslop`.

**Watch out:** Snapshotting a live site or making a "story" video needs Playwright and its Chromium browser installed in the project. See the repo README.

---

## Adding a tool

Copy this block into the right section (or create a new section and add it to [Contents](#contents)):

```markdown
### Tool name

**Link:** <url> · **Type:** website / API / skill / CLI / library · **Cost:** free / paid / freemium · **Tags:** `tag1` `tag2`

One or two sentences on what it is.

**Why it helps:** the problem it solves for us.

**How to use:** install command or first steps.

**Watch out:** licenses, limits, costs, gotchas.
```
