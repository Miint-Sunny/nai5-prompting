# NovelAI V5 构思与写法 · 拆分版 · v1.2e-nightly

本项目为 AI agent 提供 NovelAI V5 创作与提示词撰写方法，涵盖整体构思、场景、艺术表达、OC、插画构图、漫画、服装及照图反推。

**默认完整安装 11 个通用技能，使用时按任务读取相关技能和章节。** 拆分结构用于区分职责与按需读取，无需由用户在每次任务前重新选择安装包。

<a id="quick-start"></a>

## 安装与开始使用

以下步骤适用于支持 Skill 安装、附件读取和文件管理的 agent。

1. **下载完整拆分包**：[nai5-split-v1.2e.zip](packs/v1.2e/nai5-split-v1.2e.zip)。
2. **将 ZIP 拖入 agent 对话**，发送以下安装请求：

   ```text
   请将此压缩包中的 11 个通用技能全部安装到当前环境的技能目录，保留每个技能的完整目录及资源。安装后确认 11 个技能均可被识别和调用。执行任务时，根据我的需求选择相关技能，并按需读取所需章节。
   ```

3. **确认安装完成后，直接描述任务**。例如，提出 OC 设计需求，或要求将已确定的方案转换为 NAI V5 提示词。agent 根据任务选择所需技能；如果客户端要求刷新或重启，按其提示完成。

安装由 agent 处理，无需手动解压或双击 `SKILL.md`。`SKILL.md` 是供 agent 读取的 Markdown 入口文件；其引用的方法位于 `references/` 等资源目录中。完整技能目录需要一起保留。缺少 Skill 或文件安装能力的聊天工具不适用上述流程，应先使用支持这些能力的 agent。

## 安装与读取的区别

| 阶段 | 本项目的使用方式 |
| --- | --- |
| 安装 | 一次安装同版本的全部 11 个通用技能及资源。 |
| 可用状态 | 客户端如有技能启用开关，将这 11 个技能设为可用，供 agent 选择。 |
| 执行任务 | agent 根据请求选择相关入口，再读取本次需要的正文和参考章节。完整安装不要求每次读取全部正文。 |

按需读取需要客户端提供相应的技能发现与资源读取机制。例如，Codex 先使用技能名称和描述进行匹配，再读取选中技能的正文；其他客户端以其实际机制为准。参见 [OpenAI 官方技能说明](https://learn.chatgpt.com/docs/build-skills)。

已有构思或定稿时，直接进入对应阶段；用户给定的内容和修改范围继续保留。仅请求构思、角色、服装或分镜时，交付相应方案；请求提示词时再进入写法。漫画、服装写法和照图反推读取同版本 `nai5-writing` 提供的共同规则。

本项目提供方案与提示词。生成图片时，将最终提示词用于 NovelAI；自动填写界面或调用生图服务需要另行配置相应工具。

## 版本与下载

**拆分版是主要维护形式。** 合并版和单文件版由相同方法源生成；三种形式选择一种安装。

| 版本与下载 | 内容 | 安装方式 |
| --- | --- | --- |
| **[拆分版（推荐）](packs/v1.2e/nai5-split-v1.2e.zip)** | 11 个按职责组织的技能 | 完整安装 11 个技能，运行时按需读取。 |
| [合并版（构思／写法两卷）](packs/v1.2e/nai5-merged-v1.2e.zip) | 一个入口与两卷完整方法 | 安装一个完整技能包，按任务读取相关卷和章节。 |
| [单文件版](packs/v1.2e/nai5-single-v1.2e.zip) | 一个入口与完整合订稿 | 安装一个完整技能包，按任务读取相关章节。 |

三种当前安装包均位于 `packs/v1.2e/`，无需切换分支下载。单技能小包集中在 `packs/v1.2e/individual/`；`skills/` 仅保留技能目录。历史版本从 [Releases](https://github.com/Miint-Sunny/nai5-prompting/releases) 获取。

支持多技能 ZIP 导入的客户端可直接导入拆分合集；一次只能导入一个技能时，将下表的 11 个小包全部依次导入。若客户端只能安装一个技能，可选择合并版或单文件版。GitHub 自动生成的仓库源码 ZIP 用于获取源码，技能安装使用本页列出的安装包。

合并版和单文件版均使用 `nai5-prompting` 名称，切换时替换同名技能。与拆分版切换时，停用原形式，避免同时加载两份相同方法。

当前版本为 **v1.2e-nightly（2026-10-09）**，方法来自 `v1.2-next-preview.11-20261009`。本次说明修订不改变已发布的技能正文和安装包。三个附件集中在 [v1.2e Release](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2e)，稳定 Latest 为 v1.1。修订记录和验证范围见 [发布说明](RELEASE_NOTES.md)。

<a id="split-skills"></a>

## 技能职责与单独下载

下表用于了解各技能的职责、查阅正文或逐个导入。默认安装范围仍为全部 11 个通用技能，任务执行不要求依次使用所有技能。

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
