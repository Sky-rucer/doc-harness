# Doc Harness Codex 维护说明

这份文档面向维护你自己的 Codex 兼容 fork 分支的人。

## 目标

同时满足三件事：

1. 本地能在 Codex 中直接安装使用
2. 能持续同步原作者的最新修改
3. 你自己的兼容改动可以长期存在，并在合适时向上游提交 PR

## 推荐仓库结构

- `upstream`：原作者仓库 `cilidinezy-commits/doc-harness`
- `origin`：你自己的 fork
- 工作分支：`codex-compat-zh`

不要直接在 `master` 上做 Codex 改动。

## 推荐更新流程

### 合并式

```powershell
git fetch upstream
git checkout codex-compat-zh
git merge upstream/master
```

### 变基式

```powershell
git fetch upstream
git checkout codex-compat-zh
git rebase upstream/master
```

如果你已经把这个分支推送并长期使用，通常 `merge` 更稳；如果你想保持提交历史更干净，可以用 `rebase`。

## 合并时优先级

### 优先保留上游内容

- 协议定义
- 文档结构
- 初始化逻辑
- 检查逻辑
- spec 章节变化

### 仅保留你的最小兼容改动

- `~/.codex/skills/...` 安装说明
- Codex 使用自然语言触发的说明
- 针对 Claude 专属 slash command 的替代提示
- 单独的 `codex_notes.md`

## 高风险冲突文件

- `skill-zh/SKILL.md`
- `skill-zh/init.md`
- `skill-zh/check.md`
- `skill-zh/operational_rules.md`
- `README_zh.md`

如果这些文件上游有大改，你要先理解上游新增的规则，再把你的 Codex 说明重新贴回去，不要机械地用旧版本覆盖新版本。

## 推荐策略

把 Codex 兼容内容尽量集中到少数文件：

- `skill-zh/codex_notes.md`
- `skill/codex_notes.md`
- `README_zh.md` 中的 Codex 小节

这样以后上游更新时，你通常只需要：

1. 先吃下上游修改
2. 再确认这些少量 Codex 说明是否还成立
3. 如有必要做极小修补

## 更新后本地重装

合并或 rebase 完成后，把 `skill-zh` 重新复制到本地 Codex skills 目录：

```powershell
Copy-Item -Recurse -Force .\skill-zh "$env:USERPROFILE\.codex\skills\doc-harness"
```

然后重启 Codex。
