# Doc Harness for Codex

## Codex 使用说明

- 本 skill 可以直接安装到 Codex 的 skills 目录中使用。
- 在 Codex 中，优先使用自然语言触发，不依赖 Claude Code 的 `/doc-harness` 斜杠命令。
- 推荐说法：
  - `use doc-harness to initialize this project`
  - `用 doc-harness 为这个项目初始化文档系统`
  - `use doc-harness to check project documentation health`
  - `用 doc-harness 检查当前项目文档健康状态`

## 安装位置

- Claude Code 上游写法：`~/.claude/skills/doc-harness`
- Codex 对应位置：`~/.codex/skills/doc-harness`
- Windows 当前用户通常是：`C:\Users\<用户名>\.codex\skills\doc-harness`

## 为什么不重命名 `CLAUDE.md`

- 这个仓库的上游规范围绕 `CLAUDE.md`、`CURRENT_STATUS.md`、`FILE_INDEX.md`、`WORKLOG.md` 展开。
- 为了最小化与上游的差异、保留后续合并更新的可维护性，这个 Codex 适配分支保留这些文件名不变。
- 在 Codex 中，这些文件依然可用，因为 skill 会明确指导代理读取它们。

## Codex 适配范围

- 已适配：安装路径说明、调用方式说明、Codex 使用提示
- 未改动：核心文档协议、阶段切换规则、文件命名体系
- 保持不变的目的是：便于持续同步上游 `master`
