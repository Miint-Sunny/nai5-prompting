<a id="writing-conventions"></a>
<a id="task-contract"></a>
<a id="general-entry.preamble"></a>
<a id="comic-entry.preamble"></a>
<a id="comic-entry.s04"></a>
<a id="comic-entry.s07"></a>
<a id="costume-entry.preamble"></a>
<a id="costume-entry.s01"></a>

# 写法规范与交付边界

本职责把已确定的内容写成 NovelAI 提示词，或按本次要求修改现有词句。语法、字段、原串、质量与 UC 只在写法侧确立。内容可直接来自用户；不以先读构思文件或重新确认作为转换前提。

| 当前请求 | 交付范围与选读 |
|---|---|
| 已定普通画面要完整词 | 本契约与 [普通写法](illustration.md#general-writing.s02)，交本次完整字段 |
| 已定分镜要 NAI | 本契约与 “漫画提示词编译”（`nai5-comic-writing`：`references/comics.md#comic-adapter.preamble`），交各实际生成单元；不重写故事 |
| 已定衣物要片段 | “服装片段的交付边界”（`nai5-costume-writing`：`references/costume.md#costume-entry.s03`），不补整幅场景、质量尾或 UC |
| 服装进入完整画面 | 服装表达加当前普通/漫画字段，不让片段默认截断请求 |
| 指定词、原串或字段局改 | 以现稿为基准只改指定目标及获准范围；精确替换无需补全模板或加载其他领域 |
| 已有实际图需要修词 | 先核对应底稿和反馈，区分表达遗漏/冲突与内容设计问题；只修当前范围 |

语义已明确就直接写，不发明新剧情、额外道具或未经请求的服装变化。未定选择只是措辞时自行决定；若必须改变内容才可解决，指出具体决定并提出建议，不把写法修复伪装成已有授权的重设计。需要整体点子、构图、故事分镜或服装设计时，分别接 `nai5-ideas`、`nai5-illustration-composition`、`nai5-comic-storyboard`、`oc-costume-design`；这些是可选创作接续，不是写法的必读依赖。

完整新漫画的未审剧情先交分镜；已有定稿、已有确认或用户明确跳过审阅时直接转换。请求里有「直接给词」「只要提示词」「不用分镜」「直接能用的」这类说法，就算明确跳过：同一轮先给 4–8 行逐格简稿并标明是本次补的，再给完整导出；自己补的分镜不称「已定」「现稿」或「已确认」。明确反馈可执行时落实后按当前请求继续，不增加重复确认（范围外的连带改动仍按[精确修改](#writing-exact-edit)先列出）；仍在讨论或只要看修订稿时不擅自导出。服装已定直接转换，纯新设计尚未决定主案时先停在设计。用户当次终点优先，不因跨领域重开全流程。

<a id="writing-exact-edit"></a>

## 精确修改与保行为

用户限定了修改范围（一处或多处）时，只改范围内的内容，其余字符与表示形式原样保留，不顺手删词、加词、排序、标准化空格、修正语法或补模板。用户原串里的字段标签（`UC:`、`Character N:`）也属于要保留的表示形式。

- **连带改动只列不改。** 需要连带改变而本次范围未包括时，先交范围内的改动，再列出原因和拟改项，等用户答复；不能先改完再用解释扩大授权。
- **范围不清先问。** 用户给的范围本身有歧义时先问清再改，不先交一个按自己理解改好的版本。例：「把背景从教室换成海边，其它一个字都别动」——课桌、窗户算不算背景，先问。
- **交付形态。** 给完整原串（只有目标处变化），再用一行改动清单写明改了哪里。交付前和上一版逐字比对，清单以外不能有任何差异，UC 也一样。

已有整段改写授权只作用于未锁定部分。没有限定范围时，改动数量取决于本次问题，不设每轮固定处数。完整首稿按需要保留用户事实与必要关系，不凑锚点、物件或词数，也不为追求短而删指定内容。解释只说明实际改了什么、哪些限制仍在，未见图不声称修复了成图效果。

<a id="shared-facts"></a>
<a id="comic-entry.s01"></a>
<a id="costume-entry.s02"></a>

## 用户事实、原串与本次可见范围

先保留用户已经确定的剧情、镜头、页格数、读向、人物、服装部件、材质、颜色、位置、数量、道具结构与原文台词。当前要求、参考图和明确反馈优先；未指定的部分才按任务需要补足，新增设计不冒充用户事实。

角色资料只有用户提供或实际启用时才用；没有 OC 库就按本题已有事实完成，不臆造缺失外貌、性格、私有条目或偏好，也不把一次换装写回永久设定。OC 名字本身不作为模型已知角色标签。版权角色使用规范名触发常规外观，不凭印象补默认设计；用户明确的服装、配饰及外观改动仍逐项保留。名称核对见[角色名称](illustration.md#general-writing.s05.h07)。

**事实记录与当前画面分开。** 用户给定的事实完整保留，普通完整画面按[角色类型与字段](illustration.md#ordinary-identity)组织；漫画每个框取实际可见子集，画外事实继续保留在本次身份与状态记录里；“从现稿提取身份、状态和可见子集”（`nai5-comic-writing`：`references/comics.md#writing-comic-state`）按实际可见范围提取。用户明确要求某细节在本格可见时，它就是取景条件；镜头装不下时指出具体冲突，不能先裁掉再称为省略。衣物片段按请求选择必要固定特征，明确只要衣物时不补人物。

**逐字原串优先于写作规范。** 用户锁定的文字、空格、标点、年份、数值、指定权重与表示形式照原文保留；局改只动指定目标，不为了去重、正向措辞、规范语法、颜色检查或补模板改动其他部分。需要连带修改时先说明具体关系，不能把局改扩成整体重写。完整改写授权只作用于未锁定部分。

画师串只来自用户原文或实际启用资料【完全模仿】节明确给定的固定串；名字列表或频次表不是配方。没有来源就省略，确需留位置时用独立一行 `<画师串：自己贴>`。有串时其顺序、权重、空格和年份照原文保留，组织方式见[样式块](illustration.md#general-writing.s02.h03)。

文字冻结、忠实转换或单点原串修改只用已有文字，不能新增对白、旁白和拟声词。声音内容由分镜或用户当前要求确定，具体表达见“文字只在需要的格里出现”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s05`）；明确无字或静默的要求优先。

保留细节不意味着机械扩写：不凑装饰数量、不为压短删锚点；先减少无作用的同义重复与未指定细节。既定设计与取景不在本次转换中重做。

<a id="field-contract"></a>
<a id="general-entry.s01"></a>
<a id="comic-entry.s06"></a>

## 字段职责：先选画面类型

基础语法、事实与原串、文字渲染、质量和 UC 统一按本文件通用规则。字段分工按当前实际交付选择，不能让一种画面的默认覆盖另一种。

| 交付 | 主串 | Character 内容 | 人数和定位 |
|---|---|---|---|
| 普通完整插画 | 人数、动作、表情、镜头、场景、光影与质量尾 | 对应人物的外貌和服装；施受前缀及相应表情例外见[多人交互](illustration.md#general-writing.s06.h13) | 主串开头只计一次；多人逐人分栏，单人简单外貌可不分栏；人物编号与实际栏位一致；角色位置由用户自己定，附注不给 |
| 漫画完整导出 | 本次生成单元的去重人数、简短布局、模式与质量尾 | 一次局部出场或画面的容器，写画格位置/大小、视图及镜头，再写本格可见人物、动作、状态、必要环境与文字 | 身份、底层格、覆盖和框分别判断；同一身份跨格重复不增加人数，同格可识别人物各一框，匿名局部互动可合框；用角色位置功能指定分格时，附注给每个框落在所在画格的位置 |
| 衣物片段 | 一个可复制片段，不展开完整画面字段 | 本次需要的已知固定特征接服装；明确只要衣物则省略角色 | 不补人数、通用动作、场景、质量尾或 UC，详见“服装片段的交付边界”（`nai5-costume-writing`：`references/costume.md#costume-entry.s03`） |
| 点子、设计、文字分镜或局改 | 按请求给相应成品 | 不为完整模板补字段 | 已有页格与人物记录仍保留，交付只到当前请求的范围 |

完整提示词的主串直接开写，不加 `Prompt:` 显示标头；保留英文半角冒号字段 `Character N:` 与 `UC:`。实际工具的 `prompt`、`negative_prompt` 等参数名称和结构依真实接口，不因显示格式而改名。多个完整方案或生成单元分别给足可复制内容，不共用角色栏、不写“同上”。**代码块只放可以直接复制的最终内容**；改前对照、原串回显和说明放在代码块外，改前对照标明「原」。

漫画人数按**实际生成单元中出现的不同身份**去重：同一位女性反复出镜是 `1girl`，两位女性轮流单独出镜是 `2girls`。整页按本页、拆组后按该组；不按单格最大人数、格数或框数计人，多格不加 `solo`。细则见“生成单元、画格称呼与输入框编号”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s01`）。普通画面的 Position 与互动前缀不构成逐格寻址。漫画用角色位置功能指定分格时，按下一段在附注里逐框给位置，不写进提示词正文。

参数只在用户询问或排查时给。完整导出附注以当前需要为限，包括不确定词兜底、必要设置调整和改动说明，不要复述内部流程。**用角色位置功能指定漫画分格时，附注逐框给角色位置**：先写「角色位置：在角色提示词区把位置从 AI's Choice 改成 Custom，点 Character Positions 打开画布，这样放」，再按每个框所在的画格写方位，2×2 四格就是框 1 左上、框 2 右上、框 3 左下、框 4 右下，同一格有两个框时都放在这一格的区域里、按站位分左右。V5 的画布可以把角色放在任意位置，模型会跟着摆放画，所以不用 V4 / V4.5 的 5×5 网格格名。这只是设置建议，没有实际操作不说已设置。**普通插画和多人图不在附注里给角色位置**，由用户自己定；用户问到怎么摆时再给建议。纯片段默认只有代码块，用户明确要术语核查或解释时才附相应内容。

<a id="shared-quality"></a>
<a id="general-writing.s08"></a>

## 完整导出的质量词与 UC

本节只用于完整导出；点子、分镜、设计、衣物片段和单点原串修改不补完整字段。只交文本且未给开关状态时按预设关闭写足；实际工具写入前检查真实生效的预设。

**质量词按预设关闭时写全，先判断画面要不要文字：**

- **无文字**：主串最末尾默认 `very aesthetic, masterpiece, no text`。
- **需要文字**：主串最末尾用 `very aesthetic, masterpiece`，不带 `no text`；文字与载体按开篇「文字渲染」写清。
- 需要更高完成度时再追加 `best quality`、`amazing quality`、`absurdres`。
  仍只写一组，放所有句子之后。预设开启时按实际附加内容删去重复项；
  有字时移除或关闭预设中的 `no text`，不能只从手写主串删掉它。
- 有本图负权重排除时，它另起一行接在质量尾之后，是主串最后一行（见下文 UC）。

**以下是按需词条，不是默认质量尾：**

| 词条 | 什么时候考虑 |
|---|---|
| `fine fabric emphasis` | 确实要突出织物细节时；不为无关画面追加 |
| `newest` | 要尝试这类风格修饰时再选；不承诺因此提高质量 |
| `cinematic lighting` | 画面确实需要电影式光效时；普通光线或简洁画面不自动追加 |

这些词只在画面需要时选择，不自动追加。
`high/ultra complexity` 是功能开关，默认不加，见开篇「V5 开关」与 [§3.10](illustration.md#general-writing.s05.h10)。

**UC 沿用用户自己的那套；本图不想要的元素不进 UC：**

- 用户给出或当前工具提供了自己的 UC 时，照原文沿用，顺序、权重和空格都不改；没有时用基础排除串：
  `lowres, artistic error, film grain, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, chromatic aberration, dithering, halftone, screentone, multiple views, logo, too many watermarks, negative space, blank page`
  要 SFW 时最前面加 `nsfw`。
- UC 里与本次目标冲突的项直接删去；不冲突的不删，也不另外提醒用户。只删不换，不自造替代词；删一项时连同它后面的逗号和空格一起删，加权段里不留空位（`2::extra characters, extra fingers, ::` 删去 `extra characters` 后是 `2::extra fingers, ::`）：
  - 漫画、分格、多视图（全彩漫画同样）删去 `multiple views`、`halftone`、`screentone`；
  - 多人图删去 `extra characters`，只删这一项，同一加权段里的其他项保留；
  - 画面要出现 logo、徽记、印字或编号时删去 `logo`；要留白构图时删去 `negative space`；要整幅空白页时删去 `blank page`。
- 预设开启时按实际内容去重，只删除它已经附加的项；预设本身含有与画面冲突的词时，
  也要移除冲突词或关闭该预设。不能只改手写 UC 而保留预设中的冲突。

**本图不想要的具体元素写成正面负权重**：另起一行放在质量尾之后，作为主串最后一行，不追加进 UC。例如要浓色时写 `-1::muted color, pale color, flat color::`，不要油光时写 `-1::oiled skin, shiny skin::`；不足时按[权重](#general-writing.s01.h01)加深。
**多人图不写 `extra characters`**，也不照抄单人模板里加权排除额外角色的段落（[§4.9](illustration.md#general-writing.s06.h23)）。
上述基础串是本文的输出约定。

---

**生成文字的判断覆盖整个实际生成单元。** 任一格的对白、旁白、声效或道具字都算有字；有字页不能用全局 `no text` 压住静默格。明确后期排字时，原文在独立文字清单里，生成引号不再重复原文，质量尾按生成图无字处理。

画面要出现文字、编号、logo 或徽记时，UC 里会压掉它们的项按上文删去，也不另加 `text`、`numbers` 这类泛化排除词；颜色同理，不能用排除项压掉本图要的颜色。必要说明放代码块外。

`negative_prompt` 不填“用默认预设”等说明文字。清空手写 UC 不等于关闭预设。若当前工具不能移除冲突词，明确用户还需关闭或调整哪些预设，再交与该设置一致的内容；没有实际操作不声称已设置。用户明确不用质量词或指定原串时按其要求。

<a id="general-writing.s01"></a>

### 语法与能力边界（画材与规格：引擎认什么）

> 当前环境实际提供运行时 NOTE 时，仅按其中适用于当前模型/接口的实际能力与可用字段使用；它不覆盖用户本次内容、冻结原串或修改范围，也不假定任何环境必有注入。
> 没有该 NOTE 时直接使用本规范，无需另找摘要版。
> 语法 = 引擎认什么（合法性）；本篇其余各章 = 其上怎么组织才稳（有效性）。

<a id="general-writing.s01.h01"></a>

#### 权重

| 写法 | 效果 |
|---|---|
| `1.2::tag::` | 增强，作用到 `::` 结束 |
| `0.5::tag::` | 弱化（0–1 区间） |
| `-2::tag::` | 负权重，定向移除或概念反转 |
| `{tag}` / `[tag]` | 旧语法，只在读旧串时理解，自己写用数值 |

常见增强取值包括 **1.1–1.5、2**；弱化可见 **0.4–0.9**，也有更细的小数配比。
负权 **-1 到 -5** 都有使用。它们是可调取值，不代表最佳强度，**默认仍不加权**。
V5 的权重在 **1.0–2.0** 区间非线性变化明显，**1.3–1.8** 是调 tag 权重最值得
关注的区间（4.5 要到 3.0–4.0 才有同等感知）。

**默认不加权。** 只在实测某层效果不足时才对该层加权，不为加权而加权。用负权重排除本图不要的元素不在此列，写法见[完整导出的质量词与 UC](#shared-quality)。

负权重的两种用法：
- **定向移除**：`-1::hat::`，不足时加深到 -3
- **概念反转**：白背景虚空 `-1::simple background::`；画面缺色 `-1::monochrome::`

**负权重块可按排除项模板理解和复用**：既有画师串中的压制词，随选定原文保留；
自己写时按上面两种用法，只排除用户明确不要或与本图目标直接相反的元素，不凭空猜造，也不为保险堆排除项。
常见排除目标有 `watermark`、`crowd`、`upscaled`；`artist collaboration` 也可能是
画师串的技术性压制项。`simple background`、`flat color` 等则可能用于概念反转。
降权也可能是在调画师配比，不能一概理解为压低次要画面元素。

`::` 可以闭合任何未配平的 `{` `[`。
数字权重**不写闭合 `::` 会作用到之后所有 tag 直到结尾**——不是只影响一个词。

<a id="general-writing.s01.h02"></a>

#### 容量与版本

- 本文默认按 **V5 Full** 写；Curated 只在任务单独指定时用，同一条提示词跨模型需要重新检查效果。
- [官方模型页](https://docs.novelai.net/en/image/models/) 列出的有效提示词容量约为
  **Full 1471 token、Curated 703 token**（2026-09-14 核对）。画师串和风格块也计入，
  按所选模型的实际计数与限制处理，不保证超出后仍能生成；不为凑容量设统一写作长度。
  画面内文字的字符限制另见下方「文字渲染」，不要与提示词 token 混算。
- 图像参考与局部重绘按**所选模型的当前界面**确认，不能从通用功能页推定每个 V5 变体都已支持。
  截至 2026-09-14，[Precise Reference 文档](https://docs.novelai.net/en/image/precisereference/)
  仍标为 V4.5 专有；[Vibe Transfer](https://docs.novelai.net/en/image/vibetransfer/) 与
  [Inpaint](https://docs.novelai.net/en/image/inpaint/) 未列完整的 V5 Full / Curated 支持表。
- [Prompt Chunks](https://docs.novelai.net/en/image/promptchunks/) 可保存和复用提示词片段；
  增强功能以当前界面及 [Enhance 文档](https://docs.novelai.net/en/image/enhance/) 为准。

<a id="general-writing.s01.h03"></a>

#### 长度与运行资源

**长度跟着画面需求走，没有统一指标。** 多格漫画和多人交互通常需要更完整的说明。
首版按 [§0.4](illustration.md#general-writing.s02.h05) 写足锚点与关系；每个词都应能说出它在解决哪个画面问题，
重复质量尾和无作用的同义词堆叠应删去。
分辨率、步数、额度与计费以实际运行环境为准，参数参考见 [§7](illustration.md#general-writing.s09)。

<a id="general-writing.s01.h04"></a>

#### 分段

**用空行分段，一段一个职能。** 先把内容分清，再决定需不需要额外的块标记。
`<artist>` / `<style>` 是人工组织手段，不是引擎语法；使用规则见 [§0.2](illustration.md#general-writing.s02.h03)。
不建议用管道符 `|` 代替空行分段。

<a id="general-writing.s01.h05"></a>

#### 文字渲染

用**引号**包裹要渲染的文字，前端会自动生成 `Text:` 块。
手动写 `Text:` 块会关闭这个自动功能。

**先判断画面是否需要文字，再选质量尾。** 不需要文字时用默认三连
`very aesthetic, masterpiece, no text`；需要文字时用 `very aesthetic, masterpiece`，
不加入 `no text`，并检查预设是否又附加了它。漫画静默格按“文字只在需要的格里出现”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s05`）省略文字指令；下方旧式语法示例只用于辨读原串。
**引号与载体成对出现**：引号里的字必须有个载体（气泡 / 纸条 / 招牌 / 屏幕），
用句子写清载体和位置；只有引号没有载体，字会飘在不该在的地方。

样式和位置用自然语言描述：

> A handwritten speech bubble with green text and a white background, floating next to
> the purple haired girl's head, "Hello, world!"

支持英语、日语、中文（简繁皆可）。中英日都可用双引号；**日语还可以用半中括号**。
4.5 的老方法（提行两次 + 大写 `TEXT` 后跟文字）**仍然有效**，可与引号法结合。
多条文本时：用自然语言写清**谁说哪句、什么样式**（"A is saying, \"…\" in green text
inside a white speech bubble, while B responds …"），防止多条文本互相串。
[官方文字渲染专页](https://docs.novelai.net/en/image/textrendering/) 标注
**Full 750 字符、Curated 374 字符，包含空格与换行**（2026-09-14 核对）。
Models 概览对同一数值使用 token，官方两页单位不一致；本篇引用文字专页的字符单位，
实际以界面限制为准。官方确认英、日、中及若干其他语言；不同语言的生成效果仍需检查。

**反过来也成立：不想画文字就别用引号**——叙事句整段包引号会被当成要渲染的
文字（[§0](illustration.md#general-writing.s02) 常见错 6、[§4.8](illustration.md#general-writing.s06.h12)）。

<a id="general-writing.s01.h06"></a>

#### 语言

既有示例包含整条中文与整条日文描述。下述是写作策略，
不将不同语言的效果相同或优劣次序当作官方保证。

**策略**：英文为主——简单描述、常用 tag、明确画面要求优先英文；
**很长、结构复杂、或英文难准确表达的句子直接写中文**，交给 V5 的自然语言理解。
有歧义的概念用中文钉死（play go 直译有歧义 → 直接写「下围棋」）。

<a id="general-writing.s01.h07"></a>

#### 多角色（语法侧）

- 角色数量、可用栏位和定位方式按当前模型、界面或工具的实际能力确认，历史样例人数不作为通用上限。各身份分别保留，不为槽位合并身份或删人
- 仅在实际提供角色定位时，按本题身份将 prompt 内的角色编号/顺序与真实栏位及对应定位匹配
- 普通插画角色栏写外貌服装，施受前缀例外见[多人交互](illustration.md#general-writing.s06.h13)；漫画逐格框的专用分工见[字段职责](#field-contract)
- 复杂互动（多人、动作纠缠、道具交换）用分段模式写死归属
- 串味处理：句子里写死归属 + 该角色 UC 栏排除对方特征 + 检查人数 tag 没在角色栏重复

<a id="general-writing.s01.h08"></a>

#### 整页自然语言与旧式分格示意

V5 可用自然语言描述整页分格。当前漫画默认采用“字段模板与先后顺序”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s02`），人数、静默格和字段按[共同契约](#field-contract)。以下原串仅用于理解旧式 `Panel N` 文本如何绑定格内事件与文字，不作为当前漫画默认输出模板（当前四格默认 2×2、从左往右，见“字段模板与先后顺序”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s02`））；用户明确要求保留这类原串时按原形式处理局改。

```
4koma, comic, speech bubble, emphasis lines, 1girl, school uniform.
The page reads top to bottom in four equal panels.
Panel 1: she is asleep at the desk, cheek flattened against an open book.
Panel 2: the alarm goes off; she jolts upright, hair sticking out, eyes still shut.
Panel 3: close on her face as she registers the time, mouth open, sweat drop.
Panel 4: she is already gone — only the toppled chair and a slice of toast in mid-air remain.
```

上例展示事件逐格组织，未写具体对白。下例展示“哪格、谁说、什么载体”的就近绑定：

```
4koma, comic, speech bubble, 1girl, school uniform.
The page reads top to bottom in four equal panels.
Panel 1: she is asleep at the desk. A small speech bubble above her head reads "zzz".
Panel 2: the alarm goes off; she jolts upright. A large jagged bubble beside her
         reads "I'm late!" in bold black text.
Panel 3: close on her face as she registers the time. No text in this panel.
Panel 4: only the toppled chair remains. A thin bubble drifting off-panel reads "bye!".
```

台词与所属格、说话者及载体当场绑定，不把全页台词集中到开头或结尾。旧例中的数字格名、`speech bubble` 和 `No text in this panel` 保留供辨读；当前漫画默认用位置/大小称呼，静默格省略文字指令，不从示例继承多余气泡。

格数、每格文字和复杂度共同影响串格风险；旧“四格以内、每格一句”的经验不能当稳定保证或硬上限。按用户已定页格和“字段模板与先后顺序”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s02`）表达，必要时提出分组生成，不能自行改成两次或删除文字。文字容量见[文字渲染](#general-writing.s01.h05)。

<a id="general-writing.s01.h09"></a>

#### V5 开关与旧限制（NOTE 没细说的三条）

- V5 新增 tag：`depthness` · `attractive male` · `low/medium/high/ultra complexity` · `has alpha`——
  只在跟画面直接相关时用，不当固定质量尾
- **Complexity 不是无脑加**：要看画师串、画面和内容——有的画师串不适合，
  简单画面、简洁内容也不适合加；它有一定**画面固化**倾向（实测有
  `-N::ultra complexity::` 负权重后画面反而变好的例子）。语义上 complexity =
  生成时的计算预算，steps = 采样迭代，尺寸 = 画布，三者不互替；
  低/超高两档偏特殊风格化，可能明显改观感
- 透明三词条：①`transparent background` = 左下角透明背景设置同效
  ②`has alpha` **加在光效/粒子词条之后**（提示这些特效需要透明生成）
  ③`alpha transparency` 让画面里的物体（魔法特效、火焰、伞等）在输出文件里真的透空，走 alpha 通道，
  多和 `transparent background` 一起用来做素材；完整画面里要画一把透明的伞，写 `transparent umbrella`，
  不用这个词（带完整背景时它常常没效果，或让局部像素变成半透明）。
  风格词改 3d 也能生效；比导演工具 removebg 不耗点、效果更好
- 年代感控制词条（官方称整体往特定时代偏移）：**实测无明显效果，不写进提示词**；
  想试的话在输出末尾以建议形式提
- 视觉小说素材词条：`visual novel art`（整体风格）· `vn bg`（背景图，可配
  high complexity + depthness）· `vn cg`（剧情事件图）· Q 版角色图、角色立绘
  （后两类推荐开透明背景）
- 不要沿用 V4 文档「最多六人」和 5×5 网格旧限制：官方写 V5 最多 22 个角色，角色位置是自由画布（[官方说明](sources.md#comic-sources.s03)）

<a id="shared-color"></a>

## 按需色彩参考

本段的漫画全彩默认、`manga` 风格串、逐格措辞及漫画实图归因只适用于漫画；普通插画或服装完整画面仅在用户明确请求黑白或限定保色时，取对应色彩转换与检查，不自动加 `manga`、改用漫画字段或替用户切换模式。具体方案沿用下述口径，用户指定的保色范围优先。

<a id="comic-continuity.s03"></a>
<a id="comic-entry.s03"></a>

### 色彩模式与输出前检查

色彩模式统一在本节选择与检查。

**新漫画未指定色彩模式时默认全彩。** 同一漫画的续页、局部改稿沿用已明确选择的模式；用户本次切换优先，其他任务或历史示例的黑白设定不成为新任务默认。

| 模式 | 主 Prompt 风格词 | 颜色处理 |
|---|---|---|
| 全彩（默认） | `manga`；不加 `monochrome` 或灰阶词 | 人物沿用本题已知原色，环境保留本来颜色，不做灰阶转换；仍按镜头提取可见外貌 |
| 半黑白 | `manga, {{{greyscale with colored eyes,greyscale with colored hair}}}` | 仅头发与眼睛保留原色；其余人物部位、服装、饰品、物件和全部环境转灰阶；不加 `monochrome` |
| 黑白 | `manga, monochrome` | 全部人物、物件、环境及光效去色相，头发与眼睛也转灰阶；保留明暗与结构 |


转换只影响本次绘制表现，不修改用户原始设定或实际启用的 OC 库，也不改变角色身份、服装结构、材质、剧情或已定台词。用户给出的服饰原色留在连续性记录；黑白/半黑白只转换绘色词，不删该部件。若用户另有明确保色范围，按本题范围处理，不拿默认色彩模式覆盖它。

<a id="comic-continuity.s03.h01"></a>

#### 全彩

主 Prompt 使用 `manga`，不附加 `monochrome` 或灰阶风格串。人物沿用当前用户设定或实际启用 OC 库中的可见外貌及颜色，环境保留原有色彩，不做灰阶修正；仍按各格取景省略画外特征，清理库内非身份的构图、动作等词。由黑白或半黑白切回全彩时回读本题角色原色及已定场景颜色，不能把上一版的 `pale/dark` 映射当作原始颜色，也不凭空给原本无指定色的环境强配色。

<a id="comic-continuity.s03.h02"></a>

#### 半黑白

主 Prompt 使用 `manga, {{{greyscale with colored eyes,greyscale with colored hair}}}`，保留用户指定串的顺序和三重花括号；不加 `monochrome`。

- 仅头发与眼睛自身保留原色，包括挑染、内层发色、渐变发、异色瞳；闭眼或裁切外不为保色强行补写。
- 其他所有可见部分转灰阶：肤色与妆容、眉毛睫毛、兽耳及耳毛、尾巴、角、翅膀、服装、图案、镶边、首饰与道具。发带、发夹、头饰不属于头发；眼镜不属于眼睛。
- 全部环境及表现效果转灰阶，包括天空、建筑、植物、饮料、烟火、背景、光源、反射、辉光、格线与字效。保色的头发或眼睛也不能把彩色光晕、投影或反射带到周围。

<a id="comic-continuity.s03.h03"></a>

#### 黑白

主 Prompt 使用 `manga, monochrome`。对人物、物件、环境、光效等全部去色相，头发与眼睛也转换，不能残留 `colored eyes`、`colored hair`、`colored background`、`selective color`、`sepia` 等彩色或局部保色指令。

去色保留明暗、轮廓和材质，不是删除整个外貌或物件。例如同一角色的浅色头发与深色外套，应在可见的各格一致复用；不要用删除全部颜色信息的方式导致深浅漂移。

<a id="comic-continuity.s03.h04"></a>

#### 转换与检查方法

**每次输出黑白或半黑白提示词都必须完成以下检查**，整页、续页、局部替换、出框与覆盖框同样适用。局部改稿检查待输出字段及其与当前主 Prompt 的模式一致性；不为检查扩写无关画格。

1. 先按镜头提取可见内容，再按色相所修饰的对象分类；半黑白仅放行头发与眼睛自身，黑白不放行任何色相。对象归属优先于单纯关键词匹配。
2. 检查主 Prompt 与每个 Character 框的词组、自然语言、下划线标签、权重组和样式片段。覆盖角色、服装饰品、道具、空镜、环境、照明反射及文字外观，不能只查人物。对白与旁白原文中的颜色词不作为绘色指令，不擅自改台词。
3. 将禁用色相改为 `pale`、`light gray`、`mid-gray`、`dark` 等合适灰阶，同时保留结构和光照强弱。黑、白、灰及无色透明可保留。留意隐含色相的材质/氛围词：`golden bell` 可改 `metallic bell`，`ruby pendant` 可改 `faceted gemstone pendant in dark gray`，`warm golden sunlight` 可改 `soft daylight`；保留金属、宝石与光源本身。
4. 最后反读输出：黑白无彩色泄露；半黑白的色相都明确属于头发或眼睛，其他内容全部灰阶；风格串与各框一致。检查 UC 及附加风格词有无与模式冲突的颜色指令，但不把原色词批量塞进 UC，也不靠大量负面词代替正向转换。用户画师串按原规则保留，不把画师名中的词误当色相。

以下是同一可见外貌的局部转换示例，用于检查颜色处理，不是完整 Character 框：

| 模式 | 外貌片段 | 环境片段 |
|---|---|---|
| 全彩 | `ice-blue long hair, crimson eyes, blue and white feline ears, dark purple star-patterned robe, golden bell` | `blue sky, warm golden sunlight` |
| 半黑白 | `ice-blue long hair, crimson eyes, pale gray and white feline ears, dark star-patterned robe, metallic bell` | `light gray sky, soft daylight` |
| 黑白 | `pale long hair, dark eyes, pale gray and white feline ears, dark star-patterned robe, metallic bell` | `light gray sky, soft daylight` |

上述检查确认提示词中的色彩一致性，不能称未经生成的稿件已验证成图不会漏色。

实际生成中的增格、漏人、错位气泡或合并时刻不能改称为预先设计。先核对对应字段与原稿，分别记录观察和拟采用的改写；用户愿意调整内容时才提出新的镜头或分组方案，不以避免生成漂移为由默认改导演。
