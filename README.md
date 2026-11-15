# Tools for Work

A curated reference of tools that help our work, mostly ones that give Claude (and us) something it can't do well on its own: real assets, design judgement, data and specialised workflows.

Each entry says what the tool is, how it helps, how to use it, and anything to watch out for.

## Contents

- [Video, audio and media](#video-audio-and-media)
  - [Openverse](#openverse)
  - [Prompt Motion](#prompt-motion)
  - [YouTube Agent Skill](#youtube-agent-skill)
  - [Claude Motion (and Dashboards)](#claude-motion-and-dashboards)
- [Design and UI](#design-and-ui)
  - [unslop](#unslop)
  - [Hallmark](#hallmark)
  - [Awards skill (/awwwards and /jury)](#awards-skill-awwwards-and-jury)
  - [The Kitchen](#the-kitchen)
- [Coding agents and reverse engineering](#coding-agents-and-reverse-engineering)
  - [REA (Reverse Engineer Anything)](#rea-reverse-engineer-anything)
  - [Reverse-engineer apps prompt (no install)](#reverse-engineer-apps-prompt-no-install)
  - [OpenCode](#opencode)
- [Prompts and thinking](#prompts-and-thinking)
  - [Be Ambitious](#be-ambitious)
  - [Arena](#arena)
- [Saving tokens and limits](#saving-tokens-and-limits)
  - [Ponytail](#ponytail)
  - [Graphify](#graphify)
  - [OmniRoute](#omniroute)
  - [Flint (local coding model)](#flint-local-coding-model)
- [Desktop assistants](#desktop-assistants)
  - [Atticus (Mac and Windows)](#atticus-mac-and-windows)
- [Explaining and documenting](#explaining-and-documenting)
  - [Annotated Illustrations (Ian Xiaohei)](#annotated-illustrations-ian-xiaohei)
- [Social media, marketing and sales](#social-media-marketing-and-sales)
  - [OpenReply](#openreply)
  - [Sellbird (formerly Harvey)](#sellbird-formerly-harvey)
- [Career](#career)
  - [AI Job Search](#ai-job-search)
- [Guides and playbooks](#guides-and-playbooks)
  - [How the Claude Code team does code review](#how-the-claude-code-team-does-code-review)

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

### Claude Motion (and Dashboards)

**Link:** <https://claude.com/resources/articles/dashboards-and-motion> · **Type:** Built into Claude (claude.ai) · **Cost:** Beta. Motion: Team and Enterprise plans; Dashboards: paid plans · **Tags:** `motion-graphics` `explainer-video` `animation` `dashboards` `anthropic`

Anthropic's own animation feature, announced October 2026. Describe an explainer (for example "animate how our pricing plans compare for the sales kickoff" or "turn this quarterly report into a 30-second explainer") and Claude builds it as code that animates our text, charts, shapes and images. It plays like a short video, and you download it as an MP4.

**Why it helps:** Most AI video looks like AI video, but this has no generated footage, no AI people and nothing that melts or morphs. Because it's code, you can change just one word, number or timing, either in the editor or by asking Claude, without starting over. Like editing a doc instead of reshooting a film. Good for presentations, onboarding and turning results into short explainers. Pairs with [Prompt Motion](#prompt-motion) for ideas.

**How to use:** On a Team or Enterprise plan, ask Claude for the animation in a normal chat. Enterprise admins must first turn it on under Organization settings → Artifacts. To polish it further, open it in Adobe, Descript, Runway and others.

**Also in the same release, Claude Dashboards:** connect a data source (BigQuery, Snowflake, Databricks, Redshift, ClickHouse) or a CRM like Salesforce, ask a question in plain language, and get a dashboard that stays current. Click any number to see the query behind it.

**Watch out:** Both are in beta. Motion is not on Free or Pro plans. It's built for explaining our own work, not for realistic footage.

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

### Awards skill (/awwwards and /jury)

**Link:** <https://github.com/juliobsz/skills> · **Type:** Two agent skills (Claude Code, Codex, Cursor, Gemini CLI, OpenCode, Antigravity) · **Cost:** Free (MIT) · **Tags:** `web-design` `claude-skill` `frontend` `motion` `audit`

`/awwwards` builds a whole, memorable website from one line ("make me a portfolio, my name is Julio"), acting as creative director, designer and developer at once:

1. **Brief:** works out who the site is for and its job, and writes down any assumptions.
2. **Concept:** drafts three ideas from different angles, scores them on originality and fit, and builds the best one around a single "signature moment".
3. **Art direction:** palette, font pairing, grid and motion written to `DESIGN.md`, plus a test that throws out anything an average model would produce. Purple gradients, glassmorphism, three-card grids, fake logos and "elevate your brand" copy are banned unless the concept truly needs them.
4. **Build:** Next.js by default, Astro for content-only showcases, or your existing stack. Uses GSAP, Lenis and OGL for motion and WebGL.
5. **QA loop:** real-browser screenshots (desktop, phone, reduced motion), speed and accessibility checks. Then a fresh critic agent that never saw the plan scores the screenshots, and it keeps fixing until every category reaches 8/10.

`/jury` is the critic on its own. It scores any site (ours, one `/awwwards` built, or a competitor's) on Awwwards-style criteria and gives fixes ranked by how much score they'd gain: `/jury https://site.com`, or `/jury https://mine.com vs https://theirs.com`.

**Why it helps:** Like an art director who never settles: no lazy page ships. Of the design skills here, it's the one for building a *new* standout site from scratch. [Hallmark](#hallmark) is lighter and theme-based, and [unslop](#unslop) fixes an existing site.

**How to use:**

```bash
npx skills add juliobsz/skills -g
```

Open a new session and type `/awwwards`, or just ask for a website. Add `--skill jury` to install only the critic. Plugin route: `/plugin install awwwards --marketplace juliobsz/skills` (same for `jury`). Use the plugin or the CLI, not both.

**Watch out:**
- A full run is long and token-heavy, so use it for sites that matter.
- The 8/10 is its own score. Against two real winning sites, the critic scored about 1.1 points stricter than the actual jury. It isn't affiliated with Awwwards.
- Without real copy and photos it ships marked placeholders for us to replace. It deploys (Vercel, Netlify, Cloudflare) only after we confirm.
- The skills CLI collects anonymous usage data. Set `DISABLE_TELEMETRY=1` to turn it off.

### The Kitchen

**Link:** <https://www.dqnamo.com/kitchen> · **Type:** Gallery of UI components and interface studies · **Cost:** Free to browse · **Tags:** `ui-components` `micro-interactions` `react` `animation` `frontend`

A collection by dqnamo of small, tactile interface pieces that make an app feel crafted rather than generic. Examples include a cassette audio player with turning reels, a hold-to-delete button that fills while held and then offers an undo, a checkout that prints a receipt when payment clears, a magnetic file drop zone, a self-drawing signature, a ticket and a postage stamp frame, playing cards, scramble text and an iridescent foil effect.

**Why it helps:** Most AI-built apps look and feel the same. One or two memorable details, like swapping plastic for real wood, make ours feel expensive without changing how it works. Pairs with the design skills above: they fix the layout, these add the feel.

**How to use:** Open a component, copy its code from the page, or give Claude the page link and ask it to adapt that component to our design.

**Watch out:** We couldn't find a license on the site. Check with the author before shipping its code in a commercial product, or have Claude rebuild the idea in our own code. Use one or two signature details per app, not all of them.

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

### Reverse-engineer apps prompt (no install)

**Link:** <https://bit.ly/4i0wNCh> (Notion page "Reverse engineer Apps (no install)") · **Type:** Prompt / skill · **Cost:** Free (based on REA, MIT) · **Tags:** `reverse-engineering` `prompting` `app-builder` `rebuild`

REA's method without its tools. REA's own instructions (its skill file and guides, 789 lines) distilled into one prompt that works in any chat that accepts images. Attach screenshots or screen recordings of an app from your own account, and it:

1. writes a checklist of everything needed to rebuild it (every screen, action, rule and the stored data);
2. goes feature by feature: where the user starts, what they do, what changes, what they end up with;
3. marks each finding OBSERVED, INFERRED or UNKNOWN, citing the source screenshot;
4. lists the data model (tables and fields);
5. re-checks the list and says exactly what to click or record next for anything still open;
6. ends with a build spec under "Build this", ready to paste into Claude or an app builder.

**Why it helps:** Many subscriptions pay for a handful of core features (booking pages, forms, boards). The prompt's author says their Calendly-style rebuild worked first try (booking page, Google login, confirmation emails), and Typeform- and Trello-style rebuilds came close. Like getting the recipe, then cooking it your way.

**How to use:** Copy the "One-paste prompt" from the page, replace `[APP]`, attach the screenshots and paste. With no screenshots yet, capture every main screen, one full journey of the key feature, and any settings or results page. For decompiling app files, use [REA](#rea-reverse-engineer-anything) itself.

**Watch out:** The prompt's own rules are the right ones. Only study apps you're allowed to use, never get around a login, paywall or paid feature, and copy *what* the app does, never its code, images, logo, wording, colours or name. Before cancelling a subscription, weigh the cost of hosting and maintaining our own version.

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

### Arena

**Link:** <https://github.com/Jakeschincariol/arena-skill> · **Type:** Claude Code skill · **Cost:** Free (MIT), but very heavy on usage · **Tags:** `claude-skill` `subagents` `tournament` `quality` `decision-making`

For when Claude keeps giving a bad answer. `/arena` gives the exact same task to 100 subagents, each with a different strategy card (2,160 combinations of reasoning mode, workflow and strategy, such as first principles, test first or edge cases first). They pair off, attack each other's solutions (flaws labelled FATAL, MAJOR or MINOR), defend and revise, and a separate judge scores each match on a written rubric. The loser is out: 100 → 50 → 25 → 13 → 7 → 4 → 2 → 1.

**Why it helps:** One Claude gives one answer; here the answer has to survive a bracket, like a cooking show with 100 chefs where one dish reaches the table. You get the winner, every attack it survived and how many rounds it took. If you started from an answer you rejected, a final blind judge says honestly whether the winner beats it.

**How to use:**

```bash
git clone https://github.com/Jakeschincariol/arena-skill.git
cp -r arena-skill/skills/arena ~/.claude/skills/
```

Then `/arena` (it takes your last request and the answer you didn't like), or `/arena --quick <task>` for 16 competitors, or `/arena --agents 32 <task>`. Plugin route: `/plugin marketplace add Jakeschincariol/arena-skill`, then `/plugin install arena-skill@arena-skill` (invoked as `/arena-skill:arena`). Needs Claude Code and Python 3.8+.

**Watch out:**
- A full 100-agent run is about **595 subagent calls**, so it can burn through a big share of our Claude limits. Use `--quick` day to day and save the full bracket for the questions that matter.
- It never edits our files; every competitor writes inside `.arena/`, and using the winner is our call.

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

### Flint (local coding model)

**Model:** <https://huggingface.co/RecursiveSI/flint> · **Announcement:** <https://recursive.com/updates/introducing-recursive-flint> · **Local engine:** <https://github.com/recursive-oss/rec> · **Type:** Open-weights coding model · **Cost:** Free (Apache 2.0), runs on your own hardware · **Tags:** `local-ai` `offline` `coding-agent` `open-weights`

A coding model from Recursive, built for agent work (investigating codebases, fixing bugs, implementing features, writing tests) on local hardware. It is a mixture-of-experts model with about 40B total parameters but only ~2.5B active per token, which makes it fast. Recursive reports over 125 tokens/s on an M4 Pro MacBook Pro. It supports tool use and a context of up to 256k tokens (recommended).

**Why it helps:** Most coding jobs are small: a rename, a bug fix. Flint handles those offline on our own machine, so they don't use up Claude limits and the code never leaves the computer. We keep Claude for the hard problems.

**How to use:**
- **Mac (easiest):** install Recursive's `rec` engine, then start it with a ready-made harness:

  ```bash
  curl -fsSL https://raw.githubusercontent.com/recursive-oss/rec/main/install.sh | bash
  rec launch opencode   # or: rec launch pi (Recursive's preferred harness)
  ```

  `rec serve` exposes OpenAI- and Anthropic-compatible APIs for other clients. Pairs well with [OpenCode](#opencode).
- **NVIDIA GPU:** use the quantized NVIDIA variant, or serve the full BF16 checkpoint (~80 GB) with the SGLang kit in the Hugging Face repo.

**Watch out:**
- **Hardware is the catch.** `rec` needs an Apple Silicon Mac (M4 Pro/Max or M5 Pro/Max) with at least 48 GB of memory and ~30 GB of disk space. The full checkpoint needs a datacenter GPU (H200/B300). A typical Windows laptop can't run it well. Check our machines before planning around it.
- Recursive says it needs more guidance than the big closed models: split work into small subtasks with explicit instructions.
- Benchmark numbers are Recursive's own. Review its changes like any other agent's.

---

## Desktop assistants

### Atticus (Mac and Windows)

**Link (Mac):** <https://github.com/SaarthurR/atticus-mac> · **Link (Windows port):** <https://github.com/FindlayHi/atticus-windows> · **Type:** Voice assistant app · **Cost:** Free (MIT); runs on your Claude plan, no API key · **Tags:** `voice-assistant` `automation` `desktop` `claude-code` `productivity`

Hold a shortcut (<kbd>⌃⌥Space</kbd> on Mac, <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Space</kbd> on Windows), say what you need and let go. It opens apps, arranges windows across displays, finds files by what's inside them, reads the screen ("what's wrong with this code?"), types replies into the app you're in, dictates into any text field and runs routines. Teach it once ("when I say focus mode, close Slack and open my to-do list") and two words run it after that.

**Why it helps:** Like a chief of staff on the computer who never needs telling twice. Simple asks (open an app, move a window) skip the AI and run instantly; learned routines replay without AI too, so they cost nothing.

**How to use:**
- **Mac** (needs macOS 26 and Claude Code signed in on a Claude plan, or a local model):

  ```bash
  curl -fsSL https://raw.githubusercontent.com/SaarthurR/atticus-mac/main/install.sh | bash
  ```

- **Windows:** a community port by FindlayHi with the same features plus integrations (Home Assistant, Jellyfin and others). It runs through `claude -p` on a Claude Pro or Max plan. Install steps are in its README.

**Watch out:**
- Voice is turned into text locally and audio never leaves the computer, but what you ask and screenshots of the screen go to Claude. Be careful with sensitive windows open.
- Deletes, sends, purchases and system commands ask first, and the reply feature types but doesn't send. Keep those confirmations on.
- Each ask uses a little of our Claude plan (the Windows port estimates ~0.1¢ each). Anonymous usage counts are on by default; turn them off in Settings.
- The Windows version is a separate community project, not by the original author.

---

## Explaining and documenting

### Annotated Illustrations (Ian Xiaohei)

**Link:** <https://github.com/helloianneo/ian-xiaohei-illustrations> · **Type:** Agent skill (written for Codex) · **Cost:** Free (MIT, credit to Ian when adapting) · **Tags:** `illustrations` `diagrams` `explainers` `onboarding` `image-generation`

A skill that reads a piece of content, picks the key ideas (a flow, a structure, a before/after, a state) and draws each as a 16:9 hand-drawn sketch: white background, thin black lines, a small black character ("Xiaohei") doing the core action, and a few short red, orange and blue annotations. It first proposes a shot list (4 to 8 images, where each goes and what each shows), then generates each image separately and checks it against a QA list.

**Why it helps:** AI builds things in minutes, but understanding them takes much longer, and that gap is where bugs hide. Point it at a project, have it read the whole thing, and it sketches what each part does, what runs first and what talks to what. Like a map sketched on a napkin, a new teammate gets it in one look, even if they don't code.

**How to use:** Copy the inner `ian-xiaohei-illustrations/` folder into the agent's skills folder (Codex: `~/.codex/skills/`; for Claude Code, `~/.claude/skills/`). Then, for example: *"Use ian-xiaohei-illustrations: read this project and plan 5 illustrations of how it works, with English labels. Don't generate yet."* Approve the shot list, then ask it to generate.

**Watch out:**
- **Ask for English labels.** It's built for Chinese articles, and its instructions and labels default to Chinese.
- It generates images with Codex's built-in image tool. Claude Code has no built-in image generator, so there it can only plan the shot list and prompts unless we connect an image model.
- It's meant for explainer sketches, not exact architecture or flow diagrams, and it doesn't output editable SVGs. Image models can misspell labels, so keep labels short and check each image.

---

## Social media, marketing and sales

### OpenReply

**Link:** <https://github.com/diwenne/openreply> · **Demo:** <https://openreply.diwen.dev> · **Type:** Self-hosted web app · **Cost:** Free (MIT); hosting can fit free tiers · **Tags:** `instagram` `automation` `comment-to-dm` `manychat-alternative` `self-hosted`

An open-source alternative to ManyChat for Instagram comment-to-DM. Set a keyword on a post or reel, and everyone who comments it gets a DM with your link within seconds, optionally plus a public reply. The same keywords can fire on DMs and Story replies. It also has tracked links with click stats, an optional "follow first" gate, `{username}` personalisation, several Instagram accounts and team roles in one dashboard, a DM inbox, send logs, and a Brazilian Portuguese interface.

**Why it helps:** Per-contact pricing turns a viral reel into a bigger bill. With our own copy, like owning the vending machine instead of paying per snack, more comments don't cost more.

**How to use:** You have to deploy your own copy; the demo site never sends DMs. It needs a public HTTPS URL, PostgreSQL, Redis, email for sign-in, an always-on worker process and an Instagram Business or Creator account. The author's stack uses free tiers (Vercel, Neon, Redis Cloud, an Oracle Cloud free VM for the worker, Resend). `docs/setup.md` in the repo has the full walkthrough and a ready-made prompt to have Claude Code guide the setup.

```bash
git clone https://github.com/diwenne/openreply.git
cd openreply && npm install && cp .env.example .env   # fill in values per docs/setup.md
docker-compose up -d && npm run db:generate && npm run db:migrate
npm run dev      # web app + webhooks
npm run worker   # second terminal: this is what sends the DMs
```

**Watch out:**
- It uses Meta's official API (no scraping, no Instagram password), so Instagram's rules still apply: about 750 private replies per hour per account (overflow is queued) and a 24-hour messaging window.
- You need your own Meta developer app, or the optional *paid* Zernio connection (the project's sponsor).
- Coming from ManyChat: disconnect it first and give OpenReply control of conversations in Meta Business Suite, or DM buttons fail.
- If comments arrive but no DM goes out, check that the worker is running.

### Sellbird (formerly Harvey)

**Link:** <https://github.com/ethanplusai/harvey> (now redirects to `ethanplusai/sellbird`) · **Site:** <https://sellbird.ai> · **Type:** Self-hosted outreach agent + dashboard · **Cost:** Free (AGPL-3.0); runs on your Claude Pro/Max or ChatGPT plan · **Tags:** `cold-email` `lead-generation` `sales` `claude-code` `self-hosted`

An open-source cold-email agent that does the research first. It finds businesses that match your customer (free via OpenStreetMap, or a paid source that shows its cost first), reads each company's website for buying signals (no online booking, ads running, a role they're hiring for), finds the owner or manager, and verifies the email address. Then it writes a short personal sequence about something real for that business, sends it from your Gmail, Microsoft 365 or SMTP mailbox, reads the replies and drafts answers that steer toward a booked call.

**Why it helps:** Lazy, generic cold email gets ignored. This is a sales rep who never skips the research, even on email five hundred, without paying an agency or tools like Apollo or Clay.

**How to use:** Needs Python 3.11+, Claude Code signed in on a Pro/Max plan (or Codex on ChatGPT), and a separate, warmed-up sending mailbox.

```bash
git clone https://github.com/ethanplusai/sellbird.git
cd sellbird
claude   # then say: "set up Sellbird for me"
```

The repo's `CLAUDE.md` turns Claude Code into the setup guide. Manual route: `pip install -e .`, fill in `.env`, then `sellbird train <our-site>`, `sellbird signals --confirm free`, `sellbird discover`, `sellbird dashboard` and `sellbird run`. Only want leads? Stop after verifying and run `sellbird export` for a CSV.

**Watch out:**
- **Law first.** Unsolicited email to people's work addresses falls under LGPD in Brazil (and GDPR, CAN-SPAM and others abroad): have a legitimate basis, identify ourselves, honour opt-outs (it does this automatically) and don't store more personal data than needed.
- Keep the default where every email waits in the Outbox for our approval. Turn on autopilot only once we trust its drafts.
- Send from a separate domain and warm the mailbox first, or our main domain's deliverability suffers.
- It runs in the background through our Claude plan, so it eats into the same usage limits as our own work. Check that this kind of automated use fits the plan's terms.
- AGPL-3.0: if we modify it and offer it to others as a service, we must publish our changes.

---

## Career

### AI Job Search

**Link:** <https://github.com/ai-job-search-dev/ai-job-search> · **Type:** Claude Code project (commands + skills + tools) · **Cost:** Free (MIT); needs a Claude subscription or API credits · **Tags:** `job-search` `resume` `cover-letter` `interview-prep` `claude-code`

A job-application workflow built on Claude Code that you clone and fill with your own profile. It searches job boards, checks your fit for each posting first, then tailors the CV and writes a cover letter per job (one agent drafts, another reviews), preps you for interviews and tracks the results. The author, a geophysicist who lost their job in late 2025, used it for their own search: 69 tailored applications, 20 first interviews and one job offer.

**Why it helps:** It swaps one generic resume sent everywhere for fewer, better-fitted applications. Apply less, land more.

**How to use:** Needs Claude Code, Python 3.10+, [Bun](https://bun.sh) and LaTeX (`lualatex` and `xelatex`; MiKTeX works on Windows).

```bash
gh repo clone ai-job-search-dev/ai-job-search
cd ai-job-search
git remote rename origin upstream
gh repo create ai-job-search --private --source=. --remote=origin --push
python tools/install_portal_clis.py
```

Then in Claude Code: `/setup` (reads your CV, LinkedIn export and documents, or interviews you), `/scrape` to find jobs, `/rank` to shortlist, `/apply <job-url-or-pasted-text>` and `/interview`.

**Watch out:**
- **Keep it private.** `/setup` writes your personal data (contact details, work history, salary expectations) into tracked files. Use a private copy as above, never a public fork.
- The built-in job-board searches are for Denmark. For Brazil we'd add our own boards (`/add-portal`); the fit and tailoring steps work in any country and language. Check each board's terms before searching it automatically.
- Read every CV and letter before sending. Tailoring must never invent experience. The author was open with employers that they used it, and recommends the same.

---

## Guides and playbooks

### How the Claude Code team does code review

**Link:** <https://claude.dev/blog/solving-code-review-at-anthropic/> · **Type:** Article (Anthropic engineering blog, Oct 2026, ~14 min) · **Cost:** Free · **Tags:** `code-review` `testing` `ci` `claude-code` `process`

How Anthropic's Claude Code team reviews code now that Claude writes most of it. Review moved mostly to machines, in layers: the agent verifies its own work, then CI, AI review, security review, a risk-based human approval, a merge queue with feature flags, and fast rollback. Between June and September, merged PRs more than doubled while the share reverted fell by over 40%.

**Why it helps:** Claude saying "done" isn't proof; passing tests are. The post is a checklist we can copy, like the one pilots run before takeoff, so we ship code we can trust.

**Gates to copy into our projects:**
- **Before the PR:** give Claude checks it can run (tests, build, linter, a screenshot to compare) and ask it to *show the output* instead of saying it's done. Then have a subagent with fresh context review the diff. Locally, run `/code-review` and `/security-review`.
- **Turn every repeated mistake into a rule:** in a short `CLAUDE.md` (stack, conventions, goals, non-goals), a `REVIEW.md` saying what matters in each part of the code, a lint rule or a hook.
- **On every PR:** required CI; a PR template with "Testing", "Risk" and "How to revert"; an AI reviewer and a security review whose open findings block the merge.
- **Make reviews converge:** cap at **three rounds**, then step back and rethink the approach. After the first few passes, review only the new diff, and fix a whole class of bug at once. (One PR ran over fifty agent review/fix rounds overnight before someone stopped it.)
- **Match review effort to risk:** a quick pass for routine changes, a deep one where a missed bug is expensive. Sensitive paths (auth, billing, CI, release) always need a person, and a bot's approval never replaces a required human's.
- **After the merge:** feature flags, internal use first, staged releases, one-step rollback. Turn incidents and reverts into test cases for the reviewer.

**Watch out:** It describes a large team with heavy CI. Start with the "before the PR" habits and the round cap, then add layers as projects grow.

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
