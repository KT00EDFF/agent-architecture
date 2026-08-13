# Agent Architecture Lab

An interactive, single-page site for **learning and testing your understanding of multi-agent systems** — the coordinator role (**orchestrator / supervisor / manager / coordinator**), **sub-agents**, and the design decisions that actually matter.

Content is **grounded in and cited to primary sources**: Anthropic, LangChain/LangGraph, OpenAI, AWS, Microsoft, and Google — plus the practitioner debate (Cognition, Cursor, Manus, and academic failure analyses), current to **August 2026**.

🔗 **Live site:** once GitHub Pages is enabled, this is served at
`https://<your-username>.github.io/agent-architecture/`

## What's inside

The whole app is one self-contained `index.html` — no build step, no dependencies.

| Tab | What it does |
|-----|--------------|
| 📖 **Learn** | Anthropic's workflow-vs-agent split; the six building-block patterns; the three roles with cited definitions; **context engineering** (attention budget, context rot, compaction, sub-agents as context isolation); and the honest cost/benefit. |
| 🔤 **Vocabulary** | A **six-vendor** table mapping coordinator / worker / pattern / handoff / routing terms, the common attribution traps, and a **currency table** of terminology that recently changed. |
| 🧱 **Layering** | Can you have a supervisor *and* an orchestrator in one flow? The three documented splits — by **altitude**, **determinism**, and **function** — plus the transform-vs-relay test for whether a layer earns its place. |
| ⚔️ **The Debate** | The real argument: Cognition's *Don't Build Multi-Agents* vs. Anthropic's orchestrator-worker results, Harrison Chase's read-vs-write reconciliation, **Cognition's April 2026 public revision**, where experts still disagree, and what a 2024-era explainer gets wrong. |
| 🗺️ **Diagram** | Animated hub-and-spoke architecture showing decomposition down and distilled summaries back up. |
| 🎛️ **Simulator** | Six traces, each exercising a different pattern: orchestrator-workers, routing, parallelization, decentralized handoff, the **fresh-context judge**, and the parallel-write **anti-pattern**. |
| 🧠 **Test** | 18 questions; every answer explains *why* and cites the source. |
| 📚 **Sources** | Every reference, tagged *verified* or *corroborated*. |

## The core distinctions it teaches

- **The coordinator role has six names.** `orchestrator ≈ supervisor ≈ manager ≈ coordinator ≈ lead agent`. Notably **Anthropic never says "supervisor"** (it says *orchestrator* / *lead agent*), **Microsoft says "manager"**, and **Google reserves "orchestrator"** for its *deterministic* workflow agents.
- **Workflow vs. agent** (Anthropic): predefined code paths vs. the LLM dynamically directing its own process.
- **Routing ≠ orchestrator-workers.** Routing classifies → one path. Orchestrator-workers *dynamically decomposes* → many workers → synthesizes.
- **Handoff ≠ delegation.** A handoff transfers control and ownership to a peer; delegation keeps the coordinator in control and expects a report back.
- **Sub-agents are a context-management primitive**, not a parallelism one. They exist to keep exploration out of the parent's context window and must return a *distilled* answer.
- **Decision context should be shared; working context should be isolated.** This one distinction dissolves most of the 2025 multi-agent debate.
- **Single-threaded writes.** Parallelize reads; keep writes in one agent. Every pattern that survived to 2026 obeys this.

## A note on sourcing

Where the research environment could reach a source directly — vendor documentation repos on GitHub, library source code, and full-text mirrors — quotes are **verbatim-verified** and tagged as such. Several primary domains (anthropic.com, cognition.com, arxiv.org, learn.microsoft.com, adk.dev, docs.aws.amazon.com) were blocked by the research environment's network proxy; those were reached via the repositories that generate them or via cross-checked summaries, and are tagged **corroborated** so you can confirm exact wording before quoting elsewhere.

⚠️ Research also surfaced a widely-mirrored third-party wiki attributing **fabricated quotations** to a named author in this topic area. Secondary summaries of the multi-agent debate are unusually contaminated — prefer primary sources.

## Enabling GitHub Pages

1. Go to **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Select branch **`main`**, folder **`/ (root)`**, and **Save**.
4. Wait ~1 minute, then open `https://<your-username>.github.io/agent-architecture/`.

## Local preview

It's static — open `index.html` in a browser, or:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Editing

Everything lives inline in `index.html`:

- **Quiz questions** → the `questions` array in the `<script>` block.
- **Simulator traces** → the `tasks` array.
- **Styling / colors** → the `:root` CSS variables at the top (light + dark themes supported).
