<a id="writing-illustration"></a>
<a id="general-writing.preamble"></a>

# 普通画面表达与修词

根据已有画面组织词组、关系句与角色字段；语法、精确修改和完整导出按 [共同规范](conventions.md#writing-conventions)。本文件不是创作前置：动作、机位与故事关系已经确定时直接表达，不为了写词再发明一次画面。相关研究与旧对照的证据范围见 [写法来源](sources.md#general-writing.s12)。

<a id="ordinary-identity"></a>

## 普通插画的角色类型与外貌分工

以下是普通插画的字段细则。漫画与服装片段先按[字段职责](conventions.md#field-contract)选择对应表达。

| 字段 | 装什么 |
|---|---|
| **主提示词** | 画师串 · 人数 · **动作 · 表情 · 镜头 · 场景 · 背景** · 光影 · 氛围色彩 · 技法 · 质量尾 |
| **Character 1/2… Prompt**（角色栏） | **只放外貌**，具体放多少**取决于角色是原创还是版权**——见下面那张表，在此确定后，后文沿用同一分类 |
| **Undesired Content（UC）** | 沿用用户自己的 UC，没有就用基础串，只删与本图冲突的项；这张图明确不要的东西写成主串最后一行的负权重，不进 UC（[§6](conventions.md#shared-quality)） |
| 参数 | 仅在用户问起或排查时给 |

本包把角色外观集中放进各自角色栏，便于核对归属和避免重复；这是本包的输出约定。实际接口允许哪些内容，以当前工具为准。[§0.1](#general-writing.s02.h02) 的旧对照记录用于说明选择依据。

<a id="general-writing.s02.h01"></a>

##### 角色栏放多少：按原创或版权角色区分

角色栏的详细程度取决于外貌信息的来源：原创角色依用户设定，版权角色可由规范名称触发常规外观。两类都完整保留用户明确指定的细节；历史反馈分别出现过擅删设定和擅补默认外观的问题：

| 角色类型 | 角色栏怎么填 | 最容易犯的错 |
|---|---|---|
| **原创角色**（用户给设定的） | `girl/boy/other` 打头，后面接用户给的**样貌锚点——那是硬约束**：发色 · 发型 · 瞳色 · 体型 · 种族特征 · 耳朵 · 角 · 尾巴 · 翅膀 · 标志性饰品，**逐项保留，不删减、替换或自行调整**。用户指定的服装同样保留；未指定的细节保持简洁，明确允许设计改动时再按范围处理 | **遗漏设定**——为压短而删除给定锚点，会改变角色的辨识特征 |
| **版权角色**（danbooru 认得的） | 以 `girl/boy/other, 角色名` 触发常规外观，**不凭印象补写默认设计**。用户明确指定的服装、饰品和外观改动逐项保留；未指定部分才用简洁成套说法 | **混淆来源**——擅补默认外观，或反过来把用户明确细节删成一个笼统换装词 |

两类共同的三条：

1. **性别词写在最前面**，`girl` / `boy` / `other`，不带数字。
   这一写法在已有角色栏材料中很常见；本篇把它作为统一的字段约定。
   性别词跟着**这个角色本身**，别默认 girl。
2. **作品名可省**，写了不算错但不是必须。独立作品 tag 与角色名括号中的作品信息是两回事。
   拿不准角色名对不对时补上作品名有帮助，认得就不用。
3. **动作 · 表情 · 镜头 · 场景 · 背景默认留在主提示词**。
   施受方向与相应表情的前缀例外见 [§0.1](#general-writing.s02.h02) 与 [§4.9](#general-writing.s06.h13)。

> 版权角色的**用户明确细节逐项写入角色栏**，即使与常规设定一致也保留；
> 换装 / 换发色等改动按 [§3.7](#general-writing.s05.h07) 写，不额外补回未指定的默认设计。
> 知识库边界期的新角色是第三种情况，走中间档，见 [§3.7](#general-writing.s05.h07)。

<a id="general-writing.s02"></a>

### 普通插画完整模板与落笔检查

本节用于普通完整画面；[角色类型](#ordinary-identity)决定外貌写多少，[字段职责](conventions.md#field-contract)区分漫画与衣物片段。完整交付按下面的顺序组装。示意中的尖括号填成本次内容；每个字段各用一个代码块，标题和解释放在块外。

**1. 主串。** 先从已定画面提取物件与姿势，再写关系句。物件清单包括手里操作的东西、承托身体的物件，以及决定遮挡或取景的实体；它们各自先有一个名词短语，短语保留已定的数量、颜色和形态。接着用句子说明谁接触它、放在哪里、遮住哪里。只列本图已有的物件。

```text
<人数；仅一名人物且无其他动物入镜时按需加 solo；无人画面写 no humans>, <持握物、身体支撑物及构图所依赖的物件词组>
<姿势、取景与机位词组>, <场景、时段、光线>
<谁的哪只手接触哪个部位、同一物件由谁承托、前后遮挡等关系句>
<本次确需的技法词>
<无字：very aesthetic, masterpiece, no text；有字：very aesthetic, masterpiece>
<本图排除项的负权重行；没有排除要求时省略>
```

主串到这里完成，再开始角色栏。质量尾属于主串，写在所有内容句之后、第一项 `Character N:` 之前；不能放在最后一个角色栏与 UC 之间。实际预设或用户指定原串另按[共同质量规则](conventions.md#shared-quality)处理。

**2. 角色栏。** 每人一栏，先填本栏的 `girl`、`boy` 或 `other`，再填外观。主串的人数不在此重计；年龄用后续外观词表达。

```text
Character 1:
<girl / boy / other>, <本次已知的外貌锚点>, <用户指定的服装与配饰>
```

具名版权角色在起手词后写规范角色名；用户明确的外观与服饰继续逐项写入，未指定的常规外观由名称触发。原创角色按已给设定填实，不用名字替代外貌。更多角色依次另开 `Character 2:` 等字段；无人画面省略角色栏。施受前缀的例外按[多人交互](#general-writing.s06.h13)处理。

**3. UC。** 另开一个字段，填入实际串：

```text
UC:
<复制用户 UC 或基础串，再只删除与本图明确要求冲突的项>
```

需要沿用用户提供的 `<style>`、`<artist>` 块时，按[样式块](#general-writing.s02.h03)原样放在主串之后；没有来源时省略，不补空块。它们不替代主串质量尾。以上是新写完整词的格式；用户指定其他格式或只做局改时，沿用用户的格式与范围。

**主串不带标头**（2026-08-31 起；旧版的 `Prompt:` 行不再输出）。
保留的字段名一律用半角冒号 `:`、英文（`Character 1` / `UC`），
跟 NAI 界面上的叫法一致。

**写这个模板时最容易犯的八个错（1–4 按实测频率排，5–8 是下游实测新收）：**

1. **完整外貌在两边各写一遍。** 完整外观清单放角色栏，主串不再复制。
   交互动作句可复用辨认角色必需的简短外观锚点；角色名仍留在角色栏。

   ❌ 主提示词 `1girl, solo, silver hair, ahoge, white dress, from below`
      ＋ Character 1 `girl, silver hair, ahoge, white dress`
      → 同一组外貌在两个字段重复；删除主串中的完整清单，让角色栏统一承载这些特征
   ✅ 主提示词 `1girl, solo, from below, snowy plains, backlighting, looking at viewer`
      ＋ Character 1 `girl, silver hair, long hair, ahoge, white dress, frills, white gloves`

2. **质量词收在第一段 tag 的尾巴上**，后面还有几段句子。
   它该在**所有句子之后**（后面只接本图负权重行），而不是第一段 tag 的结尾。

3. **反向漏**：动作、表情、镜头、场景、背景漏进角色栏。它们默认留在主提示词；施受前缀例外见 [§4.9](#general-writing.s06.h13)。

4. **按角色类型核对角色栏的详细程度。**

   **往多了写**：具名版权角色还凭印象补一遍默认外观。上面模板的第一种写法是给原创角色的；
   版权角色用第二种。历史实测的五人稿里，五格均额外补写了发色发型
   （同一个模型的四人稿没有这项问题）；这组记录提示需逐栏检查，不能据此确定人数与错误率的关系。名字已经带了设计，不需要再靠猜测补全。
   **用户明确指定的细节另当别论：逐项保留，不能按“版权角色少写”删掉。**

   **往少了写**：原创角色被"精简"掉锚点。用户给了发色/发型/瞳色/耳朵/角/尾巴/翅膀
   /标志性饰品这些，**逐项保留**，以免改变角色的辨识特征。
   角色栏较长时仍保留这些锚点；可精简未指定且不影响识别的服装细节，用户给定的服装锚点仍须保留。

5. **人数词重复或冲突**（下游实测出现过以下两种情况）：主提示词写了 `2girls`，
   角色栏又各写一个 `1girl`，拼起来就是 `2girls, 1girl, 1girl`；
   或者 `2girls, solo,` 同写——直接自相矛盾。对应约定是：
   **人数 tag 只在主提示词最前面出现一次**，角色栏只写不带数字的 `girl`/`boy`；
   `solo` 只配单人。

6. **叙事句包双引号**（同为下游实测）：明明不是对话也把整段句子括进 `"…"`——
   引号在语法层的含义是**要画进图里的文字**（见开篇「文字渲染」），
   模型可能真把句子当字画出来。句子直接写；只有确实要画对话气泡/字条时才用引号。

7. **反过来漏**：用户明确要画某几个字，产出里却只描述「牌子上有黑色字」，
   **没把那几个字用引号写出来**，就没有指定要生成的原文。要画的字必须原样进引号，
   连同载体一起写：`"営業中"` + 一句 "the wooden sign she holds reads …"。

8. **角色名和作品名只认 ASCII**（下游实测）：写 `空弦, arknights` / `阿罗娜, Blue Archive`
   未按本文约定使用规范角色名——**必须是 danbooru 的英文或罗马音写法**
   （`archetto (arknights), arknights`）。想不起来英文写法时按 [§3.7](#general-writing.s05.h07) 的中间档处理，
   **不用中文名代替规范标签**。

画师串来源与原文保留见[共同事实契约](conventions.md#shared-facts)，完整输出范围和必要附注见[字段职责](conventions.md#field-contract)。

**单人且外貌简单时可以不写角色栏**，把外貌直接写进主提示词、按 [§0.3](#general-writing.s02.h04) 的顺序放在人数后面。
两个及以上角色在实际角色栏足够时逐人分栏；容量不足时按下段实际能力处理。各身份仍分别组织，不默认合并、删人或拆图。

**角色组织与填写容量分开判断。** 普通多人画面按实际人物逐人组织角色描述，不能为省槽位把不同身份合并。历史样例出现过的人物数量与旧扩展的快捷填入数量，都不能当作当前模型的通用人数上限，也不能保证同等数量的角色稳定呈现。

实际可用的角色栏和填写方式按当前模型、界面或工具确认。若当前容量不足，保留完整人物与既定关系，说明具体限制，再按用户范围选择填写或生成安排；不默认声称多出的栏位可以手动补入。

<a id="general-writing.s02.h02"></a>

#### 完整角色外貌走角色栏，交互句只复用简短锚点

带角色栏的提示词中，外貌词更常放进角色栏，场景与技法更常留在主串。
下面仅供比较字段分工：按带角色栏的提示词计，两列可同时命中；这是使用现象，不是建议权重。

| 类别 | 出现在主提示词 | 出现在角色栏 |
|---|---|---|
| 发型发色 | 12.9% | 73.1% |
| 眼睛 | 31.2% | 71.9% |
| 服装 | 36.2% | 74.1% |
| 体征 | 55.4% | 76.8% |
| 角色名 / 作品名 | 2.9% | 21.5% |
| 画师串 | 92.9% | 2.6% |
| 技法词 | 65.4% | 4.1% |
| 人数 | 59.0% | 17.5% |
| 背景 | 59.4% | 5.1% |
| 场景 | 35.5% | 19.4% |

配饰两边都可见，完整外观清单仍按归属放角色栏；交互句只复用辨认必需的简短锚点，
例如 `the girl with headphones`，不把整套配饰重新列一遍。
已有材料也常把表情放进角色栏，**本篇默认仍是表情留在主提示词**。
**例外**：配合 `source#`/`target#` 前缀、标注施受气质的表情词
（[§4.9](#general-writing.s06.h13) 的 `smirk` / `blush`）可以随前缀进角色栏；没用前缀就没有这个例外。

**角色栏里的人数词不带数字**：写 `girl` / `boy` / `other`，不写 `1girl`。
`1girl` / `2girls` 只在主提示词最前面出现一次。
**多角色必须分栏**；单人且外貌简单时可以不分栏，按 [§0](#general-writing.s02) 的顺序直接写在主串。

<a id="general-writing.s02.h03"></a>

#### XML 块是人工组织约定，不是 NAI 语法

**NAI 不把这些标签解析成特殊语法。** `<artist>` 与 `<style>` 仅用于让人看清
画师串和技法串的边界；没有相应内容就省略，不留空块。
有串时只包原本的内容：`<artist>` 放画师串，`<style>` 放技法/画风词。
不要外推造出 `<content>`、`<scene>`、`<quality>` 等块；质量词直接放主串末尾。

**带串的完整输出**：两块后置在主串之后，`<style>` 在前、`<artist>` 在后，
各自空行分隔（[§0](#general-writing.s02) 模板）。这样让画面内容顶在最前。
既有材料中的串位置各不相同，位置统计不能替代这一输出约定。

<a id="general-writing.s02.h04"></a>

#### 主提示词里的顺序

按下面的顺序组织，角色外貌在分栏时移到角色栏：

```
人数 →  外貌  →  服装  →  表情  →  镜头  →  动作
      发型/体征/眼睛                    ↑
                          场景 · 背景 ──┘（在镜头之前）
                                              质量尾 → 最后
```

**人数放最前、质量尾放最后**。中间的镜头、动作、场景等按画面关系组织，
不把既有材料里的常见位置当成引擎规则；镜头词放在哪更有效尚无对应的位置对照。

---

<a id="general-writing.s02.h05"></a>

#### 迭代范围与表达密度

按 [精确修改](conventions.md#writing-exact-edit) 保留本次范围。首稿密度由已定内容决定，既不堆同义词也不删用户锚点；权重与复杂度按表达需要，不靠数字配额判断是否充实。确有不确定的词时说明回退写法，没有就省略。构图通常只需说明竖、横、超宽或方，具体尺寸在用户询问或制作需要时另列。

<a id="general-writing.s03"></a>

### 提示词是功能块的序列

一条 V5 提示词由若干**职能块**顺序拼成。NAI 不认识"块"这个概念——
分块是写作者的组织方式；本篇按原有写法经验将关键成分放在前部，具体位置效果仍取决于整条提示词。

用空行区分职能，不要求固定段数。一段能说清就不拆，复杂关系分段写。

| 块 | 装什么 | 组织参考 |
|---|---|---|
| **主体锚** | 人数、solo、关键独立物件 | **最前** |
| **场景 / 背景** | 空间结构、物件清单、天气时段 | 中前 |
| **动作** | 姿势、体位、手部动作 | **中后**（排在表情和镜头之后） |
| **关系** | 空间关系、道具归属、运动的进行中状态 | 跟着动作 |
| **镜头** | 取景、视角、机位高低、部位锚定 | **中后**，见 [§0.3](#general-writing.s02.h04) 的注意事项 |
| **光影** | 主光方向与性质、第二光源、投影 | 中后 |
| **氛围色彩** | 色调、饱和、情绪 | 后 |
| **技法风格** | 上色方式、线条、媒材、复杂度 | 质量尾之前 |
| **版式与文字** | 分格、贴纸、画面内文字 | 视需要 |
| **质量尾** | 质量词 | **主串的最末尾**，见下 |

不必全有，按画面需要取。
**完整外观清单与角色名走角色栏**；交互句只复用辨认必需的简短外观锚点，见 [§0.1](#general-writing.s02.h02)。

> **质量词只写一组、只放在主串的最末尾，写在句子之后**（带后置串块时，
> 串块在质量尾之后）——不是「tag 段的末尾」，
> 也不要在开头或中段再来一份。用 A 形态（tag 块 + 句子块）时，
> 尤其要检查质量词是否误收在第一段 tag 的尾巴上。

中间各块按画面需要排列；人数决定构成，质量词不描述内容，分别守住首尾。

<a id="general-writing.s04"></a>

### 每块两种笔法，判据是「这块内容用哪种说得准」

V5 同时支持词组与自然语言——官方原话是 "Just describe the image in your mind"，
同时又说 "prompting with tags is still fully supported"。
既有示例覆盖短词组与完整长文。

- **词组笔法**：短词组并列，逗号分隔。可以是 danbooru 规范 tag，也可以不是。
- **句子笔法**：自然语言，现在时或现在进行时，一段一个职能。

**写作判据**：词组列出对象及其属性，句子补出对象之间的关系。已有小样本对照支持这种分工，不代表每种内容只能用其中一种笔法。

- 关系＝谁在谁前面、离镜头多近、占画幅多少、光从哪来打在哪、动作停在哪一瞬
- 离散事实＝几个人、几只袜子、机位多高、什么姿势、什么取景

> 服饰或物件的加权可能连带改变姿势与构图；旧例中加权 `white bloomers`
> 曾伴随回望姿势。若修改一个物件词后构图也变了，回查该词及权重，
> 不把伴随变化直接认定为模型机制或所有任务的固定结果。

判据来自固定其余条件、只换被测笔法的出图对照。样本较少，只支持观察到的方向，
不能当成功率。正常出图种子随机；实验方法与局限见 [§10](sources.md#general-writing.s12)。

<a id="general-writing.s05"></a>

### 适合用词组表达的对象与属性

<a id="general-writing.s05.h01"></a>

#### 人数与主体
`1girl` `2girls` `1boy` `1other` `solo` `multiple girls`
多人时人数 tag **只在最开头出现一次**，角色栏里写不带数字的 `girl`/`boy`。

- `solo focus` **不是** `solo`：多人图聚焦一人时写 `2girls, solo focus`，两者并存合法；
  `solo` 只配单人图，跟任何多人数词同写都是自相矛盾。
- 动物和人同框时去掉 `solo`，人数标签照写（如 `1girl`），动物用普通名词写进画面，例如 `black cat`。
- 分格人数按[实际生成单元](conventions.md#field-contract)中出现的不同身份去重：同一角色四格仍是 `1girl`；两位女性轮流单独出镜仍为 `2girls`。多格不写 `solo`，不按格数乘人数。

<a id="general-writing.s05.h02"></a>

#### 种族体征
种族体征可直接用 `cat ears` 等词组列出，无需另写 "she has cat ears" 一类引导句。
`cat ears` `fox ears` `rabbit ears` `pointy ears` `elf ears` `horns` `cat tail` `fox tail` `wings`

<a id="general-writing.s05.h03"></a>

#### 镜头与视角 —— **含机位高低**
`full body` `upper body` `close-up` `cowboy shot` `wide shot` `portrait`
`from below` `from above` `from side` `from behind` `dutch angle` `foreshortening`
`straight on` `three-quarter view` `pov` `profile`

**机位高低用明确的视角 tag 表达。** 既有对照里，低机位句子未稳定压低相机，
`from below` 的方向更明确。

旧对照中，`from below` + `foot focus` + `feet out of frame` 的组合伴随近乎躺倒的姿势。
若当前只需要低机位，可只保留 `from below`；用户明确要求脚部焦点或裁切时，仍保留该要求并检查它与姿势的关系，不因这个旧例一概删词。

**「占多大」仍归句子**（见 4.4）：机位归 tag，占画幅比例归句子。

<a id="general-writing.s05.h04"></a>

#### 姿势与体位
`sitting` `standing` `lying` `kneeling` `squatting` `sitting sideways` `leg up`
`knees up` `crossed legs` `arm support` `head rest` `hand on own cheek`
`arms up` `legs up` `hugging own legs` `on side` `on back` `on stomach`

既有姿势笔法对照（其余条件固定）：

| 写法 | 结果 |
|---|---|
| 句子：`She sits sideways on the windowsill with one knee drawn up…` | **未执行清楚** |
| 词组：`sitting, sideways, leg up, arm support, head rest, hand on own cheek` | **执行清楚** |

这组句子样本出现了多余的腿和连接不清的髋部。它说明这次复杂姿势的表达没有落实，
不足以证明长句或细节本身必然造成肢体错误。沿用词组表达坐姿、支撑和抬腿，
需要说明哪只手撑在哪里、身体朝哪边转时，再补对应关系句。

<a id="general-writing.s05.h05"></a>

#### 服装状态 —— **先查语义再用词**
danbooru 服装 tag 里，**「一种衣服」和「一种穿法」长得很像，选错会静默把衣服换掉**。

| tag | 真实语义 | 常被误当成 |
|---|---|---|
| `loose socks` | **堆堆袜**，一种粗针棉袜 | ❌「丝袜堆下来」 |
| `single thighhigh` | **只穿了一只**，另一腿光着 | ❌「一只滑下来了」 |
| `uneven legwear` | 两腿袜子**不一样** | 语义对，但单独写未稳定推动不对称 |
| `asymmetrical legwear` | 两腿袜子不一样 | 不能替代具体状态句 |
| `thighhighs pull` | 拉扯丝袜的**动作** | 不等于已经滑落的状态 |

写 `white thighhighs, loose socks` 想要「白丝滑下来」，拿到的是**粗针堆堆袜**，
形制被换掉且不报错。

**使用服装状态词前核对定义与用例。** 仅按英文字面理解，可能把原本要改的穿着状态写成另一种衣服。

**形制归 tag，不对称与位置归句子**：重测中形制词能保住衣服类别，
状态句更能做出不对称，但「堆在哪」的精度仍不稳。详见 [§10](sources.md#general-writing.s12)。
> `white thighhighs, uneven legwear.`
> "One thighhigh has slipped down to bunch just below the knee."

<a id="general-writing.s05.h06"></a>

#### 部位锚定（`X focus` 家族）
这组词用于提示关注的部位；沿用已有材料中的尝试顺序，具体效果仍需结合取景判断：

| 使用参考 | 词 |
|---|---|
| 可先尝试 | `ass focus` · `foot focus` · `hip focus` |
| 较弱，配合明确描述 | `eye focus` · `breast focus`（**单数**）· `back focus` · `hand focus` · `armpit focus` |
| 优先改用句子 | `navel focus` · `thigh focus` · `leg focus` |

想强调腿时，主要靠机位 + 占画幅句；强调脚可试 `foot focus`。
词条常见程度只是参考，不等于效果成功率。

`sharp focus` / `soft focus` / `out of focus` 描述清晰或虚焦程度，不能代替具体部位的焦点要求。

<a id="general-writing.s05.h07"></a>

#### IP 与角色名 —— **怎么把名字写对**

> **先按 [§0](#general-writing.s02) 区分细节来源：名字触发的默认外观不凭印象补写；
> 用户明确指定的服装、饰品和外观改动逐项保留。** 本节补充名字、换装与改动的写法。

写规范名，放进那个角色的角色栏，**跟在性别词后面**（`girl, archetto (arknights)`）。
独立作品名可加可不加；名字拿不准时补上有帮助，不必重复角色名括号中已有的信息。

> ✅ `girl, archetto (arknights)` ／ `girl, archetto (arknights), arknights`
> ❌ `archetto_arknights`（名字和作品名粘成一个词——不是任何词典里的写法）
> ❌ 角色名出现在主提示词（它只属于角色栏）

**拼写规范**（4.5 口径，V5 机制应同）：名字和作品名**必须完全正确拼写**（大小写不限）；
「姓氏 名字」两段式名字**中间必须空格**（可用下划线代替），且 danbooru 口径
**姓在前名在后**（`hanami saki`，不是 `saki hanami`——照剧中称呼的顺序写常常是反的）；
作品名括号推荐半角；
**皮肤 / 不同外观**写在角色名与作品名**之间的括号**里（三者间空格或下划线）；
变音符号要转音译（ō → ou）——角色/作品名处只认 ASCII 字符。
**角色名应有可核实的拼写与来源**；冷门角色是否被模型收录另行判断，名称正确也不保证能触发外观。
**知识库边界期的新角色走中间档**：名字照写（拼法无从核实就
「名字 (作品名)」空格加半角括号，**不自造下划线连写**），
补必要的已核实结构性外貌用于辨认，输出末尾说明收录不确定；不按固定数量删掉用户给定细节。发布日期不代替收录证据，不把猜测当成查询结论。

**角色 tag 用于触发常规外观与常见服装。** 用户没指定的发色、发型、袜子等，
不要凭印象补全；补错会与角色 tag 冲突。按下面的来源判断写多少：

| 细节来源 | 写法 |
|---|---|
| 用户只点名角色，沿用常规外观 | 性别词 + 规范角色名即可；需要提示场合时可加 `school uniform` / `track jacket` 等简洁引导词 |
| 用户只给笼统换装方向，如“穿泳装” | 写 `swimsuit` 等成套说法，不擅自补出领子、裙子、丝带 |
| 用户明确指定服装、饰品或外观改动 | 每项都写进角色栏，保留颜色、形制、位置、数量及指定权重；未指定部分才采用简洁成套说法 |

例如只要常规校服，可写 `girl, chihaya_anon, school uniform`，不再猜补服装部件。
如果用户明确要白色水手领、黑色百褶裙、蓝色丝带和红色发夹，则写：

> `girl, chihaya_anon, white sailor collar, black pleated skirt, blue ribbon, red hairclip`

不能把这四项缩成 `school uniform` 或 `casual clothes`。**保留用户细节与避免擅补默认设计同时成立。**
角色名只是触发方式，不保证每个细节都能准确生成。

**查证与改动**：

1. 没有明确细节时，用名字与必要的简洁引导词；不要把对默认外观的猜测写进成品。
2. `search_tags` 可核对 tag 是否存在、post 量和译名，不能单独证明角色与某属性的关系。
   有广域检索能力时可查角色档案；查证用于明确设计与构思，不意味着要把档案逐项抄进提示词。
3. **故意改设定**时，把用户要求的替换项写进角色栏；必要时可尝试 **1.3–1.5** 的权重
   压过常规设计（如 `1.4::swimsuit::`），不保证一定覆盖成功。**用户给了权重就原样保留**，
   不为套参考值而改数；多个明确细节仍逐项保留。输出末尾一行注明改了什么（[改动说明](conventions.md#field-contract)）。

外观之外的**职能、归属、相对位置**也要按本题写清；不靠角色名代替动作与关系，见 [§4.2](#general-writing.s06.h02)。

<a id="general-writing.s05.h08"></a>

#### 版式与背景形态
版式：`comic` · `4koma` · `2koma` · `3koma` · `1koma` · `5koma` ·
`multiple 4koma` · `square 4koma` · `multiple views` · `reference sheet` ·
`chibi` · `chibi only` · `chibi inset` · `sticker`
漫画构件：`speech bubble` · `thought bubble` · `emphasis lines` · `sound effects` · `halftone`

背景按已定目标分别表达复杂度、虚实、颜色与透明性：`simple background` / `blurry background` / `white background` /
`detailed background` / `transparent background` / `dark background`。
这些词并非整组互斥；简洁与白色、复杂细节与暗色可以表达不同维度。只处理同一主体或区域上实际矛盾的要求，保留兼容属性及其归属；这种语义判断不保证成图效果。

`depth of field` / `bokeh` 用来表达景深虚化。需要前后景都清晰的大场景，检查这些词是否与远景细节要求冲突；局部虚化时写清模糊的是哪一层。

<a id="general-writing.s05.h09"></a>

#### 按主体与区域检查语义冲突

先判断词语各自描述谁、哪片区域及什么属性，再检查是否矛盾。下表用于核对表达，不按同组词语的数量删词。

| 组 | 取值 | 适用关系 |
|---|---|---|
| **视线方向** | `looking at viewer` · `looking to the side` · `looking up` · `looking down` · `looking away` · `looking at another` | `looking back`（回头）和 `closed eyes`（闭眼）**不是方向**，可以跟方向叠。**多角色互看**＝只写 `looking at another` **这一个**。❌ `looking up, looking down, looking at another`（想把两人视角都编码 → 全都摇摆）✅ `looking at another` + 句子 "the standing girl looks down at the squatting one"（高低差进句子，或角色栏前缀 `looking at target`，[§4.9](#general-writing.s06.h13)） |
| **取景距离** | `close-up` · `portrait` · `upper body` · `cowboy shot` · `full body` | `wide shot` 说的是镜头退多远，可以跟 `full body` 叠 |
| **背景形态** | `simple background` · `blurry background` · `white background` · `detailed background` · `transparent background` · `dark background` | 复杂度、虚实、底色和透明性分别判断；同一区域的真实冲突才需处理，兼容维度及不同区域的属性可以并存 |
| **体位** | `sitting` · `standing` · `lying` · `kneeling` · `squatting` | **多角色例外**——一人站一人蹲时两个都要写，靠句子说清谁是谁 |
| **水平机位** | `from side` · `from behind` · `straight on` | 垂直机位 `from below` / `from above`（两者也互斥）**可以跟水平机位叠一个**：`from below, from side` 合法；`from behind, from side` 不合法 |
| **版式** | `comic` · `4koma` · `multiple views` · `reference sheet` · `sticker` | `comic` 可与格数词（`4koma` 等）叠；格数排布 tag 说不了的用句子写，**不自造 `vertical` 这类 tag** |

**检查同一主体、同一画面里的语义冲突**。多人或分格可能同时出现不同体位、视线和距离，
要先看清各自归属，不能把共现一概算成错误。
`close up` 和 `close-up` 是同一个词的两种写法，挑一个即可。

---

<a id="general-writing.s05.h10"></a>

#### V5 专有开关（旧文档恢复，2026-08-26）

这些是功能开关，只能词组化：

- **复杂度**：`low/medium/high/ultra complexity`——**功能开关，不是质量尾，默认不加**。
  加不加看开篇「V5 开关」那三条：画师串合不合、画面内容配不配、
  它有画面固化倾向（实测有负权重后画面反而变好的例子）
- **透明**：`transparent background`（背景透明）/ `alpha transparency`（画面内物体在输出文件里真的透空，
  走 alpha 通道，如魔法特效、火焰、伞，多配透明背景做素材）/ `has alpha`（较抽象）。不稳定时 `2.1::transparent background::`。
  完整画面里画透明的伞写 `transparent umbrella`，不用 `alpha transparency`
- **`depthness`**：给阴影增加纵深
- **年代倾向**：`meta:novel era`（偏旧）/ `meta:golden era`（偏新）
- **视觉小说风**：`visual novel art` / `visual novel bg` / `visual novel cg` /
  `visual novel sprite` / `visual novel chibi`
- **`attractive male`**
- **`res_mult:Nx`**：分辨率倍数。官方示例用过 1.5x / 3x / 10x。
  已有实际提示词样例，但缺少效果对照；按给定语法使用，不因低采用率判断无效。

<a id="general-writing.s06"></a>

### 用句子补充空间、归属与动作关系

下文引文的外层引号只是标示例句，实际输出叙事句时不带外层引号；要画进图的文字另按文字渲染规则处理。

<a id="general-writing.s06.h01"></a>

#### 空间关系与归属
谁在谁前面、谁离镜头更近、道具属于谁。**多人防串味的主要手段。**
> "Character 1 stands at the left side of the room beneath a red safelight.
> Character 2 stands farther back on the right side beside an enlarger.
> The umbrella belongs only to Character 2."

> **角色栏的编号顺序不一定由你定。** 用户在自己的角色词库里存过的角色，
> 只要名字出现在需求里，前端就按**名字在需求文本里首次出现的先后**
> 直接指派 `Character 1 / 2 / 3…`，并把那个角色的外观串塞进对应格。
> 这种时候你收到的上下文里会有「【用户点名的角色】Character 1 = 某某：…」，
> **照它的编号写，不要自己重排**。没有这段的时候编号才由你定。

**编号必须跟角色栏的名字一模一样**：角色栏叫 `Character 1` / `Character 2`，
句子里就写 `Character 1` / `Character 2`。**不要写 `Character A / B`**——
那样句子与角色栏使用了两套称呼，无法按编号核对归属。
编号一致是字段对应要求，实际生成的归属仍可能出错。

<a id="general-writing.s06.h02"></a>

#### 职能与归属：按本题资料写清谁做什么

[§3.7](#general-writing.s05.h07) 讲的是「默认外观不凭印象补写，用户明确细节逐项保留」。这一条处理外观之外的内容：

| 角色 tag **带**的 | 角色 tag **不带**的 |
|---|---|
| 发色 · 发型 · 眼睛 · 体型 · 常规服装 | **群体里的职能**（谁弹贝斯、谁是队长） |
| | **归属关系**（东西是谁的、谁是谁的姐姐） |
| | **相对位置**（谁站中间、谁最高） |

**右列的关系需要在主提示词中明确表达。** 角色名不能代替本题中的乐器、持物与站位；
写错归属会给出相互冲突的要求，也不能指望角色名自动修正。

**凭印象分配职能的实测**：2026-08-25 的 MyGO 五人图，`nagasaki_soyo` 写成弹电吉他、
`kaname_raana` 写成弹贝斯——**两人写反**，出图就是五个人拿着不对的乐器。
该次记录里外观归属正确，乐器分配与角色资料不符。

<a id="general-writing.s06.h03"></a>

##### 依照实际资料与工具判断归属

只有标签查询能力时，标签名、翻译与使用量不能证明角色职能或人物关系。有广域检索能力且本次需要查证时，可以核对角色档案；没有资料就区分不确定内容与用户已经明确给定的归属。工具能力与调用限制由当前环境决定，不假设所有运行环境只有一种接口或固定调用步数。

用户明确谁做什么时忠实表达，不能因人数较多自动省略。未指定又不确定时，采用不伪造归属的表达，或在确实影响当前任务时指出需要确认的具体关系。查不到标签也不意味着不能用自然语言表达已经确定的动作。

<a id="general-writing.s06.h04"></a>

##### 查证服务当前交付

能完成的内容先完成；不以“准备查一下”代替结果。必要查询依据真实工具与本次问题，不能声称已查到未读取的资料。原稿已经确定的事实直接沿用，未确定的关系不靠猜测补成已知设定。

<a id="general-writing.s06.h05"></a>

##### 归属未确定时保留不确定性

> ✅ "Each member stands at her own instrument position."
> ❌ "Character 3 plays bass while Character 4 plays electric guitar."

未查明乐器归属时，可先表达已经确定的演出场合（`band performance, on stage, live house`），
不把猜测写成具体分配。省略分配也不保证模型自动补对；旧稿关于模型依共现完成分配的解释
只是推理，**没有单独出图验证过**。若特定归属是当前任务的必要条件，仍需补足资料。

**已由用户或资料确定的归属直接写清**：
> "The microphone belongs only to Character 1."

归属句让读者能核对每件物品属于谁；已定内容应完整表达。

<a id="general-writing.s06.h06"></a>

##### 这一条不只对版权角色

多人共用一件道具时（一把伞、一份便当、一只猫），归属句本来就是防串味的主要手段（[§4.1](#general-writing.s06.h01)）。
版权角色可能另有可查证资料；**原创角色的归属按用户或已定方案表达**，
把持物者、接触对象与位置写进句子，避免由模型自行补齐关键关系。

<a id="general-writing.s06.h07"></a>

#### 透视关系（**不含机位高低**）
表达焦距感与前后压缩时，将近处和远处放在同一句中对比，说明哪部分更大、哪部分向远处缩小。
> "One foot is very close to the lens while the rest of her body rapidly recedes into depth."

<a id="general-writing.s06.h08"></a>

#### 占画幅多少
取景词能给出大致范围；需要指定某部分占据画面的哪一片时，用句子补出大小与位置。
> `from below, white thighhighs, uneven legwear.`
> "Her legs dominate the lower half of the frame, and one thighhigh has slipped down
> to bunch just below the knee."

<a id="general-writing.s06.h09"></a>

#### 运动的「进行中」状态
tag 只能说 `running`，说不出停在哪一瞬、衣物头发怎么响应。
> "Her body is caught halfway through a natural running motion. Her clothing and hair
> react to the movement and wind rather than hanging motionless."

例句以 "rather than hanging motionless" 排除静止状态；使用时仍应明确衣物和头发随动作朝哪里扬起，而非只写“不要僵硬”。

<a id="general-writing.s06.h10"></a>

#### 光影叙事
说明光从哪里来、落在哪片表面，以及投影朝哪边延伸。已定画面有第二光源时，再写它照亮的区域。
> "The red safelight dominates the room, but a thin strip of neutral light enters beneath
> the closed door and produces a second subtle lighting direction."

光线方向句在既有对照里出现过反向结果；可配合对应方向 tag 表达光位，仍需核对实际结果。

<a id="general-writing.s06.h11"></a>

#### 场景物件的整体性
列出场景必须出现的物件，再说明它们应各自可辨。需要明确空间关系时，补出物件所在的桌面、架层或前后位置；下例演示清单与整体要求的组合。
> "The darkroom contains several separate chemical trays, bottles, measuring cylinders,
> clips, hanging prints, an enlarger, a timer, shelves and a small sink.
> The equipment should remain recognizable and spatially coherent rather than dissolving
> into abstract machinery."

<a id="general-writing.s06.h12"></a>

#### 句法约定
- 主语：单人 `The character`。多人**两分工**——**归属 / 位置句**用
  `Character 1 / 2 / 3`（跟角色栏同名，[§4.1](#general-writing.s06.h01)）；**交互动作句**（谁对谁做什么）用
  **外观短语**指认（"the girl in the beige coat hands the cup to the girl with
  headphones"）——旧对照中编号的外观对应成功，但职能分配出现错误（[§4.9](#general-writing.s06.h13) 末尾的实测）。
  只复用辨认必需的简短锚点，不把角色栏整套外观抄进句子，也不擅造辨认特征。
  **两种句子都不用角色真名当主语**（真名属于角色栏）
- 时态：现在时或现在进行时
- 一段一个职能，段间空行
- **物件先列词组，关系再写句子**：持握物、身体支撑物和构图所依赖的实体都按[完整模板](#general-writing.s02)进入前部物件清单，随后说明接触、位置与遮挡。
- **叙事段不要整段包在引号里**。引号在提示词里的既定语义是「要画进图里的文字」
  （画中文字的写法就是引号＋载体，见 [§4](#general-writing.s06) 分格配套条与排查表）；把叙事句包进引号，
  是在冒模型把整句当画面文字渲染的风险。
  句子直接写。

---

<a id="general-writing.s06.h13"></a>

#### 多人交互：先定施受，再找锚点

当已定画面包含互动时，除人物与场合，还要表达**谁对谁做什么**。
「三个人在野餐」只给出人数与场合；若方案还要求递杯或按住另一人的手，应继续写出对应动作。各自活动或旁观也可以是完整的多人画面。

<a id="general-writing.s06.h14"></a>

##### 表达已确定的参与关系

从当前画面提取谁发起、谁接受、谁旁观以及谁并未出场。只写与已定内容相符的关系，不给没有动作的角色补任务，也不强制所有人物参与互动。若缺失归属导致无法忠实表达，指出具体歧义；不能用修词的名义改人物关系。

<a id="general-writing.s06.h15"></a>

##### 接触点必须有主人

每一个接触、每一件共用的道具，都要说清**是谁的手、碰到谁的哪里**：

> ✅ "Character 1 presses her palm down on the back of Character 2's hand."
> ❌ "Their hands are touching."（未交代哪只手与哪个部位接触）

同一小块画面里出现多只手时，写清各自从哪侧伸入、前臂连向哪位人物，
以及手掌压在手背上还是手指握住杯沿。原有的**「每只手都清楚地连在自己主人身上」**
可作整体要求，具体入画方向和接触位置仍需写明。

<a id="general-writing.s06.h16"></a>

##### 为已定动作选择词组与关系句

将已定动作拆成可直接命名的状态与需要说明的关系：张手、持杯可找对应 tag；
手从哪边伸来、杯沿离指尖多远，用句子表达。查询用于核对现成词义，
已经能准确描述的关系无需等待一个专用 tag。

实测一次（三人递接场景）：

| 构思里的那一下 | 找到的锚点 | 结果 |
|---|---|---|
| 手是张开伸出去的 | `outstretched hand` | ✅ 该次张手状态清楚 |
| 手里有个杯子 | `holding cup` | ✅ |
| 一个人压着另一个人的手 | `hand on another's hand` | ⚠️ 要配句子 |
| 「伸到一半没接住」 | 没有 tag，这是关系 | → 句子 |

**词典写法不能只靠语感猜。** 找不到现成 tag 时用句子把动作说清，
不把直觉造出的短语当作已收录词。

> 自然语言不要求每个动作都有对应 tag。找不到规范词时，直接说明身体部位、接触对象、
> 方向与当前状态；词义未核实的短语不标作已收录标签。

<a id="general-writing.s06.h17"></a>

##### 在角色栏用前缀标明施受方向

V5 认三个方向前缀，**写在角色栏里**（不是主提示词）：

```
source#{动作}   这个角色在发起
target#{动作}   这个角色在承受
mutual#{动作}   两人互相做同一个动作
```

只有这三个，前缀表示**动作方向**，不是角色身份 ——
`female#hug` `char1#hug` `left#hug` 都无效。

需要区分动作和接触部位时，**各写一条前缀**，视线可用 `looking at target`：

```
Character 1: <角色名>, source#teasing, source#touching face, smirk, looking at target
Character 2: <角色名>, target#teased,  target#face touched, blush, embarrassed
```

（这里的 `smirk` / `blush` 是 [§0.1](#general-writing.s02.h02) 的表情词例外：跟着前缀标施受气质
才允许进角色栏；没挂前缀时，表情回主提示词。）

**前缀按需使用**：它标明谁发起、谁接受；句子继续说明手从哪边伸到哪里、碰到什么、动作完成到哪一步。分工见 [§2](#general-writing.s04)：

| 前缀（词组笔法） | 句子笔法 |
|---|---|
| **谁是施加方** —— 离散事实 | **这个动作长什么样、停在哪一瞬** —— 关系 |
| `source#pinning down` | "her fingertips have only just touched the rim and have not closed around it yet" |

**什么时候值得加前缀**：「谁对谁」本身容易错的时候——三人以上、接触密集、
或者两人动作互相对称（都伸着手，谁递谁接看不出来）。

<a id="general-writing.s06.h18"></a>

##### 前缀的使用情形

**① `target#` 只绑方向，不绑「气势」。** 承受方可以是画面上更主动的那个：

> Character 1: `source#piggyback, looking down, tired, closed mouth` ← 背人的，闷头走
> Character 2: `target#piggyback, pointing, open mouth, excited` ← 被背的，指着前方在说话

实测出来正是这样——背的人低头闭嘴，被背的人手臂伸直在指。
该例中前缀表达背人与被背的方向，表情和动作词补出各自状态；不据这次结果保证所有组合互不影响。

**② 同一个角色栏里可以同时挂 `target#` 和 `source#`**；下列旧样本同时呈现了两个方向。
A→B→C 的链式交互就是这么写的：

> Character 1: `source#covering another's eyes`
> Character 2: `target#eyes covered, source#headpat`　← 一个人两个方向
> Character 3: `target#headpat`

出图：黑发从背后捂住粉发的眼睛，粉发眼睛被捂着还在笑、**同时她自己的手按在棕发头上**。

**③ `mutual#` 表达双方互做同一动作**；下例尝试额头相抵与互看：

> Character 1 / Character 2 都写 `mutual#forehead-to-forehead, mutual#eye contact`

4.5 教程技巧（V5 待验证）：mutual 相同动作时，把 `imitate pose` 单独写进
两个角色栏更精准。

<a id="general-writing.s06.h19"></a>

##### cosplay 玩法（4.5 实测口径，V5 待验证）

`source#` = cos 者，保留自己的身型、脸型、瞳孔（有时头发）；
`target#` = 被 cos 对象，其**服饰发型转移到施动方**身上。
技巧：两个角色的 Custom position **定到同一点**，避免生成两个人；
主提示词必须点名 `1girl` / `1boy` / `1character`。

<a id="general-writing.s06.h20"></a>

##### 第三人的动作遗漏时，核对其词组与前缀

既有三人小样本中，主交互之外第三人的取食动作没有按句子执行；
改写其角色栏动作后才出现取食。该记录支持把动作归属写得更明确，
没有证明第三人只能用前缀控制，也没有测定模型注意力的原因。

| 给第三人写的 | 结果 |
|---|---|
| 句子写「趁两人较劲时把西瓜端走」，角色栏只有 `holding food` | ❌ 变成纯旁观 |
| 同一件事写成 `source#taking food, source#food theft, smug` | ✅ **真的拿到手正在吃** |
| 只要「在场且不参与」（`crossed arms, looking at another`） | ✅ 成 |

该样本的 `source#taking food` 没有对应 target 角色，仍出现了取食动作。
若第三人的已定动作遗漏，可尝试在其角色栏用对应前缀明确发起者，再在主串补出
手伸向哪件食物、食物离开谁的手或桌面。第三人本来只旁观时，保留旁观状态。

<a id="general-writing.s06.h21"></a>

##### 相对位置与占画幅：关系句及 Custom position 的旧对照

同一组旧对照中，「谁离镜头近、谁占画幅大、谁在远处缩小」用文字尝试两次未落实，
改用 NAI 的 **Character Prompts → Position → Custom** 后一次呈现了预期层次。
以下保留该次设置经验，不作为文字无效或控件必定成功的结论：

- 该次把点位放低的人物更近、更大，放高的人物更远、更小；可据此尝试安排前后层次，但不把 **Y 坐标** 当作独立的深度参数
- 用法：**控件定层次，句子描述层次**，两个一起上——
  句子写 "Character 1 is closest to the camera, cropped at the waist by the frame
  edge… Character 3 is far up the street, clearly smaller in the frame"，
  点位拖成 左下 / 中 / 右上
- 这用于落实已确定的前中后景，不替用户重新设计构图；文字保留意图，必要时另给控件建议
- 补三条（N5 教程口径）：点位**编号 = 角色栏顺序编号**；AI 会按点位**重新设计
  构图和机位（viewer 角度）**；角色点位过近时需留意人物重叠与归属错误
  （4.5「周围 8 格不放人」的精神继承）

**普通插画和多人图的附注不主动给位置**，角色位置由用户自己在 Character Positions 画布上定（[字段职责](conventions.md#field-contract)）；
本节用来把层次写进句子。用户问到怎么摆时，再按上面的方法给建议，例如
「角色位置：在角色提示词区把位置从 AI's Choice 改成 Custom，点 Character Positions 打开画布，这样放：Character 1 左下、Character 2 中、Character 3 右上」。
此为文本设置建议，不代表已经操作；实际能否精确控制层次仍需按当前模型与结果判断。

<a id="general-writing.s06.h22"></a>

##### `Character N` 的对应要求与旧样本局限

2026-08-26 实测，同一张图里：

| | 结果 |
|---|---|
| 外观归属（谁穿什么、谁什么发色） | **准** —— 三个人零串色 |
| 职能归属（谁递给谁）**写在句子里** | **错** —— 写的是 1 递给 2，出来是 1 递给 3 |
| 同一件事**改用 `source#`/`target#` 写在角色栏** | **对** —— 施受完全正确 |
| 相对位置 / 占画幅 | 该组文字尝试未落实，**Custom position 控件一次成功**（见上一节） |
| 人数 | **多出一个** —— 写 `3girls`，出了 4 个人 |

这些旧样本显示动作与归属可能分离；它们不能保证新任务的动作或身份必然准确。
遇到同类错配时，可在本次范围内考虑：

- 若用户愿意重设计，可以建议让交互只发生在两个人之间、第三人旁观，以减少错配；忠实转换与局改不能擅自采取这个变化
- 用**外观**而不是编号来指认：写 "the girl in the beige coat hands the cup to
  the girl with headphones" 用于补足 "Character 1 hands it to Character 3" 中只有编号的指认
  ——只复用辨认必需的简短锚点，完整外观清单仍在角色栏（[§0](#general-writing.s02)、[§4.8](#general-writing.s06.h12)）
- 人数词不保证成图人数准确；多人 UC 中的 `extra characters` 按下一节删除，不能用它区分指定人物与误增人物

<a id="general-writing.s06.h23"></a>

##### ⚠️ 单人的 UC 预设不能直接用在多人图上

某些单人 UC 模板里有 `2::little dolls, extra characters, ..., ::`——
**那是给 solo 图写的**。三个人的图带着它，权重 2 的「多余角色」会跟你的 `3girls` 打架。
多人图只从这一段里删去 `extra characters`，同段其他项保留，按[§6](conventions.md#shared-quality)的冲突删除规则处理。基础排除串里本来没有这段，别从单人 UC 模板抄进来。


<a id="general-writing.s06.h24"></a>

#### 分格布局与联系装置

本节表达已经确定的表情集合、设定展示及分格构图。漫画故事导出统一用“字段模板与先后顺序”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s02`），不以本节替代逐格框。布局可分三步检查：

**① 第一句话声明版式**——几格、怎么排、有没有边框，后面所有内容服从它：

> "A four-panel manga-style scene …"（顺序四格）
> "A 3x3 grid of nine headshot portraits …"（九宫格）
> "two-panel comic, one large main illustration and one small rectangular inset
> in the lower-right corner, white panel borders"（主图 + 插入格示例）

版式声明基本靠**句子**；tag 只有 `comic` / `4koma` / `multiple views` / `inset`
这几个粗粒度的（见 [§3.8](#general-writing.s05.h08)），格数和排布 tag 说不了。

**② 逐格一条，每条带方位锚**——bullet 或编号都行，方位与对应画格一致：

> · Top-left (Joy): bright yellow background, wide smile, happy squinted eyes.
> · Bottom-center (Drooling daze): pale pink background, blank stare …
>
> 1. Front half-body portrait (center-left): …
> 3. Back view (bottom-right): …

每格自己的内容自己一条（表情 / 动作 / 底色），**格与格不共享句子**。

**③ 写清已定的联系装置。** 主锚图、主次关系、贯穿色彩或共同载体来自当前设计；没有指定时不为了模板补一个新装置。确需创作这种关系可接 `nai5-illustration-composition`，并非本节的必读步骤。

**配套的几条**：

- 同一角色跨格使用一致的身份事实；当前漫画按“从现稿提取身份、状态和可见子集”（`nai5-comic-writing`：`references/comics.md#writing-comic-state`）写入每次出场框，不把全页压回一个共享外观栏。普通非叙事展示若使用共享外观方式，仍须明确各视图归属。
- **画风上做减法**：多格信息密集时，减少单格不必要的材质和装饰细节，保住轮廓与动作。
- 画中文字照老规矩：引号 + 载体（"a small paper tag reads「…」"）
- 已定版式采用画中实物时，表达清楚画框与实际照片/纸页等物件的关系；不自动添加相册或线索板。

<a id="general-writing.s07"></a>

### 三种成品形态

三种形态就是笔法在块上的不同分配，都成立：

| 形态 | 分配 | 适合 |
|---|---|---|
| **A 词组块 + 句子块** | 主体锚/镜头/姿势用词组，关系/场景/光影用句子 | **默认**，便于分别核对对象属性与关系 |
| **B 词组织进句子** | 混在同一行逗号并列 | 内容零散、有具体 UI/文字要求时 |
| **C 纯句子** | 全部自然语言 | 画面是完整场景叙事，或写风格调性 |

官方各有实例：A 见示例 #1（空行分十段），B 见 #4，C 见 #2 和 #5。

<a id="general-writing.s09"></a>

### 参数（仅在用户询问或排查时给，不随 prompt 输出）

未指定时用这组功能默认参考；用户明示参数、运行环境限制或实际启用的写法另有要求时，
按其调整。不要静默改掉已有具体参数；偏离时简要说明理由。

| 参数 | 默认参考 |
|---|---|
| Steps | 28 |
| Sampler | `k_euler_ancestral` |
| Noise Schedule | `karras` |
| Guidance | 5.0–7.0，按具体任务选定 |
| Prompt Guidance Rescale | 0.0；作为默认参考，不称官方普遍规则 |
| 尺寸 | normal 档；随竖 / 横 / 方构图选 |

常用尺寸参考：竖 832×1216；方 1024×1024；横 1216×832。
明确要更大尺寸时可考虑 1024×1536 / 1536×1024，并检查运行环境限制。
构图说明只说竖 / 横 / 超宽 / 方；仅在询问参数时给像素。

PGR 可用于高 Guidance 时的纠偏，日常先不动；Variety+ 可作为增加变化的选项，
不以随意降低 Guidance 代替。计费、免费门槛和剩余额度以实际界面为准。

<a id="general-writing.s10"></a>

### 排查

先核对对应原稿、已有画面意图与实际反馈。缺少对应图像或记录时，下表只作为条件式检查与可尝试的表达，不据症状断定原因或承诺修复效果。保持已定内容；涉及改变光色、场景或机位的建议，按当前用户允许的范围处理。

| 症状 | 处理 |
|---|---|
| **姿势画糊、多出一条腿** | 先查原稿姿势、肢体归属与表达冲突。若已定姿势被长句写散，可尝试对应的姿势 tag（`sitting, leg up, arm support, head rest`），关系仍用句子补清；单凭多腿现象不能认定是句子所致 |
| **机位压不低** | 原稿确实要求低机位时，检查视角词是否遗漏或与其他取景要求冲突，可尝试 `from below`；保留已定姿势与裁切，不因镜头词共现就直接删掉其中要求 |
| **袜子/手套形制或数量不对** | 先查中文释义。`loose socks` 是堆堆袜、`single thighhigh` 是只穿一只，都会静默换衣服。要「一只拉起一只滑下」**用句子写状态**（`uneven legwear` 单独写未稳定推动不对称） |
| **整张图变成一片纹理／泥浆** | 画师名或 tag **以数字结尾**又紧跟 `::`——`na_tarapisu153::` 会被解析成权重 **153**，后续内容受到异常高权重影响。写成 `na_tarapisu153, ::`——**加逗号比加空格更安全**，哪怕多打一个变成 `2::artist:na_tarapisu153, ::,` 也比 `na_tarapisu153 ::` 稳 |
| tag 被忽略 | 提权重 / 移到前部 / 拆成独立 tag / 改用整句 |
| 画面平、缺层次 | 先查已定前后关系、主光方向、投影形状与色彩层次是否表达清楚，补足遗漏的既有意图；新设主光或主题色属于内容调整，按获准范围提出具体建议 |
| 色调不符 | 对照已定配色与实际结果，检查颜色归属、遗漏和冲突；可尝试将目标色彩词前移。只有当前意图确实要求有限配色时才考虑 `limited palette`，不另定主题色 |
| 逆光面部过暗 | 先核对原稿要求的逆光与面部明暗。若用户允许减弱逆光或补面部光，可考虑 `-2::backlighting::` 或 `front lighting` / `face lighting`；它们会改变光照表达，不作为默认修复 |
| 角色白背景虚空 | 先确认原稿是否本就要求简洁白底。若既定场景未被表达，可补清该场景，并检查是否有冲突词；`-1::simple background::` 仅作为目标确需排除简洁背景时的尝试，不另造场景 |
| 多角色串味 | 核对角色栏与关系句的指认、持物及接触归属；实际使用定位时核对编号；检查人数 tag 位置 |
| 动作僵硬 | 用姿势 tag 表达已定体位，句子补出动作停在哪一瞬、手脚的接触对象及衣物头发的响应 |
| 场景糊成抽象物 | 清单后补整体性要求句 |
| 透视不对 | 机位用 tag，前后压缩用对比句式 |
| 想强调腿但出不来 | 先核对原稿的机位、裁切与腿部占画幅是否表达清楚。`thighhighs, bare legs` 描述服饰/裸露，不能代替焦点关系；`leg focus` 或占画幅句可作为表达尝试。原方案含低机位时才用 `from below`，需要强调脚时才考虑 `foot focus`；不为突出腿默认更换镜头 |
| 文字不出/出错 | 引号包裹 + 句子写清**载体**和位置；需要文字时去掉质量尾及预设附加的 `no text`；多格逐格绑定文字；使用引号自动处理时别另写 `Text:` 块 |
| 画面缺少辨识点 | 先核对现稿意图与实际反馈，检查必要特征是否遗漏、词义是否准确、归属和关系是否表达清楚；需要改变内容或构图时提出具体建议，仅在获准范围内修改，或接 `nai5-illustration-composition` 处理，不在修词时擅自另定画面 |
| 固定物体始终画不对 | 对照现稿和实际结果，先核对物体名称、词义、结构、归属及表达冲突；单凭画错不能判定模型知识盲区。先修获准范围内的表达，确需更换物体或构图时说明具体建议，获准后修改或接构图技能，不直接换掉已定方案 |

<a id="general-writing.s11"></a>

### 普通完整插画写完对照

普通完整插画交付前检查下表。漫画另核对“看实图后按症状修正”（`nai5-comic-writing`：`references/comics.md#comic-adapter.s07`），服装片段另核对“服装交付检查”（`nai5-costume-writing`：`references/costume.md#costume-writing.s09`）；共同事实、字段、文字和实际预设仍统一适用。

| 检查 | 对照位置 |
|---|---|
| 姿势、机位高低用词组；空间关系、动作瞬间用句子 | [§3.3](#general-writing.s05.h03)–3.4、[§4](#general-writing.s06) |
| 普通多角色分栏；主串不复制完整外观清单，交互句只复用辨认必需的简短锚点；漫画按逐格框 | [§0](#general-writing.s02)、[§4.8](#general-writing.s06.h12)；单人简单外貌可不分栏 |
| 普通插画角色栏以不带数字的 `girl` / `boy` / `other` 开头；漫画用格位与镜头起句 | [§0](#general-writing.s02) 角色类型表 |
| 版权角色用规范名字，独立作品名可选；不凭印象补默认外观，用户指定服装 / 饰品 / 外观改动逐项保留 | [§0](#general-writing.s02)、[§3.7](#general-writing.s05.h07) |
| 原创角色给定样貌锚点完整，没为压短而删改 | [§0](#general-writing.s02) 角色类型表 |
| 人数 tag 在最前且只写一次，与对应领域的实际生成单元及人物身份一致 | [§3.1](#general-writing.s05.h01) |
| 表情默认在主串；施受前缀例外按需使用 | [§0.1](#general-writing.s02.h02)、[§4.9](#general-writing.s06.h13) |
| 服装状态词已核语义，不把一种衣服误作一种穿法 | [§3.5](#general-writing.s05.h05) |
| 视线、距离、背景形态按同一主体 / 同一画面检查冲突 | [§3.9](#general-writing.s05.h09)；多人和分格先判归属 |
| 多人归属清楚，没有凭印象分配职能或乐器 | [§4.1](#general-writing.s06.h01)–4.2 |
| 普通插画、多人图的附注没有主动给角色位置（由用户自己定，问到才给）；层次写进了句子 | [相对位置](#general-writing.s06.h21)、[字段职责](conventions.md#field-contract) |
| 质量词只有一组，放所有句子之后、不包 `<quality>` 块 | [§6](conventions.md#shared-quality) |
| 无字用 `very aesthetic, masterpiece, no text`；有字去掉 `no text` 并检查预设 | [§6](conventions.md#shared-quality) |
| 要画的文字有引号与载体；漫画台词逐格绑定，静默格省略文字指令 | 开篇「文字渲染」「漫画」 |
| UC 沿用用户的或基础串，只删与本图冲突的项；本图不要的写成主串最后的负权重，不进 UC；多人删去 `extra characters` | [§6](conventions.md#shared-quality) |
| 用户逐字原串（含空格、标点、年份）和指定权重原样保留；未拿通用化当作删细节的理由 | [§0](#general-writing.s02)、[§3.7](#general-writing.s05.h07) |
| 参数仅在询问或排查时给，已有具体值未被静默修改 | [§7](#general-writing.s09) |


<a id="writing-multiple-example"></a>

## 多个完整方案

用户要求多个完整提示词时，各方案有自己的主串、必要角色栏和 UC（UC 按[§6](conventions.md#shared-quality)沿用并去冲突）；数量按请求，不共用字段或写“同上”。只要点子或构图时不使用完整字段格式。附注以实际需要为限。
