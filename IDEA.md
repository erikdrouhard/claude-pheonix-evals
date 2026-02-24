# Phoenix Evals & Agent Observability

## 1. Eval Foundations

### Open & Axial Coding
- **Open coding**: Label everything you observe in model outputs (failures, quality issues, patterns)
- **Axial coding**: Group and structure those labels into a hierarchy (parent-child relationships, subtypes)
- This process is model-agnostic and durable — the methodology hasn't changed even as models improve
- The bar has moved up: failure modes are more subtle now, evals need finer granularity

### Key Principle
- You must always **look at the data** — automation scales the labeling, it doesn't replace your judgment
- Start manual (20-30 examples), then automate, then validate the automation

---

## 2. Practice Evals on Your Own Prompting

### Concept
Use your own AI coding sessions as eval data to build eval skills and improve prompting simultaneously.

### Practical Steps
- [ ] Review SpecStory session logs and apply open coding (label patterns: one-shot success, multi-turn struggle, model going off track)
- [ ] Apply axial coding to organize labels into a taxonomy (e.g., "missing context" → subtypes)
- [ ] Start with a markdown file or notebook before reaching for tooling
- [ ] Graduate to Phoenix when you feel the pain of wanting structured tooling

---

## 3. Local Phoenix + MCP Setup

### Architecture
```
[CLI Agent (Claude Code / OpenCode)]
        ↓ (queries via MCP)
[Phoenix MCP Server (local process)]
        ↓
[Phoenix Instance (localhost:6006)]
        ↓
[SQLite (local storage)]
```

Everything runs locally. No data leaves your machine.

### Practical Steps
- [ ] Install Phoenix locally (`pip install arize-phoenix`, then `phoenix serve`)
- [ ] Add Phoenix MCP to Claude Code:
  ```bash
  claude mcp add phoenix npx -y @arizeai/phoenix-mcp@latest --baseUrl http://localhost:6006 --apiKey your-api-key
  ```
- [ ] Restart Claude Code and verify MCP connection
- [ ] Test querying traces conversationally through your CLI agent

---

## 4. Agentic Eval Workflow

### Concept
Use Phoenix to automate open/axial coding at scale, with you as the human-in-the-loop.

### The Loop
1. **You** define what good looks like (manual open/axial coding)
2. **Phoenix** applies that at scale (automated labeling, clustering)
3. **You** review and correct
4. **Phoenix** re-runs with refined criteria
5. Repeat

### Practical Steps
- [ ] Build a test subject agent with Copilot SDK or Claude SDK
- [ ] Instrument the agent with OpenTelemetry to send traces to Phoenix
- [ ] Run the test subject agent through scenarios
- [ ] Use CLI agent + MCP to query and analyze the trace data
- [ ] Define eval criteria from your manual review
- [ ] Run Phoenix LLM-as-judge evals against those criteria

---

## 5. Designer Playground (Multi-User Tool)

### Concept
Build an agent for designers with Phoenix bundled invisibly in the background. They use the tool, traces are collected locally on their machine, and they can export when they need help.

### Architecture
```
Designer's Machine:
[Design Agent CLI/Playground]
        ↓ (auto-instrumented)
[Phoenix (background process)]
        ↓
[SQLite (local file)]
        ↓
[Download Trace Log button] → file export
```

### UX Principles
- Phoenix is invisible — designers never configure or interact with it
- Tracing is baked in at instantiation, not user-configured
- One-click trace export (not a terminal command)
- Designers send the file via Slack/email/Teams — no automated pipeline needed

### Practical Steps
- [ ] Build the design agent with Copilot SDK / Claude SDK
- [ ] Bundle Phoenix to run as a background process (starts with agent, stops with agent)
- [ ] Configure SQLite storage in the app's data directory (zero config for user)
- [ ] Pre-wire OpenTelemetry tracing with user/session metadata
- [ ] Build a "Download Trace Log" export feature (outputs JSON file)
- [ ] Test the full install experience — one command gets everything

---

## 6. Debug Workflow (Importing External Traces)

### Concept
When a designer sends you a trace file, import it into your local Phoenix and use your CLI agent to analyze it.

### Flow
```
Designer hits issue → Downloads trace file → Sends via Slack/email
        ↓
You save the file → Import into local Phoenix → Query via CLI agent + MCP
```

### Practical Steps
- [ ] Set up a folder structure for received trace files (organize by user/date)
- [ ] Import trace data into local Phoenix (`phoenix import <file>`)
- [ ] Query imported traces through Claude Code + MCP ("What went wrong in Jane's session?")

---

## Security & Privacy Notes

- **Self-hosted Phoenix**: No telemetry collected, data stays on machine
- **Arize (the company)**: SOC 2 Type II certified, HIPAA compliant
- **For multi-user tools**: Users control their own data, export only what they choose to share
- **No central server needed**: Each user runs Phoenix locally, avoids custodian-of-data problem
- **Cloud option exists** but unnecessary for this workflow
