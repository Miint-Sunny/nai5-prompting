# NovelAI V5 构思与写法 · v1.2b-nightly／预发布

这是 2026-09-19 的 nightly 预发布；发布标签与 ZIP 文件名沿用 `v1.2b`，方法、附件内容和下载地址均不变。

**同一套方法，三种包装，选择一种即可。** 本次预发布接替旧 nightly 的当前下载入口，v1.1 的历史稳定发布与标签保留。内容覆盖整体想法、场景、艺术表达、OC、插画构图、漫画与服装设计，以及把已定方案写成 NovelAI Diffusion V5 提示词。已有想法或定稿就从当前阶段继续，不必从头走一遍。

| 下载 | 包里是什么 | 适合怎样用 |
|---|---|---|
| [单文件完整包](https://github.com/Miint-Sunny/nai5-prompting/releases/download/v1.2b/nai5-single-v1.2b.zip) | 一个薄入口＋完整合订稿 | 想保留一份完整方法，按章节阅读 |
| [两卷完整包](https://github.com/Miint-Sunny/nai5-prompting/releases/download/v1.2b/nai5-paired-v1.2b.zip) | 一个薄入口＋构思卷、写法卷 | 想分开阅读构思与写法；写法卷已含专项补充 |
| [拆分技能包](https://github.com/Miint-Sunny/nai5-prompting/releases/download/v1.2b/nai5-split-v1.2b.zip) | 十个平级的小技能 | 想按当前任务启用相应内容；需要支持多技能导入的客户端 |

直接在客户端选择对应 ZIP 导入；不要导入整个仓库的源码 ZIP。单文件与两卷都安装为 `nai5-prompting`，导入另一种时选择替换同名技能。从完整包切换到拆分包时，停用旧的完整包，避免同一套方法叠加；反向切换时也停用原拆分技能。旧发布记录保留，当前下载入口使用上面三个 v1.2b 包。

只支持单技能导入的客户端，从下表分别下载所需小包。漫画／服装写法补充需同时启用本版 **通用 NAI5 写法**；安装先后不决定任务执行顺序。

## 先看看 split 有什么

**通用构思找想法 → 专项构思深入题材 → 通用写法表达定稿 → 按需要加专项写法补充。**

只要想法、角色、衣服或分镜，交到该阶段即可；已有定稿要词句则直接进入写法。下表名称可打开完整入口，方法链接可直接阅读正文。

| 技能与用途 | 方法全文 | 单独下载 |
|---|---|---|
| [整体想法](skills/nai5-ideas/SKILL.md)：主题、关系与故事种子 | [想法](skills/nai5-ideas/references/ideas.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-ideas-v1.2b.zip) |
| [场景与情境](skills/nai5-scene-design/SKILL.md)：环境、空间与气氛 | [场景](skills/nai5-scene-design/references/scene.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-scene-design-v1.2b.zip) |
| [艺术表达](skills/nai5-art-direction/SKILL.md)：情绪、光色、媒介与风格，含具象和写实 | [艺术](skills/nai5-art-direction/references/art.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-art-direction-v1.2b.zip) |
| [OC 整体设计](skills/oc-character-design/SKILL.md)：角色核心、行为与外形辨识 | [角色](skills/oc-character-design/references/character.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/oc-character-design-v1.2b.zip) |
| [插画构图](skills/nai5-illustration-composition/SKILL.md)：已有想法变成具体画面 | [构图](skills/nai5-illustration-composition/references/composition.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-illustration-composition-v1.2b.zip) |
| [漫画架构与分镜](skills/nai5-comic-storyboard/SKILL.md)：故事、页格与连续性 | [架构](skills/nai5-comic-storyboard/references/comic-story.md) · [布局](skills/nai5-comic-storyboard/references/comic-layout.md) · [连续性](skills/nai5-comic-storyboard/references/comic-continuity.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-comic-storyboard-v1.2b.zip) |
| [服装设计](skills/oc-costume-design/SKILL.md)：轮廓、部件、配色与材质 | [服装设计](skills/oc-costume-design/references/costume.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/oc-costume-design-v1.2b.zip) |
| [通用 NAI5 写法](skills/nai5-writing/SKILL.md)：共同语法、字段、普通画面与精确改词 | [共同规范](skills/nai5-writing/references/conventions.md) · [普通画面](skills/nai5-writing/references/illustration.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-writing-v1.2b.zip) |
| [漫画写法补充](skills/nai5-comic-writing/SKILL.md)：已定分镜转主串、角色串与 UC | [漫画编译](skills/nai5-comic-writing/references/comics.md) · [示例](skills/nai5-comic-writing/references/comic-examples.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-comic-writing-v1.2b.zip) |
| [服装写法补充](skills/nai5-costume-writing/SKILL.md)：已定衣物的片段或完整画面表达 | [服装表达](skills/nai5-costume-writing/references/costume.md) | [ZIP](https://raw.githubusercontent.com/Miint-Sunny/nai5-prompting/v1.2b/skills/nai5-costume-writing-v1.2b.zip) |

也可直接读 [完整合订稿](references/NAI5_All_Prompting.md)，或 [构思卷](paired/references/通用构思.md)＋[写法卷](paired/references/通用写法.md)。这三种包装共同使用同一批方法，资源按任务选读；无需重复挂载。

## 导入与读取说明

ZIP 中保留合法技能目录，只写文件条目，各技能的 `SKILL.md` 在其资源前面。单文件／两卷包各有一个技能；拆分包包含十个平级技能目录，ZIP 根层不混入说明文件或其他 ZIP。

使用技能资源工具时，路径相对当前技能目录，不再加技能名前缀或 Markdown 章节锚点。若使用通用文件读取工具，应从宿主提供的技能位置解析路径，不能用图片输出目录猜测。文件列表或 ZIP 的排列顺序不等于模型应逐个读取所有文件。

这些包提供内容方法与可填写的词句，适合能读取相应文件的 LLM 客户端。Harness 可复用内容方法，但本发布不包含工作台操作包；实际写入仍依赖相应适配工具，不因导入成功就具备工具能力或自动生图能力。

已知验证范围见 [发布说明](RELEASE_NOTES.md)。不承诺所有 agent、全部 Windows 界面或生图效果均已验证。来源与同源文件对应见 [SOURCE.json](SOURCE.json)，下载后可用 [SHA256SUMS.txt](SHA256SUMS.txt) 核对文件。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。所有包装保留完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE)，项目贡献按 GNU GPL version 3（GPL-3.0-only）提供。项目公开来源：[nai5-prompting](https://github.com/Miint-Sunny/nai5-prompting)。
