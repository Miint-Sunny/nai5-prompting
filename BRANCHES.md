# 主线与版本

**`main` 是拆分版，也是主要版本。** 按任务组织的十一个技能放在 `skills/`；日常维护围绕它们使用的共同方法与入口进行。

| 分支 | 内容 | 维护方式 |
| --- | --- | --- |
| [`main`](https://github.com/Miint-Sunny/nai5-prompting/tree/main) | 拆分版：十一个按任务组织的技能 | 主要版本，按职责维护共同方法和入口 |
| [`merged`](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) | 合并版：一个入口、构思与写法两卷 | 脚本从同一批方法源自动合并 |
| [`single`](https://github.com/Miint-Sunny/nai5-prompting/tree/single) | 单文件版：一个入口、完整合订稿 | 脚本从同一批方法源自动合订 |
| [`mini`](https://github.com/Miint-Sunny/nai5-prompting/tree/mini) | 极简版：一个技能 `nai5-mini`，全是平常话，只管普通单幅插画 | 独立维护，第二顺位；源文单独维护，不从拆分版生成 |
| [`gemini`](https://github.com/Miint-Sunny/nai5-prompting/tree/gemini) | strict-safe 版（Gemini 防拦截）的源文件（`gemini/nai5-art-studio/`）和维护记录 | Gemini 单独维护，不并入 `main`；发布时打包成 `nai5-strict-safe-*.zip` |

本地公开仓与 GitHub 使用相同的分支。四条形式分支各保留对应形式的技能目录；四种当前安装包、strict 版和 strict-safe 版统一放在这四条分支的 `packs/v1.2.8/`，单技能小包位于其 `individual/` 子目录。`main` 的 `skills/` 只放技能目录，历史版本从 Releases 获取。合并版和单文件版不分别维护内容；修改共同源后重新生成并更新分支，不能在生成副本中单独改稿。极简版单独维护，改源文后同样只通过发布脚本更新分支。

未指定形式时，默认配置全部拆分技能，执行时优先从拆分技能中按需读取；极简版、合并版与单文件版仅在用户明确指定时使用；strict 版给导入拆分版失败的环境（比如 Gemini 网页）；strict-safe 版（Gemini 防拦截）只在 Gemini 里被安全拦截时使用。v1.2.8 的方法基线为 `v1.2-next-preview.30-20261102`，拆分版、合并版、单文件版从同一批源生成；极简版单独维护。各分支 `SOURCE.json` 记录对应形式、来源及文件哈希。当前正式版为 [v1.2.8（2026-11-02）](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2.8)，Latest；标签 `v1.2.8` 固定本次 main 拆分版，Release 同时提供极简版、合并版、单文件版附件以及 strict 版和 strict-safe 版。各形式的对应提交见 Release 说明。历史标签与附件保留。

NovelAI Harness、Plana-App 和 Ultimate NovelAI launcher 各自维护应用适配。本仓提供通用内容技能，工作台操作依赖对应应用与工具；验证范围见 [发布说明](RELEASE_NOTES.md)。

strict 版每次发版从拆分版自动封装成一个技能，正文和拆分版相同，给导入要求严格的环境（比如 Gemini 网页）；strict-safe 版（Gemini 防拦截）由 Gemini 在 `gemini` 分支维护，内容跟进通用版会晚一些，打包后随发布附上。旧的 Gemini 适配包（1.2、1.2.5）不再随新版提供：1.2 包在 v1.2 至 v1.2.6 的 [Release](https://github.com/Miint-Sunny/nai5-prompting/releases) 附件里，1.2.5 包在 v1.2.5 的附件里。
