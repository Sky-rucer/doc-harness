# Doc Harness

**Document-based project control for AI-human collaboration.**

Doc Harness is a [Claude Code](https://claude.ai/code) skill that creates and maintains a lightweight documentation system for any project. It enables any AI agent or human collaborator to understand and resume project work purely from reading files — no external memory system needed.

## The Problem

When AI agents collaborate with humans on projects, three things inevitably happen:

1. **Context loss** — AI context windows compress or reset, wiping out "what we were doing"
2. **Agent handoff** — A different agent arrives with zero knowledge of the project
3. **File chaos** — Work generates dozens of files that become unfindable without an index

Doc Harness solves all three by maintaining five documents per project that serve as a complete, self-contained project state.

## How It Works

Every project gets five documents:

| Document | Role | Metaphor |
|----------|------|----------|
| **CLAUDE.md** | Project entry point — overview, recovery chain, iron rules, operational rules | Front door |
| **CURRENT_STATUS.md** | Active work state — what was done, what's happening, what's next | Moving car |
| **FILE_INDEX.md** | Complete file catalog organized by category | Library catalog |
| **WORKLOG.md** | Permanent history of all completed phases | Dash cam |
| **DOC_HARNESS_SPEC.md** | Full specification (reference) | Owner's manual |

The key innovation is `CURRENT_STATUS.md`'s **"moving car" structure**:

```
┌──────────────────────────────────────────┐
│  Tire Tracks  — recent completed phases  │  (rolling 2-3 summaries)
│  Car Body     — current phase details    │  (full record, <200 lines)
│  Headlights   — next steps              │  (immediate + future)
│  Driving Manual — working principles     │  (phase-specific rules)
└──────────────────────────────────────────┘
```

When a phase ends, the car body content flows into WORKLOG (permanent archive), gets compressed into a tire track summary, and the car body clears for the new phase.

## Quick Start

### Install

```bash
# Clone this repository
git clone https://github.com/YOUR_USERNAME/doc-harness.git

# Copy the skill to your Claude Code skills directory
cp -r doc-harness/skill ~/.claude/skills/doc-harness

# Or for project-level installation
mkdir -p .claude/skills
cp -r doc-harness/skill .claude/skills/doc-harness
```

### Initialize a Project

In Claude Code, navigate to your project directory and run:

```
/doc-harness init MyProject A study of market microstructure dynamics
```

This creates all 5 files. The generated `CLAUDE.md` includes embedded operational rules, so any future agent reading it will know exactly how to maintain the system.

### Check Project Health

```
/doc-harness check
```

This runs a two-part audit:

**Part 1 — File Health**: Checks all 4 core documents exist, dates are fresh, FILE_INDEX matches actual files, WORKLOG TOC is consistent, car body isn't too long.

**Part 2 — Principle Reflection**: Reads the project's iron rules and driving manual, prompts the agent to reflect on whether it's following them. Includes a "Write It Down" check for unsaved information.

## Core Principles

### "Write It Down or Lose It"

The first and most important principle. All information in AI context is temporary. If something important isn't written to a file AND registered in FILE_INDEX, it will be lost. Better to write one extra file than to let information vanish.

### Single Source of Truth

Each fact is maintained in only one document:
- Current state → CURRENT_STATUS.md
- File catalog → FILE_INDEX.md
- Historical details → WORKLOG.md
- Project overview/rules → CLAUDE.md

### Phase Transitions

When work shifts to a new goal, a five-step protocol ensures no data is lost:
1. Copy car body to WORKLOG (protect data first)
2. Compress to tire track summary
3. Trim old tire tracks
4. Clear car body for new phase
5. Update CLAUDE.md status

Step 1 executes first — even if the process is interrupted, data is safe.

## Languages

- `skill/` — English version (default)
- `skill-zh/` — Chinese (中文) version

Install whichever matches your working language.

## Requirements

- [Claude Code](https://claude.ai/code) (CLI, desktop app, or IDE extension)
- No other dependencies

## FAQ

**Q: Does this work with other AI tools besides Claude Code?**
A: The skill mechanism is Claude Code specific, but the documentation system itself is universal. Any AI agent that reads markdown files can follow the operational rules embedded in CLAUDE.md.

**Q: How much overhead does this add?**
A: Minimal. During work, you update CURRENT_STATUS after each meaningful step (~1 line) and register new files in FILE_INDEX (~1 line). The `/doc-harness check` takes about 2 minutes.

**Q: Can I customize the document structure?**
A: Yes. The templates are starting points. Add sections to CLAUDE.md, customize FILE_INDEX categories, adjust the driving manual to your needs. The only hard rules are: keep the four core documents, follow the phase transition protocol, and register all files.

**Q: What if I have multiple related projects?**
A: Each project gets its own Doc Harness. A parent directory can have a lightweight CLAUDE.md that links to all sub-projects. See the spec for details on project groups.

## License

[MIT](LICENSE)

## Credits

Designed and developed through collaborative iteration between a human researcher and AI agents, with multiple rounds of blind testing, architectural review, and real-world validation.
