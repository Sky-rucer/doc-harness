# Doc Harness

**Document-based project control for AI-human collaboration.**

Doc Harness is a [Claude Code](https://claude.ai/code) skill that helps you and AI agents stay in control of any project — from a research paper to a software build to a data analysis pipeline. It maintains a small set of structured documents that capture everything about your project's state, so that any agent (or you, after a break) can pick up exactly where things left off.

---

## What Problem Does This Solve?

When you work with AI agents on a project over days or weeks, several things go wrong:

**Your AI loses its memory.** AI context windows compress or reset. The agent that spent two hours analyzing your data yesterday doesn't remember any of it today.

**Files multiply without a map.** After a few sessions, your project has 30 files — analysis reports, plans, notes, scripts — and nobody remembers what's where.

**Principles drift.** You establish important rules ("always validate on out-of-sample data"), but as work gets complex, the AI gradually forgets to follow them.

**Handoffs fail.** A different agent arrives and asks "what is this project?" — there's no single place that answers this question.

Doc Harness solves all four by creating a **self-contained documentation system** that any agent can read and immediately understand.

---

## What Is a "Project"?

In Doc Harness, a **project** is any structured work effort that:
- Has a goal and produces outputs
- Involves multiple work sessions
- Generates files along the way
- Benefits from someone (human or AI) being able to understand its current state

Examples:
- Writing a research paper or thesis
- Building a data analysis pipeline
- Developing a software library
- Conducting a literature review
- Planning and executing experiments

If your work spans more than one session and creates more than a handful of files, it's a project — and Doc Harness can help.

### What Does a Project Look Like?

A project is simply a folder. Inside it, Doc Harness creates its five status documents. Beyond that, you create whatever folders and files your work needs:

```
my-research-project/
├── CLAUDE.md                ← Doc Harness: entry point
├── CURRENT_STATUS.md        ← Doc Harness: active state
├── FILE_INDEX.md            ← Doc Harness: file catalog
├── WORKLOG.md               ← Doc Harness: work history
├── DOC_HARNESS_SPEC.md      ← Doc Harness: reference
│
├── notes/                   ← Your work: analysis notes, insights
│   ├── literature_review.md
│   ├── experiment_design.md
│   └── key_findings.md
├── scripts/                 ← Your work: code, tools
│   ├── analyze_data.py
│   └── generate_figures.py
├── data/                    ← Your work: datasets
│   └── sample_data.csv
└── drafts/                  ← Your work: paper drafts
    └── chapter1.tex
```

Doc Harness doesn't dictate how you organize your work — it only asks that every file gets registered in FILE_INDEX so nothing becomes invisible. The folders, naming, and structure are entirely yours.

---

## What Does Doc Harness Do?

Doc Harness does three things, corresponding to three moments in a project's life.

### 1. Establish Structure (`/doc-harness init`)

At the start of a project, Doc Harness creates **five documents**:

| Document | What It Does |
|----------|-------------|
| **CLAUDE.md** | The front door. Anyone opening this learns what the project is, what the rules are, and where to read next. Contains embedded operational rules that teach agents how to maintain the system. |
| **CURRENT_STATUS.md** | The living pulse. What was recently completed, what's happening now, what's next, and what principles to follow. |
| **FILE_INDEX.md** | The file catalog. Every document registered here by category. No more lost files. |
| **WORKLOG.md** | The permanent record. When a work phase ends, its full details are archived here forever. |
| **DOC_HARNESS_SPEC.md** | The reference manual. Complete specification with design rationale and worked examples. |

The agent gathers information about your project (name, goals, first tasks, constraints) and generates all five documents tailored to your specific situation — not generic templates.

### 2. Keep Projects Under Control (During Work)

As work progresses, the system provides three ongoing benefits:

**No information loss.** The core principle is **"Write It Down or Lose It"** — every important result, decision, or insight gets saved to a file and registered in the index. AI context is temporary; files are permanent.

**Always recoverable.** If the AI's context resets, it reads CLAUDE.md → CURRENT_STATUS.md and picks up exactly where it left off. CURRENT_STATUS uses a "moving car" structure:

```
┌──────────────────────────────────────────────┐
│  🛤️  Tire Tracks  — recent completed phases  │
│  🚗 Car Body     — current phase details     │
│  🔦 Headlights   — what to do next           │
│  📋 Driving Manual — working principles       │
└──────────────────────────────────────────────┘
```

When a phase ends, car body details flow to WORKLOG (permanent), get compressed into a tire track summary, and the car body clears for the new phase.

**Organized growth.** Every new file gets registered in FILE_INDEX. Projects stay navigable no matter how many files accumulate.

### 3. Check and Reflect (`/doc-harness check`)

At any point, you can run a health check that does two things:

**File audit** — Are all documents present? Is CURRENT_STATUS up to date? Does FILE_INDEX match actual files on disk? Issues get flagged with specific fix suggestions.

**Principle reflection** — Reads the project's iron rules and working principles, prompts the agent to reflect: "Am I actually following these?" This catches the gradual drift that happens during long sessions. Also runs a "Write It Down" check for unsaved information.

> Tip: Run the check as a background agent to avoid interrupting main work.

---

## Quick Start

### Install

```bash
git clone https://github.com/cilidinezy-commits/doc-harness.git
cp -r doc-harness/skill ~/.claude/skills/doc-harness
```

Or for project-level installation (available in one project only):
```bash
mkdir -p .claude/skills
cp -r doc-harness/skill .claude/skills/doc-harness
```

### Start a New Project

In Claude Code, navigate to your project directory and say:

```
/doc-harness init
```

The agent will ask about your project and create all 5 files. Or provide details directly:

```
/doc-harness init MyProject A study of price dynamics in limit order book markets
```

### During Work

The operational rules are embedded in your project's CLAUDE.md. Any agent reading it will know to:
- Update CURRENT_STATUS after each meaningful step
- Register new files in FILE_INDEX immediately
- Save important information to files ("Write It Down!")
- Run the session-end checklist before finishing

You don't need to repeatedly remind the agent — the rules are in the document it reads at every session start.

### Run a Health Check

Anytime you want to verify things are in order:

```
/doc-harness check
```

Or simply tell your AI: *"Check the status documentation"* or *"Run a doc-harness check in the background."*

---

## How It Works Day-to-Day

**Session starts →** Agent reads CLAUDE.md (overview + rules) → CURRENT_STATUS (current state) → continues working.

**During work →** Completes a step → updates CURRENT_STATUS. Creates a file → registers in FILE_INDEX. Has an important insight → saves to file ("Write It Down!").

**Phase ends →** Five-step protocol: save car body to WORKLOG (data protected first), compress to tire track summary, clear car body for new phase. Even if interrupted mid-protocol, data is safe.

**Session ends →** Quick checklist: status updated? Files registered? Anything unsaved?

**New agent arrives →** Reads CLAUDE.md → CURRENT_STATUS → fully oriented. No briefing needed.

---

## Languages

- `skill/` — English (default)
- `skill-zh/` — 中文版

Install whichever matches your working language.

## Requirements

- [Claude Code](https://claude.ai/code) (CLI, desktop app, web app, or IDE extension)
- No other dependencies

## FAQ

**Q: Does this work with AI tools other than Claude Code?**
The `/doc-harness` commands are Claude Code specific. But the documentation system itself is universal — any AI that reads markdown can follow the operational rules embedded in CLAUDE.md.

**Q: How much overhead does this add?**
Minimal. One line per completed step, one line per new file. The `/doc-harness check` takes about 2 minutes and can run in the background.

**Q: Can I customize the structure?**
Yes. Add sections to CLAUDE.md, create your own FILE_INDEX categories, adjust principles to your needs. Core requirements: keep the four documents, follow the phase transition protocol, register all files.

**Q: What about existing projects with many files?**
Run `/doc-harness init`, then populate FILE_INDEX with existing files. The agent can help scan and categorize.

**Q: Sub-projects?**
Each gets its own Doc Harness. Parent's FILE_INDEX links to sub-project entries. See spec for details.

## License

[MIT](LICENSE)

## Credits

Designed and built through iterative human-AI collaboration, with multiple rounds of blind testing by independent agents, architectural review, stress-test simulation, and real-world validation.
