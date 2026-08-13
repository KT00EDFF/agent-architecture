# Agent Architecture Lab

An interactive, single-page site for **learning and testing your understanding of multi-agent systems** — specifically the **supervisor**, **orchestrator**, and **sub-agent / domain agent** patterns.

🔗 **Live site:** once GitHub Pages is enabled, this is served at
`https://<your-username>.github.io/agent-architecture/`

## What's inside

The whole app is one self-contained `index.html` (no build step, no dependencies).

| Tab | What it does |
|-----|--------------|
| 📖 **Learn** | Plain-language breakdown of each role — what it thinks about, its superpower, its risk, and an analogy. Plus how the roles nest (`Supervisor → Orchestrator → Sub-agents`). |
| 🗺️ **Diagram** | An animated architecture diagram showing a request flowing down the hierarchy and results flowing back up. |
| 🎛️ **Simulator** | Pick a task and watch the message trace: how the supervisor routes, how the orchestrator sequences (including parallel fan-out and retry-on-failure), and how domain agents execute. Four contrasting tasks exercise different paths. |
| 🧠 **Test** | A 9-question quiz with instant, explained feedback and a score at the end. |

## The core distinction it teaches

- **Supervisor** = dynamic **routing**. Decides *who* handles the task at runtime.
- **Orchestrator** = defined **process**. Runs an ordered plan, handles handoffs, retries, and parallelism.
- **Sub-agent / domain agent** = the **specialist** that does the focused work with narrow context.

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
