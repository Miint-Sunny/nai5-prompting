# 主线与版本

**`main` 是拆分版，也是主要版本。** 按任务组织的十一个技能放在 `skills/`；日常维护围绕它们使用的共同方法与入口进行。

| 分支 | 内容 | 维护方式 |
| --- | --- | --- |
| [`main`](https://github.com/Miint-Sunny/nai5-prompting/tree/main) | 拆分版：十一个按任务组织的技能 | 主要版本，按职责维护共同方法和入口 |
| [`merged`](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) | 合并版：一个入口、构思与写法两卷 | 脚本从同一批方法源自动合并 |
| [`single`](https://github.com/Miint-Sunny/nai5-prompting/tree/single) | 单文件版：一个入口、完整合订稿 | 脚本从同一批方法源自动合订 |

本地公开仓与 GitHub 使用相同的三条分支。每条分支只放对应形式及其下载文件。合并版和单文件版不分别维护内容；修改共同源后重新生成并更新分支，不能在生成副本中单独改稿。

三种形式选择一种使用，历史内容以标签查询。本次方法基于 `v1.2-next-preview.8-20261009`，来源仍为 `7025c6a18d6ce820217511ef19b639495ec47d80`。各分支 `SOURCE.json` 记录对应形式、方法与文件哈希。当前预发布为 [v1.2d-nightly（2026-10-09）](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2d)，标签 `v1.2d` 固定本次 main 拆分版，Release 同时提供合并版和单文件版附件。其他形式的对应提交见 Release 说明。v1.2c、v1.2b、v1.1 等历史标签与附件保留，v1.1 仍是稳定 Latest。

NovelAI Harness、Plana-App 和 Ultimate NovelAI launcher 各自维护应用适配。本仓提供通用内容技能，工作台操作依赖对应应用与工具；验证范围见 [发布说明](RELEASE_NOTES.md)。
