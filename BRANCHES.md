# 分支协作

共同构思与写法只维护一份，各分支承载不同的交付形态或运行环境。分支存在不代表该环境已完成适配；具体可用范围以分支 README 为准。

| 分支 | 用途与当前基线 |
|---|---|
| `main` | 稳定版，保持 v1.1 正式交付 |
| `develop` | 已审通用整合稿与日常开发，承接当前 nightly |
| `experiment/skill-split` | 从通用整合稿拆出任务入口，当前为通用 LLM 的普通画面、漫画、服装三个包 |
| `adapt/novelai-harness` | 在拆分成果上接 NovelAI Harness 工具，当前为三个内容包和工作台写入包 |
| `adapt/plana-app` | 为 [Plana-App](https://github.com/mc5024/Plana-App) 预留独立适配，以通用 LLM 三包起步，尚未完成运行时适配 |
| `adapt/ultimate-launcher` | 为 [Ultimate_Novelai_launcher](https://github.com/Miint-Sunny/Ultimate_Novelai_launcher) 预留独立适配，以通用 LLM 三包起步，尚未完成运行时适配 |

## 改动如何回流

通用方法改进回到 `develop` 的共同源，经核对后同步各分支；不要在每个任务包或适配分支手写一套通用规则。拆分实验验证后，将可复用的入口、结构或通用改进选取回 `develop`。应用专用工具、字段与调用差异留在对应适配层，不反向成为通用 LLM 的必需依赖。

Plana-App 与 Ultimate_Novelai_launcher 是独立目标。后者存在 `plana_adapter`，不表示两者共用完整运行时，也不证明任一应用提供 Harness 工具。每个适配分别核对实际接口、装载方式和可完成任务。

正式发布以审定的发布树晋升 `main`，不把实验分支全部合入当成发布。此次公开仓的 `main` 通过追加提交从 nightly 恢复稳定内容；该历史仍保留，因此不能指望简单合并旧 `develop` 自动恢复被撤回的 nightly 内容，下一次晋升应以目标发布树明确核对。

已有标签与 Release 保留。分支整理本身不改发布记录；发布与推送另按对应任务执行。
