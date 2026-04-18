# CURRENT_STATUS — Doc Harness

**Last updated**: 2026-04-19
**Current phase**: v1.2 development (⏳)

---

## Recent Completed (Tire Tracks)

### Phase 2: Independent Project Setup (2026-04-03)
Migrated from `project_reorganization/github-repo/` to standalone `D:\Projects\doc-harness\`. Doc Harness self-applied. Installed at user-level and ObsVault_Tools project-level. v1.1 stable on GitHub; community submissions active. Detailed record in WORKLOG.md § Phase 2.

### Phase 1: Design, Development, Publishing (2026-04-01 ~ 2026-04-03)
Full lifecycle in project_reorganization: spec v0.1→v1.0→v1.1, /doc-harness skill with init+check, 5 test rounds, GitHub publish, bilingual sync, 6 real-world applications. Detailed record in WORKLOG.md § Phase 1.

---

## Current Work (Car Body)

### Phase Goal

Incorporate v1.2 improvements motivated by sister-project feedback (WhoAMI 2026-04-19 proposals + SMSS 2026-04-18 mandate, both archived in `inbox/`). Scope: Recovery Chain two-layer structure + self-contained constraint; WORKLOG archival rule; optional PARKING_LOT.md and PHILOSOPHY.md; explicit rejection of inbox/outbox as doc-harness framework element. Apply v1.2 to doc-harness own docs as test-before-release.

### Completed Steps

#### Git baseline committed (2026-04-19)
- Committed Phase 2 self-apply docs (CLAUDE.md / CURRENT_STATUS.md / DOC_HARNESS_SPEC.md / FILE_INDEX.md / WORKLOG.md) that had been uncommitted since 2026-04-03 — commit `92e5358`.
- Committed inbox/ messages as traceable motivation for v1.2 — commit `d54f63d`.
- Pushed to GitHub master.

#### v1.2 design finalized (2026-04-19)
- Accepted: Recovery Chain two-layer (must-read ≤3 + task-conditional + self-contained meta-rule); WORKLOG archival at ~1000 lines with quarterly archives; optional PARKING_LOT.md and PHILOSOPHY.md (Chapter 13).
- Rejected: inbox/outbox as doc-harness element (user-held principle: doc-harness stays agnostic to inter-project communication). Rationale preserved in spec Appendix E FAQ.
- Rejected: VISION.md (role already served by CLAUDE.md Project Overview + Iron Rules).
- Rejected: dedicated "not-an-optional-doc" section in spec (defining by negation was dead weight; concept is not introduced, so no defense needed).
- Philosophy rationale (user): universal principles emerge from long-term project practice — forbidding project-level PHILOSOPHY severs principle from origin.

#### Skill files updated — English (`skill/`) (2026-04-19)
- `spec.md` v1.1 → v1.2: Chapter 2.3 Recovery Chain template rewritten (two layers + meta-rules); new §5.5 WORKLOG Archival; §11.1 Session Start replaced with "Applying Recovery Chain"; §11.3 Session End adds WORKLOG length item; Chapter 12 Anti-patterns adds three rows (self-contained dep, must-read bloat, WORKLOG bloat); new Chapter 13 Optional Long-Horizon Documents (§13.1 PARKING_LOT, §13.2 PHILOSOPHY); new Appendix E Design Choices (FAQ including inbox/outbox rationale); Appendix B updated; Version History gains v1.1 and v1.2 entries.
- `operational_rules.md`: WORKLOG archival subsection; "Session Start" → "Recovery Chain" with two layers; Session End checklist adds WORKLOG-length item; new "Optional Long-Horizon Documents" section at end.
- `SKILL.md`: five mandatory docs + two optional docs clarification.
- `init.md`: CLAUDE.md template Recovery Chain switched to two-layer.
- `check.md`: new §1.6 WORKLOG length check (old §1.6 renumbered to §1.7); new §2.5 Recovery Chain health; output format updated.

#### Skill files mirrored — Chinese (`skill-zh/`) (2026-04-19)
- All five files mirrored to v1.2 per iron rule 1 (bilingual sync).

#### DOC_HARNESS_SPEC.md re-synced (2026-04-19)
- Copied `skill/spec.md` → `DOC_HARNESS_SPEC.md` at project root (987 lines).

### Unresolved Issues

(None — all within scope)

---

## Next Steps (Headlights)

### Immediate Actions

1. Update README.md and README_zh.md with concise v1.2 What's New section.
2. Commit v1.2 work with clear message; tag `v1.2`; push to GitHub.
3. Deploy sync: copy `skill/` → `~/.claude/skills/doc-harness/` and `C:\Users\ZY\Documents\ObsVault_Tools\.claude\skills\doc-harness\`.
4. Smoke-test: run `/doc-harness check` on a live project to verify v1.2 check.md logic works.

### Future Plans

- Field-test v1.2 in 1–2 projects over the coming weeks; collect drift/rough-edge reports via inbox.
- Monitor GitHub issues and community PR (awesome-claude-skills #476, anthropics/skills #846).
- Possible v1.3 directions: automation for WORKLOG archival trigger; FILE_INDEX auto-generation script; integration patterns with external memory systems that DO exist (opt-in only).

---

## Current Working Principles (Driving Manual)

- **Bilingual sync is non-negotiable** (iron rule 1). Every English edit must land in Chinese in the same session. Don't defer.
- **Test before release** (iron rule 4). v1.2 applies itself before v1.2 ships — dogfooding is the smoke test.
- **Deployment sync is three places**: dev source → GitHub → installed copies (user-level + ObsVault_Tools). Missing any one produces inconsistent behavior.
- **Doc-harness is agnostic about inter-project concerns.** When tempted to add inbox/outbox or cross-project hooks, remember: that's a separate spec's job. Keep the skill narrow.
- **Define by what IS, not by what isn't.** If a concept isn't introduced, don't introduce it just to reject it.
