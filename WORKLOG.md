# WORKLOG — Doc Harness

## Table of Contents
| Phase | Period | Anchor |
|-------|--------|--------|
| Phase 2: Independent project | 2026-04-03 | [→](#phase-2-independent-project-setup-2026-04-03) |
| Phase 1: Design → publish (in project_reorganization) | 2026-04-01 ~ 04-03 | [→](#phase-1-design-development-and-publishing-2026-04-01--2026-04-03) |

---

## Phase 2: Independent Project Setup (2026-04-03)

### Summary
Migrated from `project_reorganization/github-repo/` to `D:\Projects\doc-harness\` as standalone project. Applied Doc Harness to self. No code changes — purely organizational.

### Details
- Copied `D:\Projects\project_reorganization\github-repo\` → `D:\Projects\doc-harness\` (with .git history preserved)
- Created CLAUDE.md, CURRENT_STATUS.md, FILE_INDEX.md, WORKLOG.md, DOC_HARNESS_SPEC.md
- Documented deployment relationship (dev source → GitHub → installed copies)
- Iron rules established: bilingual sync, adapt-to-project, spec-authoritative, test-before-release, deployment-sync

---

## Phase 1: Design, Development, and Publishing (2026-04-01 ~ 2026-04-03)

### Summary
Complete lifecycle executed within the `project_reorganization` project. From initial concept to published v1.1 with 6 real-world applications.

### Milestone Timeline
| Date | Milestone |
|------|-----------|
| 04-01 | Spec v0.1 drafted (9 chapters + 2 appendices) |
| 04-02 | Three-way review (practical/architect/stress-test) → v0.2 → v1.0 |
| 04-02 | Skill developed: /doc-harness (init + check), 5 rounds of testing |
| 04-02 | GitHub publish (cilidinezy-commits/doc-harness), README 4 iterations |
| 04-02 | Chinese version (skill-zh/) created and synced |
| 04-02 | Applied to journal_ch5, WhoAMI, lit_review |
| 04-02 | BH_AgentsModel deep application, lit_review quality refinement |
| 04-02 ~ 03 | ZY_DoctorThesis (1504 files), notes/ sub-index (126 files) |
| 04-03 | v1.1: 10 improvements analyzed → 7 kept, 3 dropped → implemented |
| 04-03 | Backup notices at old locations, MEMORY.md updated |

### Key Design Decisions
- "Write It Down or Lose It" as first principle (user insight: context info is ephemeral)
- "Moving car" metaphor for CURRENT_STATUS (tire tracks / car body / headlights / driving manual)
- Two-level principles: project iron rules (permanent) + phase driving manual (temporary)
- 5-step phase transition protocol (data protection first)
- Spec as two versions: operational (~110 lines, embedded) + complete (~830 lines, reference)

### v1.1 Improvements
- 7 implemented: mid-project adoption, SUPERSEDED-but-retained, spec check, FILE_INDEX script, phase coherence, adapt-to-project, sub-index guidance
- 3 dropped after deep analysis: car body threshold (wrong metric), completed-project template (adds complexity), small-project lite rules (consistency > brevity)

Full details: `D:\Projects\project_reorganization\WORKLOG.md` §阶段2-7
