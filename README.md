# NovelAI V5 构思与写法 · 拆分版 · v1.2d-nightly

**拆分版是主要版本。** `main` 按任务提供十一个技能，日常维护围绕各项方法与技能入口进行。合并版和单文件版由同一批方法源自动生成，分别放在 `merged`、`single` 分支；三种形式选择一种使用。

内容覆盖整体想法、场景、艺术表达、OC、插画构图、漫画与服装设计、照图反推，以及将已定方案写成 NovelAI Diffusion V5 提示词。已有想法或定稿可直接进入对应阶段。

| 版本与下载 | 包里是什么 | 使用方式 |
| --- | --- | --- |
| **[拆分版（主要版本）](downloads/nai5-split-v1.2d.zip)** | 十一个按任务划分的技能 | 启用本次需要的技能；也可从下表逐个下载 |
| [合并版（构思／写法两卷）](https://github.com/Miint-Sunny/nai5-prompting/blob/merged/downloads/nai5-merged-v1.2d.zip) | 一个入口＋构思卷、写法卷 | 由共同方法自动合并，写法卷含全部专项补充 |
| [单文件版](https://github.com/Miint-Sunny/nai5-prompting/blob/single/downloads/nai5-single-v1.2d.zip) | 一个入口＋完整合订稿 | 由共同方法自动合订，按章节阅读 |

本版为 **v1.2d-nightly（2026-10-09）**，下载也集中在 [v1.2d Release](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2d)。方法基于 `v1.2-next-preview.8-20261009`，包含近期文稿、读取条件和例子使用修订；10-08 确定拆分主线及独立形式分支。本次发布统一版本标识，方法内容沿用已核候选。稳定 Latest 仍为 v1.1；修订与验证范围见 [发布说明](RELEASE_NOTES.md)。

下载表中的 ZIP 后在客户端导入；不要导入整个仓库的源码 ZIP。拆分版 ZIP 面向支持多技能导入的客户端；只支持单技能导入时，分别下载下表中需要的小包。漫画、服装写法补充和照图反推需同时启用本版 **通用 NAI5 写法**。

合并版与单文件版均安装为 `nai5-prompting`，导入另一种时替换同名技能。从这两种完整包切换到拆分版时停用旧完整包；反向切换时停用原拆分技能，避免重复启用同一套方法。

## 怎样使用这些技能

**按当前任务选包，不必全装。** 只要想法装整体想法；场景、艺术表达、OC、构图、漫画分镜、服装设计各装对应的构思包；手里已有定稿要词句装通用写法，漫画、服装、照图再各加一个补充包。

**已有内容直达。** 有想法就从专项构思进，有定稿就从写法进；模型沿用你已经给定的内容、细节、确认和修改范围，不重走前面的阶段，也不要求填交接表。只装了写法包时，说「想画……」模型会直接给完整提示词；想先聊想法，就装构思包，或者明说「先构思」。分镜阶段没说要词，模型会停在分镜，说「转成提示词」再转。

**补充包怎么取通用规则。** 漫画、服装写法补充和照图反推都依赖同版本的通用写法，要一起启用。没装到所需的包时，模型用现有规则完成能做的部分，说明哪些规则尚未载入，不编造规范。

**偏好是另一层。** 这三个包只讲通用方法，不带任何人的审美。想让结果更像自己或自己所在的群，可以在它之上叠一层偏好：把常画的题材、光色、机位和写词习惯写成一份补充，说「按……的路子」时启用，说「关掉偏好」就回到通用方法。偏好在维护阶段结合真实提示词、角色栏、UC、参数与画面证据整理，再由用户或本人审定。普通生成只读整理后正文，不自行回查这些原始材料来补题；只有用户明确要求整理、核对或指定作品分析时才读相应材料。这三个 ZIP 不含任何人的偏好。

<a id="split-skills"></a>

## 拆分版的技能

**通用构思找想法 → 专项构思深入题材 → 通用写法表达定稿 → 按需要加专项写法补充。**

只要想法、角色、衣服或分镜，交到该阶段即可；已有定稿要词句则直接进入写法。下表名称可打开完整入口，方法链接可直接阅读正文。

| 技能与用途 | 方法全文 | 单独下载 |
|---|---|---|
| [整体想法](skills/nai5-ideas/SKILL.md)：主题、关系与故事种子 | [想法](skills/nai5-ideas/references/ideas.md) | [ZIP](skills/nai5-ideas-v1.2d.zip) |
| [场景与情境](skills/nai5-scene-design/SKILL.md)：环境、空间与气氛 | [场景](skills/nai5-scene-design/references/scene.md) | [ZIP](skills/nai5-scene-design-v1.2d.zip) |
| [艺术表达](skills/nai5-art-direction/SKILL.md)：情绪、光色、媒介与风格，含具象和写实 | [艺术](skills/nai5-art-direction/references/art.md) | [ZIP](skills/nai5-art-direction-v1.2d.zip) |
| [OC 整体设计](skills/oc-character-design/SKILL.md)：角色核心、行为与外形辨识 | [角色](skills/oc-character-design/references/character.md) | [ZIP](skills/oc-character-design-v1.2d.zip) |
| [插画构图](skills/nai5-illustration-composition/SKILL.md)：已有想法变成具体画面 | [构图](skills/nai5-illustration-composition/references/composition.md) | [ZIP](skills/nai5-illustration-composition-v1.2d.zip) |
| [漫画架构与分镜](skills/nai5-comic-storyboard/SKILL.md)：故事、页格与连续性 | [架构](skills/nai5-comic-storyboard/references/comic-story.md) · [布局](skills/nai5-comic-storyboard/references/comic-layout.md) · [连续性](skills/nai5-comic-storyboard/references/comic-continuity.md) | [ZIP](skills/nai5-comic-storyboard-v1.2d.zip) |
| [服装设计](skills/oc-costume-design/SKILL.md)：轮廓、部件、配色与材质 | [服装设计](skills/oc-costume-design/references/costume.md) | [ZIP](skills/oc-costume-design-v1.2d.zip) |
| [通用 NAI5 写法](skills/nai5-writing/SKILL.md)：共同语法、字段、普通画面与精确改词 | [共同规范](skills/nai5-writing/references/conventions.md) · [普通画面](skills/nai5-writing/references/illustration.md) | [ZIP](skills/nai5-writing-v1.2d.zip) |
| [漫画写法补充](skills/nai5-comic-writing/SKILL.md)：已定分镜转主串、角色串与 UC | [漫画编译](skills/nai5-comic-writing/references/comics.md) · [示例](skills/nai5-comic-writing/references/comic-examples.md) | [ZIP](skills/nai5-comic-writing-v1.2d.zip) |
| [服装写法补充](skills/nai5-costume-writing/SKILL.md)：已定衣物的片段或完整画面表达 | [服装表达](skills/nai5-costume-writing/references/costume.md) | [ZIP](skills/nai5-costume-writing-v1.2d.zip) |
| [照图反推](skills/nai5-reverse-prompt/SKILL.md)：照图写提示词，或只推其中一部分 | [照图反推](skills/nai5-reverse-prompt/references/reverse.md) | [ZIP](skills/nai5-reverse-prompt-v1.2d.zip) |

合并版见 [`merged` 分支](https://github.com/Miint-Sunny/nai5-prompting/tree/merged)，单文件版见 [`single` 分支](https://github.com/Miint-Sunny/nai5-prompting/tree/single)。两者都由脚本从拆分版使用的共同方法自动合并，修改方法后统一重建；本地公开仓使用相同的三条分支。

## 导入与读取说明

ZIP 中保留合法技能目录，只写文件条目，各技能的 `SKILL.md` 在其资源前面。合并版／单文件版各有一个技能；拆分版包含十一个平级技能目录，ZIP 根层不混入说明文件或其他 ZIP。

使用技能资源工具时，路径相对当前技能目录，不再加技能名前缀或 Markdown 章节锚点。若使用通用文件读取工具，应从宿主提供的技能位置解析路径，不能用图片输出目录猜测。文件列表或 ZIP 的排列顺序不等于模型应逐个读取所有文件。

这些包提供内容方法与可填写的词句，适合能读取相应文件的 LLM 客户端。Harness 可复用内容方法，但本发布不包含工作台操作包；实际写入仍依赖相应适配工具，不因导入成功就具备工具能力或自动生图能力。

已知验证范围见 [发布说明](RELEASE_NOTES.md)。不承诺所有 agent、全部 Windows 界面或生图效果均已验证。来源与同源文件对应见 [SOURCE.json](SOURCE.json)，下载后可用 [SHA256SUMS.txt](SHA256SUMS.txt) 核对文件。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。所有包装保留完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE)，项目贡献按 GNU GPL version 3（GPL-3.0-only）提供。项目公开来源：[nai5-prompting](https://github.com/Miint-Sunny/nai5-prompting)。
