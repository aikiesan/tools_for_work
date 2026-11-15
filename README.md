# Tools for Work

A curated reference of tools that help our work, mostly ones that give Claude (and us) something it can't do well on its own: real assets, design judgement, data and specialised workflows.

Each entry says what the tool is, how it helps, how to use it, and anything to watch out for.

## Contents

- [Video, audio and media](#video-audio-and-media)
  - [Openverse](#openverse)
  - [Prompt Motion](#prompt-motion)
  - [YouTube Agent Skill](#youtube-agent-skill)
- [Design and UI](#design-and-ui)
  - [unslop](#unslop)
  - [Hallmark](#hallmark)
- [Coding agents and reverse engineering](#coding-agents-and-reverse-engineering)
  - [REA (Reverse Engineer Anything)](#rea-reverse-engineer-anything)
  - [OpenCode](#opencode)
- [Prompts and thinking](#prompts-and-thinking)
  - [Be Ambitious](#be-ambitious)
- [Saving tokens and limits](#saving-tokens-and-limits)
  - [Ponytail](#ponytail)
  - [Graphify](#graphify)
  - [OmniRoute](#omniroute)

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

### YouTube Agent Skill

**Link:** <https://github.com/Jakeschincariol/youtube-agent-skill> · **Type:** Claude skills (11) + Python tools · **Cost:** Free (MIT), no API key · **Tags:** `youtube` `content-creation` `claude-skill` `video` `scripts`

Eleven Claude skills for running a YouTube channel, backed by six dependency-free Python scripts. It covers the boring parts where channels usually fail:

| Command | What it does |
| --- | --- |
| `/yt-script` | Turns an idea into a script: five hooks from 21 formulas, scored before you film, then the spoken script with retention beats marked |
| `/yt-package` | Checks title and thumbnail together for truncation, duplication and vagueness |
| `/yt-edit` | Turns a transcript into an edit decision list (dead air, filler, retakes) with timecodes |
| `/yt-retention` | Reads your retention export and finds the exact second viewers left, and what was being said |
| `/yt-viral` | Ranks what works in your niche by how far each video beat its own channel's median |
| `/yt-shorts` | Finds Shorts inside a long video and writes a new first line for each |
| `/yt-seo`, `/yt-chapters` | Description, useful tags, target queries; chapters checked against YouTube's rules |
| `/yt-comment`, `/yt-plan`, `/yt-audit` | Comment triage and replies, a weekly plan that fits your hours, a channel audit ending in one fix |

**Why it helps:** Like a producer reviewing every upload, so we stop guessing what went wrong.

**How to use:** In Claude Code, run these as two separate prompts:

```
/plugin marketplace add Jakeschincariol/youtube-agent-skill
/plugin install youtube-agent
```

Or copy `skills/yt-*` into `~/.claude/skills/`. Then fill in `templates/voice.md` (copy it to `~/.claude/youtube/voice.md`); every skill reads it.

**Watch out:** It never publishes; you upload. The hook score is a heuristic, not a prediction of views. `/yt-viral` reads public listings only.

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

### Hallmark

**Link:** <https://github.com/Nutlope/hallmark> · **Site:** <https://www.usehallmark.com> · **Type:** Design skill (Claude Code, Codex, Cursor, OpenCode) · **Cost:** Free (MIT) · **Tags:** `web-design` `ui` `claude-skill` `frontend` `audit`

A design skill by Together AI that won't produce pages that look AI-generated. For a new page it offers three of its fifty themes (each a full material: type, colour, surfaces, components), builds the page around what the visitor came to do, then checks it in a real browser at eight screen widths and has a fresh reviewer look at it. It catches the usual tells: the same fonts, tiny capitalised labels above every heading, one coloured word in a headline, rows of three cards, a sign-up box at the end of every page.

**Why it helps:** People stop trusting a site once they spot it as AI-made. Hallmark is a second pair of eyes before launch. Compared with [unslop](#unslop): Hallmark is strongest for building new pages from its themes, and unslop for fixing an existing site in its own style. Both can audit.

**How to use:**

```bash
npx skills add nutlope/hallmark -g
```

Then `/hallmark <prompt>` for a new page, `/hallmark audit ./index.html` to only list the tells, or `/hallmark redesign ./src/app` to rebuild while keeping content and wiring. Plugin route: `/plugin marketplace add nutlope/hallmark`, then `/plugin install hallmark@hallmark`.

**Watch out:** Needs Node 18+. The browser checks also need `npm i -g puppeteer-core` and Chrome; without them only the static checks run. It outputs self-contained HTML/CSS, so a framework app may need the result ported.

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

## Prompts and thinking

### Be Ambitious

**Post:** <https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models> · **Skill:** <https://github.com/DannyMac180/skills/tree/main/be-ambitious> · **Type:** Prompt + Claude skill · **Cost:** Free (skill is MIT) · **Tags:** `prompting` `claude-skill` `research` `quality`

A prompt by Felix Rieseberg (who works on Claude at Anthropic), packaged as a `/be-ambitious` skill by DannyMac180. Before doing a task, Claude says what a top professional in the field would do that we aren't asking for, the rawest source material they'd start from, the specific methods and tools they'd use, and what (other than us or the model) would show the result is right. Then it rewrites the prompt to ask for exactly that.

**Why it helps:** The model's work is capped by what we ask for. Ask for a small fix and you get a small fix. This pushes it to find the goal behind the task and work like a senior expert would. The post explains the four kinds of ambition: speed, altitude (aim at the outcome, not the task), depth (work like a field-leading expert) and range (borrow from other fields).

**How to use:** Read the post once. Then paste the prompt before any big task, or install the skill folder in `~/.claude/skills/be-ambitious/` and run `/be-ambitious <task>`.

**Watch out:** It is meant to make a task *deeper, not bigger*: same goal and scope, higher standard. If its suggestions start adding features or side quests, drop them.

---

## Saving tokens and limits

Claude's usage limits mostly run out from waste: code nobody asked for, the same files read over and over, and builds that stop dead halfway when a limit hits. These three tools tackle each of those.

### Ponytail

**Link:** <https://github.com/DietrichGebert/ponytail> · **Site:** <https://ponytail.dev> · **Type:** Claude Code plugin / skill · **Cost:** Free (MIT) · **Tags:** `claude-skill` `minimal-code` `tokens` `code-quality`

A skill that makes the agent write like a terse senior developer: only the code the task needs, without cutting validation, error handling, security or accessibility. The author's benchmark (Claude Code, 39 tasks, with and without the skill) reports roughly half the code and about 45% fewer tokens, and more risky logic shipped with tests.

**Why it helps:** Less code that nobody asked for means fewer tokens, less to review and less to maintain.

**How to use:** In Claude Code, run these as two separate prompts:

```
/plugin marketplace add DietrichGebert/ponytail
/plugin install ponytail@ponytail
```

Codex and other agents: see the repo's `INSTALL.md` (or copy its `AGENTS.md` into the project).

**Watch out:** The numbers are the author's own benchmark. Still review what it removes.

### Graphify

**Link:** <https://github.com/Graphify-Labs/graphify> · **Site:** <https://www.graphify.com> · **Type:** CLI + `/graphify` skill · **Cost:** Free (Apache 2.0); optional paid cloud · **Tags:** `knowledge-graph` `codebase-map` `tokens` `claude-skill`

Maps a whole project (code, docs, SQL schemas, configs, PDFs, images) into a knowledge graph that the agent queries instead of grepping and re-reading files. Code is parsed locally with tree-sitter (deterministic, no LLM, nothing leaves the machine). Each edge is marked as read directly from the source (`EXTRACTED`) or inferred (`INFERRED`).

**Why it helps:** Gives Claude a map of the project, so it stops reading the same files again and again.

**How to use:** Needs Python 3.10+ and `uv` (or `pipx`):

```bash
uv tool install graphifyy
graphify install
```

Then run `/graphify .` in the assistant. It writes `graphify-out/` with `graph.html` (clickable map), `GRAPH_REPORT.md` (highlights) and `graph.json` (the full graph).

**Watch out:** The package is spelled `graphifyy` (two y's). Docs, PDFs and images go through a model for their semantic pass, so they cost tokens and leave the machine, unlike code. Graphify Cloud is a separate paid product.

### OmniRoute

**Link:** <https://github.com/cheaper-inference/OmniRoute> · **Site:** <https://omniroute.online> · **Type:** Local AI gateway (proxy + dashboard) · **Cost:** Free (MIT); provider costs are your own · **Tags:** `ai-gateway` `fallback` `multi-provider` `tokens`

A local gateway with one OpenAI-compatible endpoint in front of hundreds of model providers. It falls back automatically between your connected providers based on quota, and can compress prompts. It works with Claude Code, Codex, Cursor, OpenCode, Cline and Copilot.

**Why it helps:** When one provider's limit hits, work continues on another instead of stopping halfway through a build.

**How to use:**

```bash
npm install -g omniroute
omniroute
```

Open the dashboard at `http://localhost:20128`, connect providers with your own accounts or API keys, then point the coding tool at `http://localhost:20128/v1` with the key shown under Dashboard → Endpoints and model `auto`.

**Watch out:**
- It only routes to accounts you connect yourself. Check each provider's terms, quotas and data policy, and avoid the "web-cookie" providers, which use a logged-in browser session instead of an official API and can break the provider's terms. Providers marked `tos: avoid` are left out of `auto` by default; keep it that way.
- Fallback means the same task can switch to a weaker model mid-way. Check which model answered before trusting important output.
- Don't route confidential project data through free tiers that train on inputs.
- On npm 11+ you may need to allow its install scripts (see its README).

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
