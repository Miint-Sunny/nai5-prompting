<a id="writing-illustration"></a>
<a id="ordinary-identity"></a>
<a id="general-writing.s02"></a>

# 普通插画与多人交互写法

本文件用于普通单幅插画（单人、多人、局部动作场景、多视图设定页）的提示词组装、角色栏分工、多人方向前缀与成图排错。基础语法、质量词与 UC 见 [核心语法与字段契约](writing-core.md)。

---

## 一、普通插画完整模板与行序

普通完整插画按 `Base Prompt:`、`Character 1:`、（多人依次 `Character 2:`……）、（用户要求时 `Undesired Content:`）分块交付。**每行末尾均以英文半角逗号 `,` 结尾（含英文句子末尾）。**

### 1. 单人完整插画模板

Base Prompt:

```text
1girl, solo, <持握物、身体支撑物及决定前景遮挡或取景框的实体词组>,
<姿势、动作、表情、视线词组>, <取景范围与机位高低/角度词组>, <场景、时段、光线与氛围词组>,
<自然语言关系句：用 The character 作主语，说明此刻姿态、哪只手接触或承托何处、前后遮挡与光线落点>,
<本次确需的技法词；不需要时省略本行>,
<本图单独排除项的负权重行，如 -1::hat::；无排除项时省略本行>,
```

Character 1:

```text
<girl / boy / other>, <角色名或本次沿用的外貌锚点（发型、发色、瞳色、物种特征等）>,
<本次服装与配饰；若为仅写规范名的默认装束版权角色则省略第二行>,
```

### 2. 多人（2 人及以上）完整插画模板（含 v1.2.7 互动前缀规则）

**两个人及以上时，写法有三项关键变化**：
1. **主串前两行不写任何人物的动作、姿势、表情和视线词**（避免 `1girl, 1boy, sitting, standing, smile` 混在一起导致模型张冠李戴）。
2. **主串英文句子从简（只写 1–2 句）**：先写从观者视角看**谁在左、谁在右**，再写**谁对谁在做什么**（用户明确给定的接触、持物归属与分工照写；用户未指定的细碎手部支撑不铺开长篇描写）。句子中用左/右位置或简短外观锚点配合中性主语指代人物（如 `The character on the left`、`The woman in the beige coat`），**绝不用 `Character 1 / 2`、角色真名或 `The girl` 作句子主语**。
3. **主串末尾空一行，按人逐行写 `Character N:`**：从观者视角看**最左边的人是 `Character 1`**，依次向右编号（与下方角色栏编号严格一致；若上下文已由用户工具预指派 `Character 1 = 某某`，则照预指派编号写）。每行冒号后先写性别词（`girl` / `boy` / `other`），再写该人物自己的动作、姿势、表情与视线。

Base Prompt:

```text
2girls, <共用或决定画面的关键物件词组>,
<取景范围与机位词组>, <场景、时段、光线词组>,
<1–2 句简短英文：交代谁在左谁在右、谁对谁做什么，以及必要的持物归属或文字载体>,
<本图单独排除项的负权重行；没有时省略>,

Character 1: <girl / boy / other>, <最左侧人物的动作与姿势词；有互动时加 source# / target# / mutual#>, <表情词>, <视线词>,
Character 2: <girl / boy / other>, <右侧人物的动作与姿势词；有互动时加对应前缀>, <表情词>, <视线词>,
```

Character 1:

```text
<girl / boy / other>, <最左侧人物的角色名或外貌锚点>,
<最左侧人物的服装与配饰>,
```

Character 2:

```text
<girl / boy / other>, <右侧人物的角色名或外貌锚点>,
<右侧人物的服装与配饰>,
```

<a id="partial-base-prompt"></a>

### 3. 局部请求：只要动作与场景（不写角色栏）

当用户自己已有固定的角色栏设定，明确要求**「只要动作和场景」「不用写角色栏／不用写外貌服装」**时：
- **只输出 `Base Prompt:` 一个代码块**，不输出 `Character 1:`。
- 若用户点明了物种或局部体态特征（如「适合慵懒兔娘的侧躺野餐提示词」），可在主串动作与关系句中自然写出与姿态结合的动作特征（如 `drooping rabbit ears`、`her long rabbit ears drape loosely over her shoulder`），但**不替用户锁死发色、瞳色、发型或具体衣服**，方便用户直接搭配自己的角色栏使用。

---

<a id="general-writing.s06.h13"></a>
<a id="general-writing.s06.h17"></a>

## 二、多人方向前缀规则（`source#` / `target#` / `mutual#`）

NovelAI V5 识别以下三个动作方向前缀（**写在主串末尾各人那行 `Character N:` 或分开写进角色栏最后一行都会生效**；前缀只表方向，绝不能自造 `female#hug`、`char1#hug` 或 `left#hug`）：

- `source#<动作tag>`：动作发起方（如 `source#hug`、`source#hand on another's face`）
- `target#<动作tag>`：动作承受方，**必须使用与发起方完全相同的动作词**（如 `target#hug`、`target#hand on another's face`）
- `mutual#<动作tag>`：双方互相做或共同完成的动作（如 `mutual#holding hands`、对视 `mutual#eye contact`、额头相抵 `mutual#forehead-to-forehead`）

