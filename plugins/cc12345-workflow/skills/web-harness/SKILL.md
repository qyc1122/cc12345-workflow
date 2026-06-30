---
name: web-harness
description: 当用户希望把本插件中的 cc12345 协作模板应用到 Web 代码仓库时使用，基于插件包内 templates 目录中的 AGENTS.md、CLAUDE.md、docs/ 和 tasks/ 模板文件。
---

# Web Harness

当一个仓库需要接入 cc12345 协作脚手架时，使用这个 skill。

## 源模板

以下文件为本插件包内的源模板。接入目标仓库时，以它们为基线复制或谨慎合并，不要直接改写插件包内模板：

- `templates/AGENTS.md`
- `templates/CLAUDE.md`
- `templates/docs/architecture.md`
- `templates/docs/conventions.md`
- `templates/docs/api.md`
- `templates/docs/decisions.md`
- `templates/tasks/todo.md`
- `templates/tasks/lessons.md`
- `templates/tasks/review.md`

## tasks 目录使用约束

1. `tasks/todo.md` 只保留当前任务状态和最近一次调整记录。
2. `tasks/todo.md` 的“使用方式”“模板”两节属于固定模板，禁止修改。
3. `tasks/review.md` 的“索引”“模板”两节属于固定模板，禁止修改。

## 工作流程

请阅读当前项目结构、配置文件、包管理文件、构建脚本和主要源码目录，把这套 cc12345 协作模板完整接入目标仓库。

接入范围：

- 根目录协作文件：
  - `AGENTS.md`
  - `CLAUDE.md`
- 项目事实文档：
  - `docs/architecture.md`
  - `docs/conventions.md`
  - `docs/api.md`
  - `docs/decisions.md`
- 任务工作流文档：
  - `tasks/todo.md`
  - `tasks/lessons.md`
  - `tasks/review.md`

执行方式：

1. 检查目标仓库中是否已有对应文件；不存在时基于源模板创建，已存在时以源模板为基线谨慎合并。
2. 合并时优先保留目标仓库中已确认的项目事实和历史记录，并保持各文件职责不变：
   - `AGENTS.md` 保留长期有效的协作规则。
   - `CLAUDE.md` 仅作为入口指向 `AGENTS.md`。
   - `docs/` 维护项目事实、约定、API 边界和长期决策。
   - `tasks/` 维护当前任务、经验和复盘，不把历史内容塞回 `todo.md`。
3. 处理 `AGENTS.md` 和 `CLAUDE.md` 时，默认保留源模板的完整内容，不要擅自简化。
4. 对 `docs/architecture.md`、`docs/conventions.md`、`docs/api.md` 按目标仓库实际情况补全内容。
5. 对 `docs/decisions.md`、`tasks/todo.md`、`tasks/lessons.md`、`tasks/review.md` 保持模板职责和结构，不擅自改写固定模板区。

要求：

- 对 `docs/` 目录下需要按项目实际补全的文件，删除或替换其中的占位内容，例如 [填写]、[路径]、[说明]。
- 补齐本地开发、测试、构建和发布命令。
- 补齐项目目录边界、共享模块边界和禁止改动项。
- 补齐请求封装、鉴权、错误处理和高风险业务边界。
- 不要编造无法从代码、配置或用户说明中确认的信息。
- 不确定的内容标记为“待确认”。
