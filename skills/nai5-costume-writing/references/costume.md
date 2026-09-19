<a id="writing-costume"></a>

# 已定服装的表达与修词

本文件只承接已定服装或明确部件修改。共同语法、原串、完整字段与实际预设以 “写法规范与交付边界”（`nai5-writing`：`references/conventions.md#writing-conventions`） 为准；不重新设计角色衣橱，不因为词库没有某个名字而删掉设计。

<a id="costume-entry.s03"></a>

## 服装片段的交付边界

### 服装提示词的专用交付边界

当用户要“服装提示词”“把这套衣服转成 NAI 提示词”或同义任务时，本节优先于基础层的完整画面字段模板：

- 默认先输出角色已知且必要的固定可见提示词，再紧接服装描述；不把 OC 名字本身当作模型已知角色标签。用户明确只要衣物串、不带角色时仅交服装；缺失外貌不为了补槽而编造。
- 不包含人数、通用姿势、表情、镜头、场景、背景、光影、氛围、画风、质量词或 UC。服装自带的包与武器若必须说明携带方式，可保留一句最短的佩戴、手持或肩扛关系。
- 当前资料中的固定特征用于设计适配，按本次交付范围选择必要可见项；资料里的场景与动作不自动进入服装片段。
- 默认只给一个可直接复制的代码块，不附设计摘要、术语映射、参数或排错说明；用户明确索要时再补。
- 新写部件按[服装表达](#costume-writing.s06)一次定义、以部件为主语，并使用正向目标形态。
- 逐字原串和单点局改按“用户事实、原串与本次可见范围”（`nai5-writing`：`references/conventions.md#shared-facts`），已有否定句与权重也保留，不为片段规范重写。

<a id="costume-writing.preamble"></a>

## 服装部件表达

目标是把已经成立的服装设计转成 NAI Diffusion V5 容易识别、关系清楚、便于排错的“角色固定提示词＋服装片段”。默认成品不是完整画面提示词；本模块的专用交付约定优先于基础层的完整画面模板；本项目 v1.1 语法与用户原串保留规则仍适用。

转换服装时，使用用户当前给定和实际启用资料中的固定外貌，检查帽子或兜帽是否遮住关键发型、衣领如何接住长发、袖口与手套是否影响手臂、袜靴如何衔接腿脚，以及配色是否保留识别锚点。翅膀、尾巴、角和兽耳作为固定可见特征照常写入，默认不为它们描述洞口、分片、系带或防穿模结构。清理角色资料中的人数、通用姿势、表情、镜头、场景、背景、光影、氛围、画风和质量词，再把必要的固定可见角色提示词放在服装描述之前；OC 名字本身不作为模型已知角色标签。没有外貌资料时只写已有事实；用户明确只要衣物串时不附角色特征。

<a id="costume-writing.s01"></a>

### 先写“视觉意图清单”

不要直接从中文设计稿逐词翻译。先按以下顺序列出肉眼必须看到的事实：

1. 服装原型或主单品。
2. 整体轮廓与长度。
3. 领型、领口、袖型、袖口。
4. 外层与内层关系。
5. 腰部、下装与开衩/褶结构。
6. 腿饰和鞋履。
7. 材质、图案、滚边与装饰工艺。
8. 标志配件。
9. 不对称、滑落、掀起、敞开、塞入，以及服装配件的佩戴或携带关系。

用户明确的部件、颜色、材质、位置、数量和可见印字逐项保留，定稿转换不重新设计。新写内容中一个视觉事实只保留一个主要表达，避免同义词叠加或互相冲突；锁定原串不为去重而改写。

整理清单时给每个部件指定唯一落点。颜色、材质、长度、轮廓、装饰和穿着关系全部并入该部件的同一条描述；后文不再以概括标签或补充句重复它。

保留定稿所依赖的设计效果：异质搭配写清各部件及必要关系，结构重组写清剪裁，材质或比例变化写清对应属性。按实际方案取舍，不因转换提示词而补加主题、共同纹样或内部融合细节。

<a id="costume-writing.s02"></a>

### 用 FASHIONPEDIA 确认现实术语

FASHIONPEDIA 用于确认“这件东西现实中叫什么、结构含义是什么”，尤其适合查：

- 服装大类和轮廓。
- neckline、collar、lapel、sleeve、cuff。
- opening、closure、pocket、pleat、dart 等结构细节。
- 面料、纺织、装饰工艺和配件。

为关键项目记下“现实术语＋一句可观察定义”。若查不到原书，可使用博物馆藏品说明、服装院校或可靠术语资料交叉核对；不要只信商品标题。

<a id="costume-writing.s03"></a>

### 在 Danbooru 查 AI 对应名称

需要确定规范名的关键术语应核对标签含义与用例。已有可用的 Danbooru 查询工具时优先使用；否则查官方/镜像 API 与对应 wiki 页。无法查询时用普通类别词和可观察关系表达，不制造下划线标签或声称已验证；用户专门要求核实时说明未能确认的项目。

Danbooru 标签接口支持 `name_matches`、`fuzzy_name_matches`、`name_normalize`、`name_or_alias_matches`、`hide_empty`、`is_deprecated` 和按 `count` 排序。例如可以从以下思路开始，再按实际接口做 URL 编码：

```text
/tags.json?search[name_or_alias_matches]=TERM*&search[hide_empty]=true&search[is_deprecated]=false&search[order]=count&limit=20
```

逐项检查：

- `name`：规范拼写，而不是自己猜的下划线形式。
- `post_count`：是否有足够用例；高频只代表常见，不代表语义最精确。
- `category`：是否真是普通标签而非角色、版权或元标签。
- `is_deprecated` 与别名：避免使用已废弃或仅为别名的词。
- wiki 定义与样例图：确认模型语境中的含义和边界。

匹配优先级：精确规范标签 → 已确认别名对应的规范标签 → 语义较宽但稳定的标签 → 自然语言说明。找不到标签时，绝不能把现实英文名直接改为蛇形命名并声称“已验证”。

建议保留一张内部映射表；只有用户明确要求术语解释时才展示：

```text
视觉意图 | 现实服装术语 | Danbooru 规范标签 | 证据/置信度 | 无标签时的回退写法
```

<a id="costume-writing.s04"></a>

### 选词层级

按“主名词 → 轮廓 → 结构 → 材质 → 表面装饰 → 穿着状态”选择词：

- 主名词：dress、jacket、skirt、boots 等，确定它是什么。
- 轮廓：fitted、oversized、cropped、high-waisted、long 等，确定整体形。
- 结构：具体领型、袖型、褶、开衩、开合、层叠。
- 材质：denim、leather、satin、knit 等，必须能影响可见质感。
- 装饰：lace trim、embroidery、applique、print、frill 等，区分工艺。
- 状态：open、unbuttoned、slipping、tucked、wind-lifted 等，通常涉及关系。

按部件保留使设计成立的可见信息，不以修饰词数量删掉用户指定的服饰事实。把“luxurious、premium、detailed、fashionable”改成模型能画出的材质、结构和工艺。

颜色紧贴它所修饰的衣物，例如 `navy jacket, ivory blouse, burgundy ribbon`，不要把一串颜色与一串单品分开放置。

同一部件采用“一次性定义”：

```text
dark-purple knee-high boots with segmented mother-of-pearl armor panels, outward-curling cuffs, low tarnished-silver wedge heels
```

不要先写 `knee boots`，后面再用完整句重复靴子的颜色、护甲、鞋口和鞋跟。

<a id="costume-writing.s05"></a>

### 标签与自然语言的分工

优先使用标签表达：

- 有稳定标签的服装类别、颜色、材质、图案和独立配件。
- 单一、离散、没有主体歧义的视觉事实。

优先使用不加引号的自然语言句子表达：

- 层与层之间谁在上、谁露出、谁被塞入。
- 单侧滑落、左右不对称、衣摆被风掀起等状态。
- 没有单一 Danbooru 标签的自定义裁片、帽兜与长发关系、袖口与手部关系。
- 多角色之间容易串属性的衣服关系。

句子也以部件为主语，不以角色为主语：

```text
Six overlapping petal-shaped panels form a layered black overskirt around the waist.
```

不要写 `She wears a layered skirt...`。若句子已经完整定义了这个部件，也不要在前后另列 `layered skirt, overskirt` 重复召回。

<a id="costume-writing.s06"></a>

### 用户服装串写法

服装片段默认采用紧凑名词短语：先写颜色、材质、形制与部件，再用 `with` 或短关系句收纳该部件的细节。这是表达方法，不依赖特定 OC 库：

1. **部件一次写清。** 一个部件只出现一次；同义标签、宽泛标签和完整句不围绕同一部件重复堆叠。
2. **部件直接定义。** 使用 `[颜色/材质/形制] + [部件] + [with 细节]`，或让部件成为句子主语。避免 `She wears...`、`The character has...` 等角色引导句。
3. **新写内容定义正向目标。** 直接描述部件的实际形态，未采用样式不写，也不主动加入负权重排除块。用户锁定原串时，已有否定句与权重按 [入口局改约定](#costume-entry.s03) 保留。
4. **按穿着位置排序。** 可先放整套原型或最关键的自定义结构，再按头颈、上身、腰胯、下装、腿脚、配件排列。与某部件绑定的材质和装饰紧跟该部件，不另开全局材质清单。
5. **关系才写句子。** 交叉、缠绕、覆盖、从某处延伸、单侧位置和层叠先后用简短正向句；普通颜色、材质、长度和类别用词组。
6. **可见信息才落笔。** 穿脱方式、隐藏安全层和设定解释若画面不可见，不进入服装片段。
7. **道具关系只留一句。** 包、巨剑、镰刀等是造型核心时，用最短的正向关系明确斜背、肩扛、手持和方向；这属于服装配件的可见状态，不扩写成通用姿势或战斗动作。

<a id="costume-writing.s07"></a>

### 服装片段的组织示意

[片段边界](#costume-entry.s03)统一决定是否带角色和字段。下面示意已知必要特征与衣物的先后；每个部件一次定义，关系才写句子。明确只要衣物时省略第一个槽，局部替换只交指定片段。

```text
[角色固定外貌、体型、物种特征与识别锚点], [服装原型与核心结构], [从上到下的各部件及其完整属性], [必要的部件关系句]
```

需要场景、动作或完整字段时转[完整画面导出](#costume-writing.full-export)，不要让片段格式截断本次请求。

<a id="costume-writing.full-export"></a>

### 将服装放入完整画面

先按“字段职责：先选画面类型”（`nai5-writing`：`references/conventions.md#field-contract`）选择普通插画或漫画。普通画面动作、镜头、场景、光影在主串，已知可见外貌与服装在对应 Character；漫画将各格可见衣物和状态写入对应框。印字按“文字渲染”（`nai5-writing`：`references/conventions.md#general-writing.s01.h05`）保留原文与载体。使用黑白或半黑白时，对所有待输出字段执行“按需色彩参考”（`nai5-writing`：`references/conventions.md#shared-color`），不修改原色事实。

完整导出执行“完整导出的质量词与 UC”（`nai5-writing`：`references/conventions.md#shared-quality`），片段省略质量和 UC 的规则不再适用。下面保留完整画面基础 UC 的原样参考；它是去冲突的起点，不是所有服装图必抄的固定串：

```text
lowres, artistic error, film grain, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, chromatic aberration, dithering, halftone, screentone, multiple views, logo, too many watermarks, negative space, blank page
```

有服装印字、logo/徽记、留白、网点、多视图或多人时，按目标检查实际生效的正向、UC 与预设；只改手写词不能抵消预设冲突。局部修改仍保留原来的其他字段和完整设置，不借转换重构。

<a id="costume-writing.s08"></a>

### 易误用词与排错

迭代用户给出的生成图时，先把问题归到“服装原型、轮廓气质、搭配或融合关系、核心识别点、道具可读性、携带关系、细节负载”中的一项。已经画对的部位保持不动，每轮优先重写一个失败层级。复杂武器若在用户提供的实际图中持续读错，先修部位和关系；用户允许改设计时可简化轮廓或更换类别，锁定部件不直接删掉。若问题属于设计本身，说明具体选择并按用户意图接 `oc-costume-design`；已有设计不在修词时擅自变更。用户只要写法修复时，继续表达既定结构、材质、比例和穿法。提示词保留清楚的整体轮廓、视觉层级和使方案成立的可见特征，不预设核心识别点的数量或部件类别。

- `loose socks` 通常指堆堆袜/泡泡袜，不表示“袜子松到滑落”。
- `single thighhigh` 表示只穿一只，不表示一双袜子中有一只下滑。
- `uneven legwear` 可描述左右不同，但不总能稳定表达滑落过程；需要时补句子，如 `One sock has slipped down to her calf while the other stays pulled up.`
- dress、gown、robe、kimono 不是可随意替换的近义词；先核对剪裁和文化语境。
- sheer、translucent、transparent 的透明程度不同；同时说明是哪一层透明。
- print、embroidery、applique、lace、trim、frill 是不同的表面或边缘工艺。
- 同一部位若出现两个主名词或冲突长度，先删词，不要马上加权。
- 新写正向服装描述通过定义 A 的形态排错，未采用的 B 不进入正文；用户要求原串保留时，不改其中既有的排除表达或权重。

排错顺序：先检查主体归属 → 删除冲突词 → 把复杂关系改成句子 → 调整顺序 → 最后才小幅加权。有授权且确实进行出图比较时，保持其余设置与 seed 稳定、只改待验证变量；仅进行文字改写时不把设想称为出图验证。

<a id="costume-writing.s09"></a>

### 服装交付检查

按“写法规范与交付边界”（`nai5-writing`：`references/conventions.md#task-contract`）检查内容与范围，片段按[片段边界](#costume-entry.s03)只给可复制代码块：

```text
[角色固定提示词], [服装提示词]
```

多个方案各自给具名代码块，角色特征只用对应人物的已知必要项，明确只要衣物就省略角色。需要完整画面时按[完整导出](#costume-writing.full-export)，不能被默认片段格式截断。术语映射与排错过程不默认附上；用户明确要核查/解释时如实给已证实与未能确认的项目。


术语查询来源见 “查询依据”（`nai5-writing`：`references/sources.md#costume-writing.s10`）。
