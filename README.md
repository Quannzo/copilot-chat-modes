# Copilot Chat Modes

Your personal GitHub Copilot chatmodes for planning, building, reviewing, and prompt crafting—quick to use, easy to love. Drop them in your user prompts folder and pick a mode while chatting.

## What’s included ✨
- `code.chatmode.md` — Implementation Agent. End-to-end coding assistant that turns a requirement into minimal, verified diffs with tests and quality gates.
- `planner.chatmode.md` — PRD Implementation Planner. Converts a PRD into an actionable plan (requirements, architecture, WBS, validation, risks). Control phrases: `concise`, `include-estimates`, `json-output`, `add-diagrams`, `no-clarify`.
- `prd.chatmode.md` — PRD Author. Iterates to a final PRD and emits the document as JSON-only on finalization. Strong guardrails for assumptions and clarifications.
- `prompter.chatmode.md` — Prompt Optimizer. Transforms any input into a high-quality, copy-ready prompt. Single-output text, no explanations.
- `review.chatmode.md` — Code Review. Security-first diff review for a PR or branch compare with deterministic sections and prioritized findings.
- `debug.chatmode.md` — Debug & Root Cause Analysis. Reproduce, isolate, and propose minimal, safe fixes with evidence-backed hypotheses and regression test guidance.

## Prerequisites 🧰
- Visual Studio Code
- GitHub Copilot Chat extension enabled

## Installation 🚀
These files are already in the correct folder for this profile. To install on another machine, place them under your user prompts path and reload VS Code.

Paths by platform (Stable):

```
Windows: %APPDATA%\Code\User\prompts
macOS:   ~/Library/Application Support/Code/User/prompts
Linux:   ~/.config/Code/User/prompts
```

Paths for VS Code Insiders:

```
Windows: %APPDATA%\Code - Insiders\User\prompts
macOS:   ~/Library/Application Support/Code - Insiders/User/prompts
Linux:   ~/.config/Code - Insiders/User/prompts
```

Steps (any OS):
1) Create the `prompts` folder if it doesn’t exist at your user settings path.
2) Copy the `*.chatmode.md` files into that folder.
3) Reload VS Code (Command Palette → “Developer: Reload Window”).

## Usage ▶️
1) Open Copilot Chat in VS Code.
2) Use the Chat mode selector at the top of the chat panel to pick a mode (the name comes from each file’s description).
3) Start chatting; follow each mode’s operating rules and control phrases as applicable.

> Tip: If custom modes don’t appear, reload the window after placing files.

## Mode notes 📚
### Implementation Agent (`code.chatmode.md`)
- Use when you want end-to-end changes with minimal, verifiable diffs.
- Keeps a visible checklist, adds/updates tests, runs quality gates, and documents deltas briefly.

### PRD Implementation Planner (`planner.chatmode.md`)
- Input: a PRD as plain text. Output: structured plan with requirements, architecture, WBS, validation, rollout, risks, and traceability.
- Control phrases: `concise`, `include-estimates`, `json-output`, `add-diagrams`, `no-clarify`.

### PRD Author (`prd.chatmode.md`)
- Guides short clarify → ground → draft → finalize loops.
- Finalization emits a single JSON object only, matching a strict schema.

### Prompt Optimizer (`prompter.chatmode.md`)
- Treats the entire user message as the prompt to optimize—no external context.
- Returns exactly one optimized prompt string. No preamble, no code fences, no notes.

### Code Review (`review.chatmode.md`)
- Input: PR URL or repo + base/head branches.
- Produces a deterministic review: summary; prioritized findings with severity, evidence, impact, minimal fix, and suggested tests; API/back-compat; tests/docs; CI/deps; file-by-file notes; readiness checklist.

### Debug & Root Cause Analysis (`debug.chatmode.md`)
- Entry styles: task mode (run & surface issues) or issue mode (specific defect description).
- Workflow: reproduce → form ≤3 evidence-linked hypotheses → investigate with minimal probes → confirm root cause → propose smallest behavior-preserving fix (+ alternative if riskier) → outline regression tests (failing path + negative/edge).
- Guardrails: no feature creep, minimal diffs, explicit assumptions, ≤3 clarification questions per turn, deterministic output sections.

## Editing or extending 🔧
- Duplicate any `*.chatmode.md` and tweak the description, rules, or control phrases.
- Structure: each file uses a fenced `chatmode` block with a short frontmatter and a spec.
- Keep modes self-contained and deterministic; avoid cross-referencing other modes.

### Tool availability & customization 🧩
Each chatmode lists a `tools:` array. This must reflect tools actually available in your Copilot / VS Code setup. If a tool name is listed but not installed/enabled, the mode may error or silently skip capabilities.

Common built-ins: codebase, search, usages, problems, changes, runCommands, runTasks, findTestFiles, openSimpleBrowser.

Additional tools I use (and referenced in these modes):
- `context7` — Pull focused framework/library docs.
- `github` / GitHub APIs — Issues, PRs, commits, security alerts.
- `activePullRequest` (from GitHub Pull Requests extension) — Current PR context.
- `markitdown` — Convert URLs to inline markdown excerpts.
- `memory` — Persist lightweight session assumptions/preferences.
- `sequentialthinking` — Structured internal reasoning / planning steps.

To adapt:
1) Open a `*.chatmode.md` file.
2) Remove any tools you don’t have installed (keep list lean; order doesn’t matter semantically).
3) Add new tools only if you know their identifiers and behavior.
4) Reload VS Code to apply changes.

Minimal example tools list (safe baseline):
```
tools: ['codebase', 'search', 'usages', 'runCommands', 'runTasks', 'problems', 'changes']
```

Tip: Smaller tool lists can reduce noise and keep reasoning more deterministic. Expand only when a workflow genuinely benefits (e.g., architecture planning → add context7; PR work → add github / activePullRequest).

## Troubleshooting 🛠️
**Modes not visible**
- Confirm files are under the correct user `prompts` folder for your VS Code channel (Stable vs Insiders).
- Reload VS Code (Command Palette → “Developer: Reload Window”).

**Multiple similar modes**
- Update each file’s `description` to disambiguate names in the picker.

**Insiders vs Stable paths**
- Ensure you’re using the matching user settings path for your channel.

---