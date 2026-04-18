# Doc Harness for Codex

## Codex notes

- This skill works in Codex as a normal markdown skill.
- In Codex, prefer natural-language invocation instead of Claude Code slash commands.
- Example prompts:
  - `use doc-harness to initialize this project`
  - `use doc-harness to check project documentation health`

## Install location

- Upstream Claude Code path: `~/.claude/skills/doc-harness`
- Codex path: `~/.codex/skills/doc-harness`

## Why `CLAUDE.md` stays unchanged

- The upstream method is built around `CLAUDE.md`, `CURRENT_STATUS.md`, `FILE_INDEX.md`, and `WORKLOG.md`.
- This Codex compatibility branch keeps those filenames unchanged to minimize divergence and make upstream sync practical.
- In Codex, the skill can still instruct the agent to read those files explicitly.
