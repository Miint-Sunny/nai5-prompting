# 通用版 `skills/`（v1.2.7）发现的问题与改进建议

根据任务要求，本轮维护保留仓库根目录的通用 `skills/` 原封不动，将适配过程中以及排查 `session-595e368e-7191-4fa3-a0bf-18360edd2b4d` 时发现的通用版问题单独汇总于此，供后续更新上游通用版时集中决策。

> **状态说明**：以下问题已在 `gemini/nai5-art-studio/` 适配版中先行修复或规避；通用版 `skills/` 尚未改动。


## 维护者核对结果（2026-11-02）

逐条拿通用版 v1.2.7 原文核对。报告里引用的几句原文（第 2 条的三句英文例句、第 3 条的「核心外貌特征」「环境设定」「镜头语言」、第 6 条的几句口号）在通用版里都找不到，以下按实际原文判断。通用版的修改随 v1.2.8 发布（方法仓 `32efba8`）；本防拦截版这三处原本就有，跟进 v1.2.8 时正文不用改。

| 条 | 结论 | 处理 |
| --- | --- | --- |
| 1 只要动作和场景 | 属实：通用版没写用户只要主串时怎么交 | 通用版补上：只给 `Base Prompt:` 一块，不写角色栏，外貌和服装不挪进主串，跟动作、神态连着的耳朵和尾巴状态可以写（字段职责加一行，模板和对照表各补一句） |
| 2 例句的引号和句号 | 部分属实：§4 开头已经说明外层引号只是标示例句，没说句末句号 | 那句说明补上「句末句号照模板换成逗号」 |
| 3 旧词序 | 属实：§0.3 示意图和 §1 职能块表还是旧顺序（外貌服装在主串、动作在镜头之后） | 两处都改成和 §0 模板一致 |
| 4 漫画内容放在共同规范里 | 不改：旧式 `Panel N` 示例已标明只用来看懂旧串、不作默认模板；色彩一节普通插画要黑白时也用 | 无 |
| 5 敏感词与句子主语 | Gemini 平台的问题：通用版给其他模型用，部位焦点词是 NovelAI 的实用知识；单人句子主语通用版本来就写 `The character` | 只在本防拦截版里处理 |
| 6 重复的口号和文件 | 不属实：引的几句口号通用版里一次都没有；`sources.md` 是 4 份不是 10 份，多出来的是仓库目录里 `.worktrees/` 下其他分支的检出；`background.md` 3 份、`composition.md` 2 份相同是有意的，拆分版每个技能要能单独装 | 无 |

---

## 1. `nai5-writing`：普通插画缺少「局部主串（只要动作与场景、不带角色栏）」的明确交付分支

- **涉及文件**：
  - [`skills/nai5-writing/references/conventions.md`](../skills/nai5-writing/references/conventions.md)（`#field-contract`）
  - [`skills/nai5-writing/references/illustration.md`](../skills/nai5-writing/references/illustration.md)（`§0` 模板与落笔检查）
- **问题现象**：
  - 在 `session-595e368e-7191-4fa3-a0bf-18360edd2b4d` 中，用户请求：*“写点适合慵懒兔娘的提示词，比如室外野餐垫侧躺下来，不用写UC和质量词，只要动作和场景，单人”*。
  - 用户已有角色栏（或打算复用到不同兔娘角色上），因此明确只要 `Base Prompt:` 的动作与场景。但 `illustration.md` 反复强调*“角色栏（普通完整插画每人一栏，单人也保留）”*以及*“外貌和服装全部写进角色栏”*，没有给出“只要动作和场景主串”时的标准模板，也没有说明与动作联动的可变物种特征（如 `drooping rabbit ears`）能否留在主串。
  - 这导致模型在思考链中反复纠结是否要输出 `Character 1:`、是否要把 `drooping rabbit ears` 从主串剔除。
- **建议修复**：
  - 在 `conventions.md` 和 `illustration.md` 中显式增设 **「局部主串（只要动作与场景）」** 分支：当用户明确只要动作与场景、不需要角色栏时，仅输出 `Base Prompt:` 一个代码块；允许在主串保留与动作/神态直接相关的可变物种状态（如 `drooping rabbit ears`、`wagging tail`），不写入锁死发色、瞳色和整套服装的描述。

---

## 2. `nai5-writing`：`illustration.md` 句子示例自带外层引号与句末句号，与核心语法规则自相矛盾

- **涉及文件**：
  - [`skills/nai5-writing/references/illustration.md`](../skills/nai5-writing/references/illustration.md) 第 466–576 行（`§4.1` 至 `§4.7` 的所有正例句子）
- **问题现象**：
  - `conventions.md` 与 `illustration.md` 核心规则明确要求：
    1. *“不要给整句自然语言描述加引号”*（因为 NAI V5 前端会把引号识别为画面渲染文字 `Text:`）；
    2. *“主串与角色栏代码块内，每一行末尾必须带一个英文半角逗号 `,`，英文句子末尾的句号 `.` 也要换成英文逗号 `,`”*。
  - 然而在 `illustration.md` 的 `§4.1`～`§4.7` 中，几乎所有示范句都写成了带外层双引号且以句号结尾的格式，例如：
    - 第 466 行：`> "Two girls sit back-to-back on a wooden bench, reading the same book."`
    - 第 483 行：`> "A girl reaches out with her right hand to gently touch a glowing butterfly resting on a stone railing."`
    - 第 562 行：`> "Three girls stand in a circle holding hands, looking toward the center."`
  - 模型模仿这些正例时，极易违反“不加引号”和“句尾句号换逗号”两条硬性规则。