### 核心判据（v1.2.7 口径）

1. **有互动才写前缀，各做各的不写**：
   - 两人之间存在互动（拥抱、牵手、摸头、背人、递物、对视等）时，对互动动作加上 `source#` / `target#` / `mutual#`；同一个人身上只跟自己有关的独立动作（如 `sitting`、`holding cup`）直接写原词，不加前缀。
   - 若画面里两个人各自做自己的事、彼此没有互动（如一人靠窗看书、另一人在桌边记笔记），**都不写方向前缀**。
2. **找不到现成动作 tag 时不硬造前缀词**：前缀后只接 Danbooru/NAI 现成动作 tag；没有现成 tag 的复杂互动留在主串英文句子中写清。
3. **链式与主动感细节**：
   - `target#` 只代表语法上的承受方，不代表画面气势被动（例如背人：`Character 1: girl, source#piggyback, tired, looking down,`；被背的人很兴奋：`Character 2: girl, target#piggyback, pointing, excited, open mouth,`）。
   - 三人链式互动时，中间人可同时挂两个前缀（如 `Character 2: girl, target#headpat, source#hug,`）。
4. **何时把动作分开写进角色栏**：
   - **默认写在主串末尾的 `Character N:` 行**，角色栏只放性别外貌与服装，方便用户随时换角色。
   - **当用户明确要求把动作分开写进角色栏**（或成图出现两人动作做反、串人，经建议后用户同意分开写）时：删去主串末尾的 `Character N:` 行，把原本那行的 `<动作（含前缀）>, <姿势>, <表情>, <视线>,` 另起一行放在各自 `Character N:` 代码块的最后一行（第 3 行）；此时互看的视线词可由 `looking at another` 改为 `looking at target`。
5. **特殊用法：Cosplay（A 扮演 B）**：
   - 当用户要求画「角色 A cos 角色 B」的单人图时：主串写 `1girl, solo`（或 `1boy`）；`Character 1` 放 cos 者（加 `source#`），`Character 2` 放被 cos 对象（加 `target#`），并在末尾 `补充:` 提醒用户在 Character Positions 中把两个角色定在**同一个位置点**上。

---

## 三、角色栏写法：原创角色（OC）vs. 版权角色（IP）

1. **起手词**：每个角色栏第一行都以不带数字的 `girl`、`boy` 或 `other` 开头（人数数字只在 `Base Prompt` 开头出现一次；有人与动物同框时主串写 `1girl, black cat`，去掉 `solo`）。
2. **原创角色（OC）**：
   - 第一行写 `<girl/boy/other>, <发色、发型、瞳色、身材、兽耳/角/尾/翅膀等固定辨识锚点>,`；第二行写 `<本次服装与配饰>,`。
   - **保留全部给定锚点**，不为求短删掉用户的辨识特征；用户没给长相时不编造。
3. **版权角色（有规范名）**：
   - 第一行写 `<girl/boy/other>, <danbooru 英文/罗马音规范角色名>,`（如 `girl, archetto (arknights),` 或 `girl, hanami saki,`）。**姓在前名在后，中间用空格或下划线，变音符转 ASCII（ō → ou），绝不用中文名或把角色名和作品名粘成一个词**。
   - **默认外观不凭印象补写，用户指定细节逐项保留**：用户只点名角色时，常规发色瞳色和默认服装由名字自动触发，无需手写长串默认外貌；用户只说「穿泳装」就只加 `swimsuit,`；但**用户明确指定的服装部件、饰品或改色改发型（哪怕与原设定一致）必须逐项写进角色栏**，绝不能缩成一个笼统词。
   - **新角色或冷门角色兜底**：拿不准模型是否已收录时，保留规范名，补上独立作品名和少量已核实的核心外貌结构锚点，并在 `补充:` 说明收录不确定。

---

## 四、词组与句子的配合及高频防错规则

### 1. 词组与自然语言分工

- **词组（Tags）**：列离散对象、人数、姿势体位（`sitting, on side, arm support, head rest, knees slightly bent`）、取景距离（`full body, cowboy shot, upper body, close-up`）、机位角度（`from above, from below, from side, three-quarter view`）、表情视线与光影词。
- **自然语言句子**：写空间方位、谁的哪只手接触或承托哪里、前后遮挡、光线从哪打向哪、运动停在哪一瞬（如衣发随风或动作扬起的方向）、身体部位占画幅的比例。

### 2. 高频实测防错清单（落笔必查）

