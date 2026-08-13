# Agent Architecture Lab

An interactive, single-page site for **learning and testing your understanding of multi-agent systems** — the coordinator (**orchestrator / supervisor / manager**), **sub-agent / worker**, and the **workflow-vs-agent** distinction.

Content is **grounded in and cited to the primary sources**: Anthropic, LangChain/LangGraph, OpenAI, and AWS. A key theme of the site is that these companies use *different words for the same ideas*, and it maps them explicitly.

🔗 **Live site:** once GitHub Pages is enabled, this is served at
`https://<your-username>.github.io/agent-architecture/`

## What's inside

The whole app is one self-contained `index.html` (no build step, no dependencies).

| Tab | What it does |
|-----|--------------|
| 📖 **Learn** | Anthropic's workflow-vs-agent split, the six building-block patterns (prompt chaining, routing, parallelization, orchestrator-workers, evaluator-optimizer, autonomous agent), the three roles with cited definitions, and the honest cost/benefit (token multipliers, when *not* to go multi-agent). |
| 🔤 **Vocabulary** | The core correction: a side-by-side table mapping *coordinator / worker / pattern* terms across Anthropic, LangGraph, OpenAI, and AWS — plus the common attribution traps it fixes. |
| 🗺️ **Diagram** | An animated hub-and-spoke architecture diagram (coordinator → decompose/delegate → sub-agents). |
| 🎛️ **Simulator** | Four tasks, each exercising a *different pattern from the taxonomy*: orchestrator-workers (dynamic decomposition), routing (classify → one path), parallelization/sectioning, and a decentralized handoff (control transfer). |
| 🧠 **Test** | A 12-question quiz; every answer explains *why* and **cites the source**. |
| 📚 **Sources** | Every reference, each tagged *verified* (fetched from source) or *corroborated* (page was network-blocked during research; confirm exact wording against the live page). |

## The core distinctions it teaches

- **Coordinator role has four names.** `orchestrator ≈ supervisor ≈ manager ≈ lead agent` — same role, different vendor vocabularies. (Notably, **Anthropic never says "supervisor"** — it says *orchestrator* / *lead agent*; "supervisor" is LangGraph/AWS.)
- **Workflow vs. agent** (Anthropic): workflows follow *predefined code paths*; agents let the LLM *dynamically direct its own process*.
- **Routing ≠ orchestrator-workers.** Routing classifies → one path; orchestrator-workers *dynamically decomposes* → many workers → synthesizes.
- **Handoff ≠ delegation.** A handoff transfers control/ownership to a peer; delegation keeps the coordinator in control and expects a report back.

## A note on sourcing

Where the research environment could reach a source directly (LangGraph & OpenAI repo docs, Anthropic cookbook), quotes are **verbatim-verified**. Anthropic's blog posts, the OpenAI PDF, and AWS docs were blocked by the network proxy during research, so those quotes are **corroborated** across multiple summaries — accurate in substance, but the Sources tab flags them so you can confirm exact wording against the live pages.

## Enabling GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Select branch **`main`**, folder **`/ (root)`**, and **Save**.
5. Wait ~1 minute, then open `https://<your-username>.github.io/agent-architecture/`.

## Local preview

It's static — just open `index.html` in a browser, or run any static server:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Editing

Everything (content, styles, quiz questions, simulator tasks) lives inline in `index.html`:

- **Quiz questions** → the `questions` array in the `<script>` block.
- **Simulator tasks** → the `tasks` array.
- **Styling / colors** → the `:root` CSS variables at the top (light + dark themes supported).
