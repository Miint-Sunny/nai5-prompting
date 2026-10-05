# NovelAI V5 构思与写法 · 通用／候选版

这是基于 `v1.2-next-preview.7-20261005` 的「通用」候选版，接在 v1.2c-nightly 之后，通过仓库提供。v1.1 仍是稳定 Latest。10-05 收紧旧材料读取与示例使用，承接 10-03 构思与写法修订：补足画面安排和词句分工，修正含混措辞与超出原有证据的断言。漫画阶段、UC 条件与「随便／你来定」的已定规则继续沿用。群与个人偏好另行启用，不在这三个 ZIP 里。详见 [发布说明](RELEASE_NOTES.md)。

**同一套方法，三种包装，选择一种即可。** 内容覆盖整体想法、场景、艺术表达、OC、插画构图、漫画与服装设计、照图反推，以及把已定方案写成 NovelAI Diffusion V5 提示词。已有想法或定稿就从当前阶段继续，不必从头走一遍。v1.1 的历史稳定发布与标签保留。

| 下载 | 包里是什么 | 适合怎样用 |
|---|---|---|
| [单文件完整包](downloads/nai5-single-通用.zip) | 一个薄入口＋完整合订稿 | 想保留一份完整方法，按章节阅读 |
| [两卷完整包](downloads/nai5-paired-通用.zip) | 一个薄入口＋构思卷、写法卷 | 想分开阅读构思与写法；写法卷已含专项补充 |
| [拆分技能包](downloads/nai5-split-通用.zip) | 十一个平级的小技能 | 想按当前任务启用相应内容；需要支持多技能导入的客户端 |

上表指向仓库内的候选 ZIP；在 GitHub 文件页点击下载即可。Release 页面仍保留历史版本，本次候选未晋升稳定 Latest。Aaalice v4.2.1 官方包内置 Pi 的真实导入与读资源仍待验证。

直接在客户端选择对应 ZIP 导入；不要导入整个仓库的源码 ZIP。单文件与两卷都安装为 `nai5-prompting`，导入另一种时选择替换同名技能。从完整包切换到拆分包时，停用旧的完整包，避免同一套方法叠加；反向切换时也停用原拆分技能。

只支持单技能导入的客户端，从下表分别下载所需小包。漫画、服装写法补充和照图反推需同时启用本版 **通用 NAI5 写法**；安装先后不决定任务执行顺序。

## 怎样使用这些技能

**按当前任务选包，不必全装。** 只要想法装整体想法；场景、艺术表达、OC、构图、漫画分镜、服装设计各装对应的构思包；手里已有定稿要词句装通用写法，漫画、服装、照图再各加一个补充包。

**已有内容直达。** 有想法就从专项构思进，有定稿就从写法进；模型沿用你已经给定的内容、细节、确认和修改范围，不重走前面的阶段，也不要求填交接表。只装了写法包时，说「想画……」模型会直接给完整提示词；想先聊想法，就装构思包，或者明说「先构思」。分镜阶段没说要词，模型会停在分镜，说「转成提示词」再转。

**补充包怎么取通用规则。** 漫画、服装写法补充和照图反推都依赖同版本的通用写法，要一起启用。没装到所需的包时，模型用现有规则完成能做的部分，说明哪些规则尚未载入，不编造规范。

**偏好是另一层。** 这三个包只讲通用方法，不带任何人的审美。想让结果更像自己或自己所在的群，可以在它之上叠一层偏好：把常画的题材、光色、机位和写词习惯写成一份补充，说「按……的路子」时启用，说「关掉偏好」就回到通用方法。偏好在维护阶段结合真实提示词、角色栏、UC、参数与画面证据整理，再由用户或本人审定。普通生成只读整理后正文，不自行回查这些原始材料来补题；只有用户明确要求整理、核对或指定作品分析时才读相应材料。这三个 ZIP 不含任何人的偏好。

## 先看看 split 有什么

**通用构思找想法 → 专项构思深入题材 → 通用写法表达定稿 → 按需要加专项写法补充。**

只要想法、角色、衣服或分镜，交到该阶段即可；已有定稿要词句则直接进入写法。下表名称可打开完整入口，方法链接可直接阅读正文。

