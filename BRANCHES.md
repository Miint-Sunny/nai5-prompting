# 主线与版本

**`main` 是拆分版，也是主要版本。** 按任务组织的十一个技能放在 `skills/`；日常维护围绕它们使用的共同方法与入口进行。

| 分支 | 内容 | 维护方式 |
| --- | --- | --- |
| [`main`](https://github.com/Miint-Sunny/nai5-prompting/tree/main) | 拆分版：十一个按任务组织的技能 | 主要版本，按职责维护共同方法和入口 |
| [`merged`](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) | 合并版：一个入口、构思与写法两卷 | 脚本从同一批方法源自动合并 |
| [`single`](https://github.com/Miint-Sunny/nai5-prompting/tree/single) | 单文件版：一个入口、完整合订稿 | 脚本从同一批方法源自动合订 |

本地公开仓与 GitHub 使用相同的三条分支。每条分支保留对应形式的技能目录；三种当前安装包统一放在各分支的 `packs/v1.2e/`，单技能小包位于其 `individual/` 子目录。`main` 的 `skills/` 只放技能目录，历史版本从 Releases 获取。合并版和单文件版不分别维护内容；修改共同源后重新生成并更新分支，不能在生成副本中单独改稿。

未指定形式时，默认配置全部拆分技能，执行时优先从拆分技能中按需读取；合并版与单文件版仅在用户明确指定时使用。历史内容以标签查询。v1.2e 的方法内容来自 `v1.2-next-preview.11-20261009`；当前分支补充安装说明，技能正文和已发布 ZIP 保持原字节。各分支 `SOURCE.json` 记录对应形式、当前装配来源及文件哈希。当前预发布为 [v1.2e-nightly（2026-10-09）](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2e)，标签 `v1.2e` 固定本次 main 拆分版，Release 同时提供合并版和单文件版附件。其他形式的对应提交见 Release 说明。v1.2c、v1.2b、v1.1 等历史标签与附件保留，v1.1 仍是稳定 Latest。

NovelAI Harness、Plana-App 和 Ultimate NovelAI launcher 各自维护应用适配。本仓提供通用内容技能，工作台操作依赖对应应用与工具；验证范围见 [发布说明](RELEASE_NOTES.md)。