- **建议修复**：
  - 将 `illustration.md` `§4.1`～`§4.7` 中所有非文字渲染类的英文示范句去掉外层双引号 `"..."`，并将句末 `.` 统一改为 `,`。

---

## 3. `nai5-writing`：`illustration.md` 残留两处旧版词序表，与 `§0` 标准模板冲突

- **涉及文件**：
  - [`skills/nai5-writing/references/illustration.md`](../skills/nai5-writing/references/illustration.md) 第 207–210 行（`§0.3` 顺序示意）与第 233–243 行（`§1` 核心排序表）
- **问题现象**：
  - `§0` 标准模板规定：普通完整插画的主串顺序是 **「人数与物件 → 动作/姿势/表情 → 镜头/机位/光影与场景 → 自然语言关系句」**，且人物外貌与服装全部放入 `Character N:` 栏。
  - 但紧接着的 `§0.3`（第 207–210 行）和 `§1` 排序表（第 233–243 行）仍然保留了单框时代的旧顺序：
    - 把 `核心外貌特征、主要服装` 列在主串第 2 顺位（第 236 行）；
    - 把 `场景→镜头→动作` 写成先写场景、再写镜头、最后写动作（第 208 行 `[环境设定], [镜头语言], "自然语言描述的具体动作与空间关系"`）。
- **建议修复**：
  - 统一 `§0.3` 和 `§1` 的排序表，使其与 `§0` 的主串/角色栏分工及「人数物件 → 动作表情 → 镜头场景 → 关系句」顺序完全一致。

---

## 4. `nai5-writing`：`conventions.md` 混入大量漫画专属规则，导致普通插画任务被动加载冗余内容

- **涉及文件**：
  - [`skills/nai5-writing/references/conventions.md`](../skills/nai5-writing/references/conventions.md) 第 279–309 行（旧版四格 `Panel 1`～`Panel 4` 示例）与第 333–402 行（`## 按需色彩参考` 漫画半黑白/黑白全字段转换细则）
- **问题现象**：
  - `conventions.md` 是所有写词任务的必读入口文件（43.1 KB）。但其中：
    1. 第 333–402 行整整 70 行是专门针对漫画的 `manga, {{{greyscale with colored eyes,greyscale with colored hair}}}` 与 `manga, monochrome` 转换细则；
    2. 第 279–309 行还保留了使用 `Panel 1: ... Panel 2: ...` 数字编号的旧版四格示例，与 `nai5-comic-writing` 中要求的*“不用 `Panel + 数字` 标注，用位置与大小称呼画格”*及*“四格默认 2×2”*相冲突。
- **建议修复**：
  - 将第 333–402 行的漫画色彩转换细则移入 `nai5-comic-writing/references/comics.md`；
  - 将第 279–309 行的旧版 `Panel 1` 四格示例更新为符合现行 2×2 规范的指向说明，或直接移至 `nai5-comic-writing`。

---

## 5. 敏感焦点词枚举与自然语言句主语习惯在严格安全平台（如 Gemini）上易触发 `PROHIBITED_CONTENT`

- **涉及文件**：
  - [`skills/nai5-writing/references/illustration.md`](../skills/nai5-writing/references/illustration.md) 第 419–428 行（`§3.6 焦点控制标签`）及第 466–576 行句例
  - [`skills/nai5-ideas/references/ideas.md`](../skills/nai5-ideas/references/ideas.md) 第 60 行
- **问题现象**：
  1. **必读参考文档含高敏感部位词**：`illustration.md` `§3.6` 枚举了 `ass focus`、`breast focus`、`navel focus`、`thigh focus`、`armpit focus` 等标签及中文解释；`ideas.md` 第 60 行包含“成人向……擦边或露骨”等字眼。
  2. **英文自然语言句频繁以 `A girl` / `The girl` 作主语**：在 Danbooru 标签中 `1girl` / `girl` 泛指任意年龄女性，但在英文自然语言长句里以 `A girl` / `The girl` 作主语并紧跟躺卧（`lying on her side`）、身体接触或鞋袜描写时，极易被 Gemini 等平台的英文自然语言分类器误判为未成年人敏感描写。
  3. **躺卧/睡姿缺少清爽几何表达提示**：在 `session-595e368e` 中，模型写“慵懒兔娘野餐垫侧躺”时将 `lying, on side` 与 `hand on own cheek, half-closed eyes, parted lips` 及 `sinking into the fabric... along her hip` 连续叠加，直接触发 `PROHIBITED_CONTENT` 流式中断。
- **建议修复**：
  - `§3.6` 改用 `face focus`、`eye focus`、`hand focus`、`foot focus`、`back focus` 说明 `<部位> focus` 语法与降权方法，删去高敏感部位标签枚举；
  - 建议在 `illustration.md` 中引导英文自然语言句子优先使用 `The character`、`The figure`、`The woman`、`She` 作主语（将 `1girl` / `girl` 限制在标签槽内），并在躺卧/放松姿态上示范骨骼支撑与构图几何写法。

---

## 6. 跨包重复的否定管束口号与重复文件

- **涉及文件**：全部 11 个技能的 `SKILL.md` 及 `references/background.md`、`references/sources.md`
- **问题现象**：
  - 诸如*“不为了显得完整而补写相邻阶段”“不回退上一阶段”“不宣称已出图验证”“不捏造未确认标签”*等防御性管束语句在每个 `SKILL.md` 和 `references/*.md` 中重复出现数十次，占据大量篇幅却稀释了核心操作指令的权重。
  - `background.md` 在 3 个技能包中完全重复，`sources.md` 在 10 个技能包中高度重复。在单平台合包或联动加载时应当去重。
