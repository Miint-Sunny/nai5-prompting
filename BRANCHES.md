# 主线与版本

**`main` 是拆分版，也是主要版本。** 按任务组织的十一个技能放在 `skills/`；日常维护围绕它们使用的共同方法与入口进行。

| 分支 | 内容 | 维护方式 |
| --- | --- | --- |
| [`main`](https://github.com/Miint-Sunny/nai5-prompting/tree/main) | 拆分版：十一个按任务组织的技能 | 主要版本，按职责维护共同方法和入口 |
| [`merged`](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) | 合并版：一个入口、构思与写法两卷 | 脚本从同一批方法源自动合并 |
| [`single`](https://github.com/Miint-Sunny/nai5-prompting/tree/single) | 单文件版：一个入口、完整合订稿 | 脚本从同一批方法源自动合订 |
| [`mini`](https://github.com/Miint-Sunny/nai5-prompting/tree/mini) | 极简版：一个技能 `nai5-mini`，全是平常话，只管普通单幅插画 | 独立维护，第二顺位；源文单独维护，不从拆分版生成 |

本地公开仓与 GitHub 使用相同的四条分支。每条分支保留对应形式的技能目录；四种当前安装包统一放在各分支的 `packs/v1.2/`，单技能小包位于其 `individual/` 子目录。`main` 的 `skills/` 只放技能目录，历史版本从 Releases 获取。合并版和单文件版不分别维护内容；修改共同源后重新生成并更新分支，不能在生成副本中单独改稿。极简版单独维护，改源文后同样只通过发布脚本更新分支。

未指定形式时，默认配置全部拆分技能，执行时优先从拆分技能中按需读取；极简版、合并版与单文件版仅在用户明确指定时使用。v1.2 的方法基线为 `v1.2-next-preview.24-20261017`，拆分版、合并版、单文件版从同一批源生成；极简版单独维护。各分支 `SOURCE.json` 记录对应形式、来源及文件哈希。当前正式版为 [v1.2（2026-10-19）](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2)，Latest 从 v1.1 更新到 v1.2；标签 `v1.2` 固定本次 main 拆分版，Release 同时提供极简版、合并版和单文件版附件。各形式的对应提交见 Release 说明。历史标签与附件保留。

NovelAI Harness、Plana-App 和 Ultimate NovelAI launcher 各自维护应用适配。本仓提供通用内容技能，工作台操作依赖对应应用与工具；验证范围见 [发布说明](RELEASE_NOTES.md)。