- **闭眼不写瞳色与视线**：画面人物闭眼（`closed eyes`、睡着）时，**不写任何视线方向词（如 `looking at viewer`），也不写眼睛颜色（如 `blue eyes`）**——哪怕角色设定里有瞳色也不写，写了容易把闭着的眼画睁开。
- **嘴部占用时的表情**：人物嘴里叼着、咬着或吃着东西时，若用户没指定表情则不写嘴部表情词；若指定了表情，挑嘴里有东西也能做出的词。**吹气、呵气时**嘴部写 `pursed lips`，并把 `blowing` 放在该人物动作最后。
- **景别与体位自洽**：
  - 人物在**走路（`walking`）或坐在地上**且用户未指定景别时，景别用 `full body`（用半身或七分身会截断腿脚导致看不出在走或坐地）。
  - `close-up`、`portrait` 近景**不配 `standing`**。
  - 同一个人身上不写互相打架的体位词（不同时写 `standing` 和 `walking`，或 `standing` 和 `sitting`）。
  - **两人并排走**且用户未指定机位时，用斜前方 `three-quarter view`，不用正侧面 `from side`。
  - 垂直机位（`from above` / `from below`）与水平机位（`from side` / `from behind` / `straight on`）每类最多选一个组合。
- **季节词位置**：用户只要求「穿某季节的衣服」（如冬装）而未要求雪景时，季节词只写在服装上，不写进主串场景，避免平白画出满地积雪。
- **服装状态词陷阱**：
  - `loose socks` 是粗针泡泡袜/堆堆袜，**不是**「丝袜滑落」；`single thighhigh` 是只穿一只袜子，**不是**「一只滑下来」。
  - 要表现「一侧丝袜滑落」：写 `white thighhighs, uneven legwear,` 并配句子 `One thighhigh has slipped down to bunch just below the knee,`。
- **强调身体局部**：优先用机位（如 `from below`）＋ 占画幅句子（如 `Her legs dominate the lower half of the frame,`）；需要局部焦点词时可用 `foot focus`、`hand focus`、`eye focus`、`back focus` 等配合镜头边界。
- **防 `PROHIBITED_CONTENT` 姿态与主语规范（Gemini 必守）**：
  1. **英文自然语言句主语不用 `girl` / `boy`**：`1girl` / `girl` 只放在标签位；自然语言关系句统一用 `The character`、`The figure`、`She`（多人用 `The character on the left`、`The woman in the white shirt`），避免 `The girl` + 姿态/衣物描写触发自然语言安全分类器误拦。
  2. **躺卧、睡姿与放松神态采用「几何支撑」表达**：写侧躺（`lying, on side`）、斜靠、午睡或慵懒姿态时，聚焦于重心与支撑点（如 `arm support, head rest, knees slightly bent, relaxed posture, sleepy expression, soft smile`；句子写 `The character rests on her side on a checkered picnic blanket, propping her head on one hand while her other arm rests loosely along her waist,`）。用户未点名时，**不主动叠加 `parted lips`、`half-closed eyes`、`sweat`、`heavy breathing`**，也不描写躯干/臀胯陷入柔软织物或手抚自身脸颊/躯干的感官细节。

---

## 五、分格设定图与多视图（单图多视窗）

当用户要表情集、服装正背设定页或拍立得相册拼贴（非连续故事漫画）时：
1. 主串开头用句子声明版式（如 `A reference sheet with one large full-body front view on the left and two smaller inset views on the right,` 或 `A 2x2 grid of four headshot portraits showing different expressions,`），配合 `multiple views`、`reference sheet` 等标签。
2. 逐个视图用带方位锚点的短句写出各自姿态、角度或表情，各视图之间不混用句子。
3. 末尾 `补充:` 提醒用户将 **UC 预设换成 Light 或 None**（若要 UC 则从 UC 中删去 `multiple views` 和 `extra characters`）。

---

## 六、常见成图症状排查速查

| 成图症状 | 排查与修正方法 |
|---|---|
| **多角色串味、衣服发色互换** | 检查主串是否误写了外貌清单、人数 tag 是否只在主串开头出现一次、主串前两行是否混入了动作词、英文句子是否误用 `Character 1` 作主语；仍串味时建议用户把各人动作（含 `source#`/`target#`）分开写进各自角色栏最后一行，或在角色专属 UC 栏排除对方特征 |
| **两人互动做反（谁抱谁反了）** | 检查主串 `Character N:` 行的 `source#` 与 `target#` 是否挂对且用了同一个动作词；三人以上或对称动作仍反时，建议把动作行移入各自角色栏末尾 |
| **姿势画糊、多手多腿** | 检查是否把连续多步动作塞进同一瞬间，或同时写了冲突体位词；单人补明确姿势 tag（如 `sitting, arm support, head rest`），多人核对各人 `Character N:` 行的体位词 |
| **整张图变成彩斑／泥浆纹理** | 检查是否有数字结尾的画师名或 tag 紧贴 `::`（如 `na_tarapisu153::` 被当成 153 倍权重），改为 `na_tarapisu153, ::` |
| **画面文字出不来或缺笔少画** | 确认要画的字已用双引号包裹并写清载体句、写字表面朝向镜头；提醒用户关闭官网质量词开关（含 `no text`），若给 UC 则删去 `logo` |
| **角色落入纯白虚空背景** | 检查场景描述是否具体；确需排斥白底时在主串负权重行加 `-1::simple background::` |
| **逆光导致人脸黑死** | 若允许调整光效，可在负权重加 `-2::backlighting::` 或正向补 `front lighting, face lighting` |
