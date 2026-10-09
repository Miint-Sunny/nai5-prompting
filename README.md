# NovelAI V5 构思与写法 · 拆分版 · v1.2e-nightly

本项目为 AI agent 提供 NovelAI V5 创作与提示词撰写方法，涵盖整体构思、场景、艺术表达、OC、插画构图、漫画、服装及照图反推。

本项目提供技能文档与参考资料。“安装技能”指将完整技能目录放到客户端能够发现的位置；项目自身无需安装依赖、构建或运行服务。

**用户未指定形式时，配置全部 11 个拆分技能；执行任务时优先从拆分技能中按需读取。** 合并版和单文件版仅在用户明确指定时使用。

<a id="quick-start"></a>

## 推荐方式：将项目地址交给 agent

在支持技能、能够读取仓库并管理文件的 agent 中，直接发送：

```text
请按照这个项目的配置指南，为当前使用的 agent 配置技能：
https://github.com/Miint-Sunny/nai5-prompting

默认配置全部 11 个拆分技能，使用时优先从拆分技能中按需读取。完成后告知配置位置和可用状态。
```

agent 按照仓库中的 [INSTALL.md 配置指南](INSTALL.md)获取文件、放置到当前客户端的技能目录并核对结果。用户无需提前下载或解压；确认可用后，直接描述 OC 设计、画面构思或提示词撰写需求即可。

## 备用方式

### 下载后交给 agent

1. 下载[完整拆分包](packs/v1.2e/nai5-split-v1.2e.zip)。
2. 将 ZIP 拖入 agent 对话，说明“请将里面全部 11 个拆分技能配置到当前客户端，保留完整目录和资源，并确认可用”。
3. 配置完成后直接描述任务；如客户端提示刷新或重启，按其提示完成。

### 下载后自行配置

