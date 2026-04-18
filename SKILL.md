---
name: doc-harness
description: "Doc Harness：基于文档的项目控制系统。此仓库作为整仓安装到 Codex 全局 skills 时使用本入口文件。优先使用自然语言触发 doc-harness，为项目初始化文档系统或检查文档健康状态。"
argument-hint: "init [项目名] [描述] | check"
allowed-tools: Read, Write, Bash, Glob, Grep
---

# Doc Harness — Repository Skill Entry

这是 `doc-harness` 仓库根级别的 Codex skill 入口文件。

## 使用场景

- 当你把**整个仓库**安装到 `~/.codex/skills/doc-harness` 时，Codex 通过本文件识别该 skill。
- 实际中文说明与操作细节位于：
  - [skill-zh/SKILL.md](skill-zh/SKILL.md)
  - [skill-zh/init.md](skill-zh/init.md)
  - [skill-zh/check.md](skill-zh/check.md)
  - [skill-zh/operational_rules.md](skill-zh/operational_rules.md)
  - [skill-zh/spec.md](skill-zh/spec.md)

## Codex 说明

- 在 Codex 中，优先使用自然语言，不依赖 Claude Code 的 `/doc-harness` 斜杠命令。
- 推荐说法：
  - `用 doc-harness 为这个项目初始化文档系统`
  - `用 doc-harness 检查当前项目文档健康状态`
- 为了方便持续同步上游，本仓库保留上游的核心文件命名体系，例如 `CLAUDE.md`。

## 维护说明

- Codex 兼容附加说明见 [skill-zh/codex_notes.md](skill-zh/codex_notes.md)
- README 中的 Codex 安装说明见 [README_zh.md](README_zh.md)
- 长期同步上游的维护文档见 [CODEx_MAINTENANCE_zh.md](CODEx_MAINTENANCE_zh.md)
