# Tools for Work

A curated reference of tools that help our work, mostly ones that give Claude (and us) something it can't do well on its own: real assets, design judgement, data and specialised workflows.

Each entry says what the tool is, how it helps, how to use it, and anything to watch out for.

## Contents

- [Video, audio and media](#video-audio-and-media)
  - [Openverse](#openverse)
  - [Prompt Motion](#prompt-motion)
- [Design and UI](#design-and-ui)
  - [unslop](#unslop)
- [Coding agents and reverse engineering](#coding-agents-and-reverse-engineering)
  - [REA (Reverse Engineer Anything)](#rea-reverse-engineer-anything)
  - [OpenCode](#opencode)

---

## Video, audio and media

### Openverse

**Link:** <https://openverse.org> · **Type:** Search engine and API · **Cost:** Free · **Tags:** `audio` `images` `sound-effects` `music` `video-editing`

A search engine for openly licensed media (Creative Commons and public domain), covering both images and audio: sound effects, whooshes, hits and music tracks.

**Why it helps:** Claude can't listen to an edit, so when it picks sounds for a video it is guessing. Openverse gives it a large library of real, licensed sounds to choose from and cite, instead of paying for sound packs.

**How to use:**
- Search on the site and use the license filters (for example "use commercially" and "modify or adapt") to keep only what we can publish.
- There is also a public API (<https://api.openverse.org>) that Claude can query directly to find and fetch candidates.

**Watch out:** Licenses vary per file. Check each one before posting and add the attribution that CC BY and similar licenses require.

### Prompt Motion

**Link:** <https://prompt-motion.com> · **Type:** Prompt library (website) · **Cost:** Free · **Tags:** `motion-graphics` `animation` `prompts` `claude-skill` `video`

A gallery of motion-graphics videos made with Claude, each shown next to the prompt or skill that produced it, ready to copy. Hundreds of entries, filterable by what you're making: product UI, phone mockups, charts, diagrams, kinetic type, shapes, particles, characters, photos, music and code.

**Why it helps:** The hard part of AI motion graphics is finding a prompt that works. Here you see the result first, so you don't spend tokens guessing.

**How to use:** Filter by category (and by Prompt or Skill), open a video you like, copy its prompt and swap in our own brand, text and data. The site also offers to customise a prompt for your project.

**Watch out:** Prompts are submitted by different creators, so quality varies. Credit the author when we reuse one closely. Some cards on the homepage are sponsored.

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

## Coding agents and reverse engineering

### REA (Reverse Engineer Anything)

**Link:** <https://github.com/morluto/rea> · **Site:** <https://rea.tools> · **Type:** MCP server + agent skill + CLI · **Cost:** Free (MIT) · **Tags:** `reverse-engineering` `mcp` `binaries` `electron` `learning`

Connects a coding agent to reverse-engineering tools for native binaries, JavaScript and Electron apps, .NET assemblies and websites. Ask it how a feature in an app works: it inspects the app without its source code, explains each part with the evidence behind each conclusion, and can build a version of that feature for our own project. Analysis runs locally.

**Why it helps:** A way to study how good apps are built (like taking a watch apart to see the gears) and learn by rebuilding the pieces we want.

**How to use:**

```bash
npx rea-agents setup
```

Setup registers REA with your agent and installs its workflow instructions. Native-binary analysis uses an existing Hopper, Ghidra, IDA or Kuna install (setup can install Hopper with your approval). Static JavaScript/Electron analysis needs no extra engine. Guides and case studies are on <https://rea.tools/guides/>.

**Watch out:**
- Only analyse software we have the right to inspect, and read its license and terms first. Many forbid reverse engineering. Use it to learn and rebuild ideas in our own code, never to copy someone else's code or assets.
- Install only from the official sources (the GitHub repo, rea.tools or the `rea-agents` npm package). The README warns about lookalike repos.
- On Linux, Ghidra/JADX and the JS/Electron analysis need a procps-compatible `ps`.

### OpenCode

**Link:** <https://github.com/anomalyco/opencode> · **Site:** <https://opencode.ai> · **Type:** Coding agent (terminal UI + desktop app) · **Cost:** Free (MIT); you pay for whichever model you connect · **Tags:** `coding-agent` `open-source` `any-model` `cli`

An open-source AI coding agent, similar to Claude Code, that works with many model providers, not just one.

**Why it helps:** Lets us run long or heavy jobs (for example a large REA analysis) on a cheaper model, such as one of DeepSeek's, and keep the stronger models for the parts that need them.

**How to use:**

```bash
npm i -g @opencode/cli@latest
```

Also available through Homebrew (`brew install anomalyco/tap/opencode-v2`), mise, Nix and Arch packages, plus a desktop app (beta) for macOS, Windows and Linux at <https://opencode.ai/download>.

**Watch out:** Remove versions older than 0.1.x before installing. Check what each model provider charges and its data policy before sending it project code.

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
