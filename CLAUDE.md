# Doc Harness — Entry Document

**Last updated**: 2026-04-03
**Current phase**: Independent project setup (⏳)
**One-line status (as of 2026-04-03)**: v1.1 stable. Migrated from project_reorganization to standalone project. GitHub repo active. Installed at user + project level. Awaiting community feedback.

---

## Recovery Chain

1. Read this file → project scope, iron rules, technical info
2. Read `CURRENT_STATUS.md` → what's done, what's active, next steps
3. As needed: `FILE_INDEX.md` → find specific files
4. As needed: `WORKLOG.md` → historical context

## Project Overview

Doc Harness is a Claude Code skill that provides document-based project control for AI-human collaboration. It creates and maintains 5 status documents per project (CLAUDE.md, CURRENT_STATUS.md, FILE_INDEX.md, WORKLOG.md, DOC_HARNESS_SPEC.md) that enable any agent or human to understand and resume project work purely from reading files.

**Two subcommands**: `/doc-harness init` (create docs) and `/doc-harness check` (audit + reflect).

**Core principle**: "Write It Down or Lose It" — context info is temporary, files are permanent.

**Origin**: Designed and validated in `D:\Projects\project_reorganization\` (7 phases, 2026-04-01 ~ 04-03), then published as standalone skill.

## Project-Level Iron Rules

1. **中英文版本永远同步**: Every change to skill/ must be mirrored to skill-zh/, and vice versa. No exceptions.
2. **Doc Harness adapts to project, not project to Doc Harness**: The skill must accommodate diverse project structures. Never impose rigid templates that break existing workflows.
3. **spec.md is the authoritative specification**: All other files (operational_rules.md, init.md, check.md, README) derive from spec.md. Contradictions are resolved in favor of spec.md.
4. **Test before release**: Every change must be validated (blind test, real project test, or simulation) before pushing to GitHub or updating installed copies.
5. **Deployment sync**: After any change, update all 3 locations: dev source → GitHub push → installed copies (user-level + project-level).

## Key Technical Information

**GitHub**: https://github.com/cilidinezy-commits/doc-harness (tag v1.1)
**License**: MIT

**File structure**:
```
doc-harness/
├── skill/           ← English skill files (5 files, authoritative)
├── skill-zh/        ← Chinese skill files (5 files, synced)
├── README.md        ← English project description
├── README_zh.md     ← Chinese project description
└── LICENSE          ← MIT
```

**Deployment locations** (installed copies must match dev source):
- User-level: `~/.claude/skills/doc-harness/` ← from `skill/`
- Project-level (ObsVault_Tools): `.claude/skills/doc-harness/` ← from `skill/`

**Skill files** (same structure in both skill/ and skill-zh/):
| File | Role |
|------|------|
| SKILL.md | Entry point + router |
| init.md | `/doc-harness init` — create 5 docs |
| check.md | `/doc-harness check` — audit + reflect |
| operational_rules.md | Rules embedded in each project's CLAUDE.md (~110 lines) |
| spec.md | Complete specification (~830 lines, 12 chapters + 4 appendices) |

## Doc Harness — Operational Rules

> Complete specification: see `DOC_HARNESS_SPEC.md` in this directory.

### Core Principle: "Write It Down or Lose It"

Important information must be **written to a file** and **registered in FILE_INDEX**. Not written = lost. Not registered = undiscoverable = effectively lost.

### Four Core Documents

| Document | Role | When to update |
|----------|------|---------------|
| **CLAUDE.md** | Project entry | Phase transitions; one-line status every session end |
| **CURRENT_STATUS.md** | Active status | Every session |
| **FILE_INDEX.md** | File catalog by category | When files created/deleted |
| **WORKLOG.md** | Complete history (append-only) | Phase transitions |

### Session End Checklist

- [ ] CURRENT_STATUS reflects all work?
- [ ] Next steps accurate?
- [ ] Dates refreshed?
- [ ] New files registered in FILE_INDEX?
- [ ] Anything unsaved? → Write it down!
