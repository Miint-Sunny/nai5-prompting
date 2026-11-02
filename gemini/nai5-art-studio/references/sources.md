<a id="sources"></a>

# 方法依据与官方参考索引

本文件汇总本技能所依据的 NovelAI 官方技术文档、服装与标签核查渠道、漫画分镜参考材料以及第三方开源致谢，供用户明确要求核查出处或能力边界时查阅。

> Copyright (C) 2026 Miint-Sunny
> SPDX-License-Identifier: GPL-3.0-only
> 项目与公开来源：[Miint-Sunny/nai5-prompting](https://github.com/Miint-Sunny/nai5-prompting)
> 许可全文见随附 `LICENSE`（[GNU GPL version 3](https://www.gnu.org/licenses/gpl-3.0.html)），第三方材料归属说明见随附 `NOTICE`。

---

<a id="comic-sources.s03"></a>

## 1. NovelAI 官方技术文档依据

| 编号 | 官方文档来源 | 核心能力与本技能采用口径 |
| --- | --- | --- |
| **N1** | [NovelAI Diffusion V5](https://novelai.net/v5) | 支持自然语言描述整页分格与复杂构图；支持最多 22 个角色及自由画布位置摆放；前端可根据双引号自动建立文字渲染块。 |
| **N2** | [Text Rendering](https://docs.novelai.net/en/image/textrendering/) | V5 支持中文、英文、日文等文字及载体/位置描述；文字专页标注上限为 Full 750 字符、Curated 374 字符（含空格与换行）。 |
| **N3** | [Image Generation Models](https://docs.novelai.net/en/image/models/) | 模型概览页与文字专页对文字容量的单位表述存在差异（tokens vs. 字符），本技能引用文字专页字符口径并区分提示词总 token 容量。 |
| **N4** | [Quality Tags](https://docs.novelai.net/en/image/qualitytags/) | 官网质量词开关默认开启：V5 标准档在主串末尾自动附加 `very aesthetic, masterpiece, no text`，轻量档附加 `very aesthetic, amazing quality, no text`。因此本技能默认不手写质量词；画面含任何可见文字时提醒用户关闭该开关。 |
| **N5** | [Precise Reference](https://docs.novelai.net/en/image/precisereference/) · [Vibe Transfer](https://docs.novelai.net/en/image/vibetransfer/) · [Inpaint](https://docs.novelai.net/en/image/inpaint/) | 各参考与局部重绘工具的模型支持范围以当前选定模型的实际界面为准。 |
| **N6** | [Multiple Characters](https://docs.novelai.net/en/image/multiplecharacters/) | 角色位置可在角色提示词区从 `AI's Choice` 改为 `Custom`，点击 `Character Positions` 在画布上自由摆放（V5 无 5×5 网格限制，支持最多 22 个角色）；不手动设位置时模型通常按角色栏顺序从上到下、从左到右排布。`source#` / `target#` / `mutual#` 前缀接在互动动作 tag 前（如 `source#hug` / `target#hug`）。 |
| **N7** | [Tags — Alpha Transparency](https://docs.novelai.net/en/image/tags/) | `transparent background` 使背景透明；`has alpha` 表示使用 alpha 通道；`alpha transparency`（仅 V5 可用）使画面内的火焰、魔法特效、伞面等物体呈现半透明 alpha 效果。 |
| **N8** | [Undesired Content](https://docs.novelai.net/en/image/undesiredcontent/) | V5 的 UC 预设共有 `Heavy`、`Light`、`Furry Focus`、`Human Focus` 四档：`Heavy` 与 `Human Focus` 含 `multiple views, halftone, screentone, logo, negative space, blank page`；`Furry Focus` 含 `comic, multiple scenes, sequence`；`Light` 均不含。漫画、网点、多视图、留白与印字任务需避开冲突预设并删除对应手写 UC 词。 |

---

<a id="costume-writing.s10"></a>

## 2. 服装术语与 Danbooru 标签核查依据

- **现实服装结构与分类**：
  - [FASHIONPEDIA 官方介绍](https://fashionary.org/products/fashionpedia)
  - [京都服饰文化研究财团数字档案 (KCI)](https://www.kci.or.jp/en/archives/digital_archives/)
  - [V&A Fashion Collection](https://www.vam.ac.uk/collections/fashion)
  - [The Met Costume Institute](https://www.metmuseum.org/about-the-met/collection-areas/the-costume-institute)
  - [POSEMANIACS：オリジナルキャラに合う衣装の決め方](https://www.posemaniacs.com/courses/4884b467-45c2-4db0-b995-2fa9e3a14b25)
  - [CLIP STUDIO TIPS：Drawing Clothing for Manga and Anime](https://tips.clip-studio.com/en-us/articles/4496) · [Character Design—Costume](https://tips.clip-studio.com/en-us/articles/1957)
  - [Proko：Drapery Fundamentals](https://www.proko.com/course/drapery-fundamentals/comments)
- **Danbooru 标签接口与规范**：
  - [Danbooru API：Tags（Safebooru 镜像）](https://safebooru.donmai.us/wiki_pages/api%3Atags)
  - [Danbooru API Help（Safebooru 镜像）](https://safebooru.donmai.us/wiki_pages/help%3Aapi)
  - [Danbooru Tag 模型源码](https://github.com/danbooru/danbooru/blob/master/app/models/tag.rb)

---

<a id="comic-sources.s01"></a>

## 3. 漫画分镜与版式创作方法来源

### 3.1 视频与专栏经验转化
- [Parion圆周率：《漫画家不会告诉你的20大技巧·分镜篇》](https://www.bilibili.com/video/BV1VT411K7RS/)：格面积与景别分离、环境建立、动作前后（预示/关键/反应）、正反打与轴线、连续蒙太奇删格、重复构图与跨时空连接。
- [Parion圆周率：《漫画家不会告诉你的20大技巧·平面篇》](https://www.bilibili.com/video/BV19G411b7tB/)：格间距分组、字距与气泡声效、破格/插格/互动格、留白/无框/背景格与前景叠像。
- **W1** [Steve Ellis：Pro Artist’s Guide to Comic & Manga Layouts, Paneling, Flow](https://www.clipstudio.net/how-to-draw/archives/160963)
- **W2–W6** MediBang Manga Tutorials ([02](https://medibangpaint.com/en/use/2021/06/mangatutorialforbeginners02/) · [03](https://medibangpaint.com/en/use/2021/07/mangatutorialforbeginners03/) · [05 Name阶段](https://medibangpaint.com/en/use/2021/08/mangatutorialforbeginners05/) · [06 Frame Layout](https://medibangpaint.com/en/use/2021/09/mangatutorialforbeginners06/) · [08 Frames & Bubbles](https://medibangpaint.com/en/use/2021/11/mangatutorialforbeginners08/))
- **W7** [Taiyo Nakashima / SMA：Japanese Manga 101 #003 — Art of Paneling](https://www.manga-audition.com/japanesemanga101_003/)
- **W8–W9** CLIP STUDIO TIPS Webtoon & Print Paneling ([69Michi: Webtoon 101](https://tips.clip-studio.com/en-us/articles/4143) · [Manny Guevarra: How to Panel Comics for WEBTOON and Print](https://tips.clip-studio.com/en-us/articles/9420))
- **W10** [Nate Piekos / Blambot：Comic Book Grammar & Tradition](https://blambot.com/pages/comic-book-grammar-tradition)
- **G1** [SILENT MANGA AUDITION：Rules & Guidelines（创作指南部分）](https://www.manga-audition.com/rules-guidelines/)

### 3.2 实图反馈沉淀的漫画写法规则

| 实图反馈问题 | 转化为本技能的具体写法规则 |
| --- | --- |
| 角色框分别写分镜可行，但每格双人同机位显得平淡冗长 | 采用 `Character` 框承载各格内容，主串只放去重人数标签与简短版式；先调度出场与景别变化 |
| 两只手的互动被分别画成两个窄格 | 无可识别主体的匿名局部互动合并为一个 `Character` 框；同格有多名可识别人物时仍每人一框 |
| 毯子前格盖到颈部，后格突然掉到腹部 | 覆盖边沿绑定具体身体锚点保持跨格一致，高度变化需有可见动作过渡 |
| 删掉彩色词转黑白后，同一人的头发由深变浅 | 黑白模式去掉色相词时，必须保留并跨格复用 `pale` / `dark` 等明暗对比锚点 |
| 包的样式、开口机构与附件跨格变形 | 固定结构短语跨格复用，逐格只改写开合或持握状态 |
| 不需要逐格写“无文字”；旁白与对白需明确载体 | 静默格直接省略文字指令（不写 `no text`），旁白统一用 `Narrator box`，对白用 `speech bubble` |

---

<a id="ideation-sources.background"></a>

## 4. 开源与创作方法致谢

- **真实世界场景、角色与服装背景核对**：
  改编自 [Elowwwen / Fanfic-background-assistant](https://github.com/Elowwwen/Fanfic-background-assistant)（提交 `0b5da382b5f5d0150b406bc66bfbc0c4aaa11e3f`，MIT License，Copyright (c) 2026 Elowwwen）。许可全文见随附 `NOTICE`。
- **动作阶段、支撑重心与可见后果设计**：
  参考署名 antimomi 的《动作扩写》所提示的动作阶段选择、身体支撑配合与可见后果判断，按本项目构图与写词分工重新表述。