1. 下载并解压[完整拆分包](packs/v1.2e/nai5-split-v1.2e.zip)。如果使用 GitHub 的 Download ZIP，取解压目录内 `skills/` 下的技能文件夹。
2. 将全部 **11 个技能文件夹** 复制到客户端的技能目录，保留每个目录内的 `SKILL.md`、`references/` 及其他随附文件。[常见客户端的目录位置](INSTALL.md#manual-paths)列出了 Codex、Claude Code 和 Cursor 的个人及项目目录。
3. 在客户端确认技能可用；如未出现，按提示刷新或重启。

每个技能都应保持“技能目录／技能名／SKILL.md”的结构。`SKILL.md` 是入口文档，无需双击运行；只复制这个文件会遗漏参考资料。

## 配置与读取的区别

| 阶段 | 本项目的默认方式 |
| --- | --- |
| 配置 | 一次放置同版本的全部 11 个拆分技能及资源，供 agent 选择。 |
| 执行任务 | 优先从拆分技能中选择相关入口，再读取本次需要的正文和参考章节。 |
| 其他形式 | 用户明确指定合并版或单文件版时，再配置或读取相应形式。 |

完整配置不要求每次读取全部正文。按需读取由客户端的技能发现与资源读取机制支持；例如 Codex 先使用名称和描述匹配，再读取选中技能，见 [OpenAI 官方说明](https://learn.chatgpt.com/docs/build-skills)。

已有构思或定稿时，直接进入对应阶段；用户给定的内容和修改范围继续保留。仅请求构思、角色、服装或分镜时，交付相应方案；请求提示词时再进入写法。漫画、服装写法和照图反推读取同版本 `nai5-writing` 提供的共同规则。

本项目提供方案与提示词。生成图片时，将最终提示词用于 NovelAI；自动填写界面或调用生图服务需要另行配置相应工具。

## 版本与下载

**拆分版是主要维护形式，也是默认配置和调用的形式。** 合并版和单文件版由相同方法源生成，供用户明确选择时使用。

| 版本与下载 | 内容 | 使用方式 |
| --- | --- | --- |
| **[拆分版（推荐）](packs/v1.2e/nai5-split-v1.2e.zip)** | 11 个按职责组织的技能 | 默认完整配置 11 个技能，执行时优先按需读取。 |
| [合并版（构思／写法两卷）](packs/v1.2e/nai5-merged-v1.2e.zip) | 一个入口与两卷完整方法 | 明确选择时配置一个完整技能，按需读取相关卷和章节。 |
| [单文件版](packs/v1.2e/nai5-single-v1.2e.zip) | 一个入口与完整合订稿 | 明确选择时配置一个完整技能，按需读取相关章节。 |

三种当前安装包均位于 `packs/v1.2e/`，无需切换分支下载。单技能小包集中在 `packs/v1.2e/individual/`；`skills/` 仅保留技能目录。历史版本从 [Releases](https://github.com/Miint-Sunny/nai5-prompting/releases) 获取。

支持多技能 ZIP 导入的客户端可直接导入拆分合集；一次只能导入一个技能时，将下表的 11 个小包全部依次导入。若客户端只能配置一个技能，可由用户明确选择合并版或单文件版。通过项目地址直接配置时，从仓库的 `skills/` 获取文件即可。

合并版和单文件版均使用 `nai5-prompting` 名称。用户明确切换形式时，先核对已有配置，避免重复读取相同方法；已同时配置多种形式时，普通任务仍优先使用拆分技能。

当前版本为 **v1.2e-nightly（2026-10-09）**，方法来自 `v1.2-next-preview.11-20261009`。本次说明修订不改变已发布的技能正文和安装包。三个附件集中在 [v1.2e Release](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2e)，稳定 Latest 为 v1.1。修订记录和验证范围见 [发布说明](RELEASE_NOTES.md)。

<a id="split-skills"></a>

## 技能职责与单独下载

下表用于了解各技能的职责、查阅正文或逐个导入。默认配置范围为全部 11 个拆分技能，任务执行不要求依次使用所有技能。

| 技能与用途 | 方法全文 | 单独下载 |
|---|---|---|
| [整体想法](skills/nai5-ideas/SKILL.md)：主题、关系与故事种子 | [想法](skills/nai5-ideas/references/ideas.md) | [ZIP](packs/v1.2e/individual/nai5-ideas-v1.2e.zip) |
| [场景与情境](skills/nai5-scene-design/SKILL.md)：环境、空间与气氛 | [场景](skills/nai5-scene-design/references/scene.md) | [ZIP](packs/v1.2e/individual/nai5-scene-design-v1.2e.zip) |
| [艺术表达](skills/nai5-art-direction/SKILL.md)：情绪、光色、媒介与风格，含具象和写实 | [艺术](skills/nai5-art-direction/references/art.md) | [ZIP](packs/v1.2e/individual/nai5-art-direction-v1.2e.zip) |
| [OC 整体设计](skills/oc-character-design/SKILL.md)：角色核心、行为与外形辨识 | [角色](skills/oc-character-design/references/character.md) | [ZIP](packs/v1.2e/individual/oc-character-design-v1.2e.zip) |
| [插画构图](skills/nai5-illustration-composition/SKILL.md)：已有想法变成具体画面 | [构图](skills/nai5-illustration-composition/references/composition.md) | [ZIP](packs/v1.2e/individual/nai5-illustration-composition-v1.2e.zip) |
| [漫画架构与分镜](skills/nai5-comic-storyboard/SKILL.md)：故事、页格与连续性 | [架构](skills/nai5-comic-storyboard/references/comic-story.md) · [布局](skills/nai5-comic-storyboard/references/comic-layout.md) · [连续性](skills/nai5-comic-storyboard/references/comic-continuity.md) | [ZIP](packs/v1.2e/individual/nai5-comic-storyboard-v1.2e.zip) |
| [服装设计](skills/oc-costume-design/SKILL.md)：轮廓、部件、配色与材质 | [服装设计](skills/oc-costume-design/references/costume.md) | [ZIP](packs/v1.2e/individual/oc-costume-design-v1.2e.zip) |
| [通用 NAI5 写法](skills/nai5-writing/SKILL.md)：共同语法、字段、普通画面与精确改词 | [共同规范](skills/nai5-writing/references/conventions.md) · [普通画面](skills/nai5-writing/references/illustration.md) | [ZIP](packs/v1.2e/individual/nai5-writing-v1.2e.zip) |
| [漫画写法补充](skills/nai5-comic-writing/SKILL.md)：已定分镜转主串、角色串与 UC | [漫画编译](skills/nai5-comic-writing/references/comics.md) · [示例](skills/nai5-comic-writing/references/comic-examples.md) | [ZIP](packs/v1.2e/individual/nai5-comic-writing-v1.2e.zip) |
| [服装写法补充](skills/nai5-costume-writing/SKILL.md)：已定衣物的片段或完整画面表达 | [服装表达](skills/nai5-costume-writing/references/costume.md) | [ZIP](packs/v1.2e/individual/nai5-costume-writing-v1.2e.zip) |
| [照图反推](skills/nai5-reverse-prompt/SKILL.md)：照图写提示词，或只推其中一部分 | [照图反推](skills/nai5-reverse-prompt/references/reverse.md) | [ZIP](packs/v1.2e/individual/nai5-reverse-prompt-v1.2e.zip) |


## 资源读取与工具接续

每个技能目录包含 `SKILL.md` 及其所需资源。使用技能资源工具时，路径相对当前技能目录；使用通用文件工具时，从客户端提供的实际技能位置解析路径。ZIP 中的文件排列不决定任务执行顺序。

普通任务使用技能正文与用户提供的当前资料。历史作品、完整提示词及维护记录仅在用户明确要求核对、分析指定作品或制作变体时读取。群与个人偏好由独立资料提供；本仓的三个通用安装包不包含这些资料。

本发布不包含 Harness 工作台操作包。工作台写入和生图能力由实际环境提供，安装本技能不改变工具权限。来源与文件哈希见 [SOURCE.json](SOURCE.json)，校验清单见 [SHA256SUMS.txt](SHA256SUMS.txt)。

## 维护与许可

`main` 维护拆分版；[merged](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) 和 [single](https://github.com/Miint-Sunny/nai5-prompting/tree/single) 分别提供同源生成的合并版与单文件版。修改共同方法后统一生成各形式。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。所有包装保留完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE)，项目贡献按 GNU GPL version 3（GPL-3.0-only）提供。