| 技能与用途 | 方法全文 | 单独下载 |
|---|---|---|
| [整体想法](skills/nai5-ideas/SKILL.md)：主题、关系与故事种子 | [想法](skills/nai5-ideas/references/ideas.md) | [ZIP](skills/nai5-ideas-通用.zip) |
| [场景与情境](skills/nai5-scene-design/SKILL.md)：环境、空间与气氛 | [场景](skills/nai5-scene-design/references/scene.md) | [ZIP](skills/nai5-scene-design-通用.zip) |
| [艺术表达](skills/nai5-art-direction/SKILL.md)：情绪、光色、媒介与风格，含具象和写实 | [艺术](skills/nai5-art-direction/references/art.md) | [ZIP](skills/nai5-art-direction-通用.zip) |
| [OC 整体设计](skills/oc-character-design/SKILL.md)：角色核心、行为与外形辨识 | [角色](skills/oc-character-design/references/character.md) | [ZIP](skills/oc-character-design-通用.zip) |
| [插画构图](skills/nai5-illustration-composition/SKILL.md)：已有想法变成具体画面 | [构图](skills/nai5-illustration-composition/references/composition.md) | [ZIP](skills/nai5-illustration-composition-通用.zip) |
| [漫画架构与分镜](skills/nai5-comic-storyboard/SKILL.md)：故事、页格与连续性 | [架构](skills/nai5-comic-storyboard/references/comic-story.md) · [布局](skills/nai5-comic-storyboard/references/comic-layout.md) · [连续性](skills/nai5-comic-storyboard/references/comic-continuity.md) | [ZIP](skills/nai5-comic-storyboard-通用.zip) |
| [服装设计](skills/oc-costume-design/SKILL.md)：轮廓、部件、配色与材质 | [服装设计](skills/oc-costume-design/references/costume.md) | [ZIP](skills/oc-costume-design-通用.zip) |
| [通用 NAI5 写法](skills/nai5-writing/SKILL.md)：共同语法、字段、普通画面与精确改词 | [共同规范](skills/nai5-writing/references/conventions.md) · [普通画面](skills/nai5-writing/references/illustration.md) | [ZIP](skills/nai5-writing-通用.zip) |
| [漫画写法补充](skills/nai5-comic-writing/SKILL.md)：已定分镜转主串、角色串与 UC | [漫画编译](skills/nai5-comic-writing/references/comics.md) · [示例](skills/nai5-comic-writing/references/comic-examples.md) | [ZIP](skills/nai5-comic-writing-通用.zip) |
| [服装写法补充](skills/nai5-costume-writing/SKILL.md)：已定衣物的片段或完整画面表达 | [服装表达](skills/nai5-costume-writing/references/costume.md) | [ZIP](skills/nai5-costume-writing-通用.zip) |
| [照图反推](skills/nai5-reverse-prompt/SKILL.md)：照图写提示词，或只推其中一部分 | [照图反推](skills/nai5-reverse-prompt/references/reverse.md) | [ZIP](skills/nai5-reverse-prompt-通用.zip) |

也可直接读 [完整合订稿](references/NAI5_All_Prompting.md)，或 [构思卷](paired/references/通用构思.md)＋[写法卷](paired/references/通用写法.md)。这三种包装共同使用同一批方法，资源按任务选读；无需重复挂载。

## 导入与读取说明

ZIP 中保留合法技能目录，只写文件条目，各技能的 `SKILL.md` 在其资源前面。单文件／两卷包各有一个技能；拆分包包含十一个平级技能目录，ZIP 根层不混入说明文件或其他 ZIP。

使用技能资源工具时，路径相对当前技能目录，不再加技能名前缀或 Markdown 章节锚点。若使用通用文件读取工具，应从宿主提供的技能位置解析路径，不能用图片输出目录猜测。文件列表或 ZIP 的排列顺序不等于模型应逐个读取所有文件。

这些包提供内容方法与可填写的词句，适合能读取相应文件的 LLM 客户端。Harness 可复用内容方法，但本发布不包含工作台操作包；实际写入仍依赖相应适配工具，不因导入成功就具备工具能力或自动生图能力。

已知验证范围见 [发布说明](RELEASE_NOTES.md)。不承诺所有 agent、全部 Windows 界面或生图效果均已验证。来源与同源文件对应见 [SOURCE.json](SOURCE.json)，下载后可用 [SHA256SUMS.txt](SHA256SUMS.txt) 核对文件。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。所有包装保留完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE)，项目贡献按 GNU GPL version 3（GPL-3.0-only）提供。项目公开来源：[nai5-prompting](https://github.com/Miint-Sunny/nai5-prompting)。
