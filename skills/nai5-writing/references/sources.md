<a id="writing-sources"></a>

# 写法来源与适用范围

本文件记录方法出处与适用边界。技术语法、术语或当前能力需要核实时，读取对应技术节；用户明确要求核对历史依据时，再读相应归档说明。普通写词不沿历史来源自主检索旧图、完整原串或反推来补画面内容。

> Copyright (C) 2026 Miint-Sunny
> SPDX-License-Identifier: GPL-3.0-only
> 项目与公开来源：[Miint-Sunny/nai5-prompting](https://github.com/Miint-Sunny/nai5-prompting)。
> 许可全文：[GNU GPL version 3](https://www.gnu.org/licenses/gpl-3.0.html)；贡献范围与第三方材料说明见 [NOTICE](https://github.com/Miint-Sunny/nai5-prompting/blob/main/NOTICE)。

<a id="general-writing.s12"></a>

### 写法判据来源

词组与句子的分工来自本项目早期的出图对照。操作方法见 [词组与句子](illustration.md#general-writing.s04)：词组列对象、属性、姿势与机位，句子说明状态、接触、方向与空间关系。

使用标签或提示词材料时，频次只供参考，不据此推断作者动机；收藏批次不等于生成时间。`res_mult:Nx` 的效果与 `face focus` 的词义仍需单独核对，不能因见过用例就当作已确认。

方法可独立使用；用户补充资料按本次指定范围生效。语法与能力以运行环境为准，不推定还有其他挂载文件或题材池。

<a id="comic-sources.s03"></a>

### NovelAI：只把官方描述当作能力依据

| 来源 | 能力与使用条件 |
|---|---|
| N1 [NovelAI Diffusion V5](https://novelai.net/v5) | 支持自然语言描述整页分格；支持多角色；前端可根据引号自动建立文字块。图像参考与重绘须按选定模型的当前界面确认，不沿用旧发布页的“后续上线”承诺。 |
| N2 [Text Rendering](https://docs.novelai.net/en/image/textrendering/) | V5支持中文等文字及位置/载体描述；Full上限写750字符，Curated写374字符，包含空格和换行。文字未出现时可检查质量词中的文字排除。 |
| N3 [Image Generation Models](https://docs.novelai.net/en/image/models/) | 概览对相同渲染文字容量使用 tokens，与文字专页单位不一致；提示词本身的 token 容量又是另一项。本项目按文字专页字符口径引用，保留差异。 |
| N4 [Quality Tags](https://docs.novelai.net/en/image/qualitytags/) | V5 Standard 与 Light 附加内容不同，均须按实际生效词去重和处理文字冲突，不能假定预设恒开。 |
| N5 [Precise Reference](https://docs.novelai.net/en/image/precisereference/)、[Vibe Transfer](https://docs.novelai.net/en/image/vibetransfer/)、[Inpaint](https://docs.novelai.net/en/image/inpaint/) | Precise、Vibe 与 Inpaint 各自的模型支持范围分别确认；以所选模型的当前界面及对应文档为准，不由其他模型或另一工具的支持情况类推。 |
| N6 [Multiple Characters](https://docs.novelai.net/en/image/multiplecharacters/) | 角色位置在角色提示词区从 AI's Choice 改成 Custom，点 Character Positions 按钮在画布上摆放，模型会贴着摆放的位置画；V4 与 V4.5 限 5×5 网格，V5 没有这项限制，是自由画布。本页写 V5 最多 22 个角色、V4 最多 6 个；N1 的 V5 页同样写最多 22 个、可把角色放在画布任意位置。每个角色另有自己的 Undesired Content 栏。 |
| N7 [Tags](https://docs.novelai.net/en/image/tags/) 的 Alpha Transparency 一节 | `transparent background` 让背景透明；`has alpha` 较抽象，表示要以某种方式用到 alpha 通道；`alpha transparency` 让画面里的物体以 alpha 通道方式透空（例子是魔法特效、火焰、伞），只在 V5 可用。 |

基础语法、字段与原串依本包共同规范，OC 库仅在用户需要且实际启用时读取；方法导航见 [写法入口](conventions.md#writing-conventions)。本包漫画采用“主 Prompt 写本页去重人数标签与简短版式、Character 框承载各格内容”，详见 “漫画提示词编译”（`nai5-comic-writing`：`references/comics.md#comic-adapter.preamble`）。这是本包的字段约定，故事身份、画格与提示框数量分别计算。

<a id="comic-sources.s05"></a>

### 用户分镜参考与实图反馈

归档材料中的《分镜脚本提示词（例）》用于支持“剧情节点→页级节奏→逐格镜头/文字/衔接”的制作顺序，以及精简对白、避免连续大头、无台词格有作用、重要节点考虑页尾等建议。该文档原本服务于已有剧本改编，右→左阅读、不新增剧情、从已有页面续写等条件，不自动成为用户原创任务的要求；格数参考的适用范围见页级规划，不当作硬配额。

本包默认从左往右、上→下阅读，四格默认 2×2；人物去重计数，保持版式简明与可见状态连续。用户另有指定时按本次要求处理。

| 归档材料记录的反馈 | 保留的写法 |
|---|---|
| 角色提示框分别写分镜可行，但每格双人、同机位导致平淡且冗长 | 采用角色框承载分镜；先改变出场与镜头调度，主串内容部分只放人数标签与简短版式，质量尾另按实际预设处理 |
| 两只手的互动被分别画成两个窄格 | 无可识别主体的局部互动合为一个框；可识别多人同格仍每人一个框 |
| 大幅场景中的“只入画一只手”难以成立 | 镜头尺寸、机位、画外身体与动作可达性先校验，必要时改景别/站位 |
| 毯子前格到颈部，后格降到腹部 | 覆盖边沿用身体锚点保持一致，变化安排可理解的动作 |
| 分页独立生成的布景与衣服变化明显 | 简化小格背景、减少跨页同角度复杂全景对照；服装结构保持一致 |
| 删去彩色词后，同一人的头发由深变浅 | 黑白保留并重复明暗锚点，去色相不等于去掉深浅 |
| 包的样式、开口机构与附件容易改变 | 固定结构与当前状态分开；后续要操作的结构先建立；实际归因须核对原提示词 |
| 不需要逐格写“无文字”；旁白与对白需明确载体 | 静默格省略文字指令，旁白用 Narrator box，对白用 speech bubble |

契诃夫之枪在此作为创作取舍原则：先建立会使用的功能，删掉没有作用的强调细节；身份、空间、气氛与停顿本身也可以构成作用，不要求故事开头立即兑现全部伏笔。

<a id="costume-writing.s10"></a>

### 查询依据

服装术语、标签含义及查询方式参考以下来源：

- [FASHIONPEDIA 官方介绍](https://fashionary.org/products/fashionpedia)
- [Danbooru API：Tags（Safebooru 镜像）](https://safebooru.donmai.us/wiki_pages/api%3Atags)
- [Danbooru API Help（Safebooru 镜像）](https://safebooru.donmai.us/wiki_pages/help%3Aapi)
- [Danbooru Tag 模型源码](https://github.com/danbooru/danbooru/blob/master/app/models/tag.rb)
