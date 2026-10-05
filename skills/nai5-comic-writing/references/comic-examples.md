<a id="writing-comic-examples"></a>

# 漫画写法示例与适用边界

以下原始代码围栏逐字保留，用于说明字段、局部修改和关系表达。例子的角色、格数、台词、色彩或动作不是任务默认；旧例与当前契约不同之处按块外说明理解，不能以示例改掉用户要求。共同规范与完整字段优先，参数或位置文本不是已经执行的操作。

<a id="comic-examples.preamble"></a>

## 漫画完整示例与局部改写

下例展示字段和取景，不是已出图验证的样张。示例使用普通成年角色，不是用户 OC；实际用库内 OC 时按本格可见范围提取其身份事实，不照搬此处外貌或剧情。

这些完整提示词示例假设**质量与 UC 预设关闭**、用户没有给出自己的 UC，因此给出实际尾词和删去漫画冲突项后的基础串；用户有自己的 UC 时换成它，同样只删冲突项。开启预设时按适配器去实际重复与冲突项。主串不带 `Prompt:` 显示标头，Character / UC 保留。

这些提示词示例属于**分镜经用户确认或修改后的第二阶段**。未审的新剧情先由 `nai5-comic-storyboard` 处理当前创作阶段；已有定稿或明确直接转换时使用这些表达示例。

本节中的 `manga, monochrome` 示例（例一、例五、例六）均假设用户明确选择黑白，仅演示该模式；新漫画默认全彩，全彩完整示例见例七。全彩与半黑白的颜色对照见 “色彩模式与输出前检查”（`nai5-writing`：`references/conventions.md#comic-continuity.s03`），套用布局时须按当前模式处理各框。

<a id="comic-examples.s01"></a>

### 例一：五格黑白短段，六个 Character 框

情境：两人准备早餐，一起拧开果酱瓶。左→右、上→下：上方建立情境，中段用手部互动和发力反应，底部确认打开与回应。中排右侧宽格的小幅破框强调使劲的瞬间。此例是完整小段落；用户只要开头时，按其要求保留后续空间。

```text
2girls, manga, monochrome. Read left to right, then top to bottom. The page is divided into five panels: one full-width top panel, a narrow middle left panel beside a wide middle right panel, a narrow bottom left panel beside a wide bottom right panel.
very aesthetic, masterpiece
```

**Character 1 — 上方全宽格，室友A**

```text
In the full-width top panel, medium shot, eye-level view: an adult woman with long pale hair in a loose side braid and a dark striped pajama top sits on the right. She braces a squat glass jam jar with a closed ribbed screw lid on a small breakfast table, looking toward the left. A simple kitchen doorway is visible behind her.
```

**Character 2 — 上方全宽格，室友B**

```text
In the full-width top panel, medium shot, eye-level view: an adult woman with dark hair in a high ponytail and a light apron over a plain shirt sits on the left, leaning toward the jar at the center of the table. A speech bubble above her reads "我来。", its tail pointing to her mouth.
```

**Character 3 — 中排左侧窄格，完整手部互动**

```text
In the narrow middle left panel, tight close-up, slightly elevated view: two bare hands enter from opposite sides. The right-entering hand braces the squat glass jam jar; the left-entering hand grips its closed ribbed screw lid, fingers tense against the ridges. Only the hands, short sections of bare forearms, and the jar fill the frame.
```

**Character 4 — 中排右侧宽格，室友B发力反应**

```text
In the wide middle right panel, close-up, slightly low angle: an adult woman with dark hair in a high ponytail, the strap of a light apron visible, squeezes her eyes shut and puffs her cheeks with effort, shoulders raised. The top of her hair extends above the panel.
```

**Character 5 — 下排左侧窄格，开合结果**

```text
In the narrow bottom left panel, tight close-up, side view: a bare hand enters from the upper left, holding the detached ribbed screw lid just above the open threaded mouth of the squat glass jam jar. Small sound-effect lettering beside the lid reads "啵".
```

**Character 6 — 下排右侧宽格，室友A回应**

```text
In the wide bottom right panel, close-up, three-quarter view: an adult woman with long pale hair in a loose side braid, the collar of a dark striped pajama top visible, turns toward the left with a relieved smile. A speech bubble above her reads "救星！", its tail pointing to her mouth.
```

**UC:**

```text
lowres, artistic error, film grain, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, chromatic aberration, dithering, logo, too many watermarks, negative space, blank page
```

本例演示三件事：同格可识别人物分别建框，匿名手部接触合框，旋盖前后的结构保持一致。本页是两个人、五格、六个提示框，因此主 Prompt 用 `2girls`。上方全宽格的两名可识别人物各一个框，复用完全相同的 `In the full-width top panel`；中排左侧窄格的两位人物的手合在一个框，不另加人数。人物特写没有裤子/鞋，下排左侧的道具格没有重新贴人物外观。旋盖结构从首次出现到打开一直一致；“拧开”的中间过程由格间省略完成，道具格只画已打开这一瞬间。

<a id="comic-examples.s02"></a>

### 例二：修正错误拆框

不合适的组织：
- Character 3 / 中排右侧窄格：某角色的手。
- Character 4 / 中排右侧窄格：另一角色的手。

如果镜头仅显示手与袖口，把它们改为同一个框，写清一只手怎样接触另一只手/袖口，分别从哪里入画，以及实际可见的衣料。不能仅因知道两只手各属于谁，就把局部接触拆成两幅画面。

若镜头同时拍到两个人的脸和主体，则仍分别建框；不要把这个合并例外扩大为全部双人戏。

<a id="comic-examples.s03"></a>

### 内容调整与写法压缩分开

原稿每格都保留两人和同一房间时，先减少重复表达，保留既定出场与镜头；不能因提示词长就改成单人、匿名手部或结果画面。用户愿意重设计时才把这样的镜头选择交回 `nai5-comic-storyboard`。道具结构按现稿延续，不能临时把敞口手提包改成拉链肩包；表达核对见 [状态与可见子集](comics.md#writing-comic-state)。

<a id="comic-examples.s04"></a>

### 例四：文字和后排

直出时，各框分别按实际用途写：
- 对白：`A speech bubble above her reads "等一下。", its tail pointing to her mouth.`
- 旁白：`A Narrator box at the upper left reads "五分钟后。".`
- 道具文字：`The note pinned to the door reads "今天休息".`

静默格直接结束画面描述。若用户指定后期排字，生成框写清对应留位，另列“画格位置/大小／说话者或载体／原文／位置”；不把后排原文再放入生成引号。无需复制一套“每格无字”的否定模板。

<a id="comic-examples.s05"></a>

### 例五：局部前景覆盖，只跨下方两格

三格记录一位成年室友读书、合书、望向窗外；下方居中的无框半身承载随后歇一会儿的收尾。读序为上方全宽格→下方左格→下方右格→覆盖画面。覆盖只跨下方并排两格的内侧，两个小格的关键内容分别靠外侧安排。这里只演示一种局部范围，不是通用布局。

```text
1girl, manga, monochrome. Read left to right, then top to bottom. The page is divided into three panels: one large full-width top panel above two equal small bottom panels. An unframed foreground overlay occupies the lower center, covering the inner portions of both bottom panels.
very aesthetic, masterpiece, no text
```

**Character 1 — 上方全宽格，读书**

```text
In the large full-width top panel, medium shot, side view: an adult woman with shoulder-length wavy light hair, round glasses, and a dark turtleneck sweater sits at a small wooden reading table beside a window, looking down at an open book. Soft daylight falls across the tabletop.
```

**Character 2 — 下方左格，合书局部**

```text
In the small bottom left panel, close-up: a bare hand rests on the just-closed cover of a book on a wooden tabletop, near the outer left side of the panel.
```

**Character 3 — 下方右格，看向窗外**

```text
In the small bottom right panel, facial close-up, profile: an adult woman with shoulder-length wavy light hair and round glasses looks left toward the window, with relaxed eyebrows and a faint smile. Her face is near the outer right side of the panel.
```

**Character 4 — 下方中央的覆盖画面**

```text
In the lower-center foreground overlay across the inner portions of both small bottom panels, waist-up, three-quarter view: an adult woman with shoulder-length wavy light hair, round glasses, and a dark turtleneck sweater sits with her chin resting on one hand, eyes gently closed and shoulders relaxed. Her elbow rests on the wooden tabletop beside the closed book. This is a single resting moment after the small bottom right panel.
```

**UC:**

```text
lowres, artistic error, film grain, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, chromatic aberration, dithering, logo, too many watermarks, negative space, blank page
```

本例的关键是覆盖只跨下方两格的内侧，底层两格的脸和手分别靠外，留出遮挡空间。这是一个角色、三个底层画格、一个覆盖画面、四个提示框，因此主 Prompt 用 `1girl`；重复出场及覆盖画面不增加人数或底层格数。覆盖范围以位置和大小说明即可，不逐条补写格线遮挡规则。闭合的书在下方局部格和覆盖画面中都保持闭合；看窗外的面部特写省略画外的书和手。

<a id="comic-examples.s06"></a>

### 例六：旧物件与新动作并存

右手已经拿着钥匙，下一格左手才拿起杯子；最后切脸部特写。以下三个局部框依次对应同一行中从左到右的三个小格。

```text
1girl, manga, monochrome. Read left to right, then top to bottom. The page is divided into three equal small panels side by side in one row.
very aesthetic, masterpiece, no text
```

**Character 1 — 左侧小格，已拿着钥匙**

```text
In the small left panel, waist-up, front view: an adult woman with long curly hair clipped up at the back and a plain light T-shirt holds a small keyring in her right hand. Her empty left hand rests beside a plain mug on the table.
```

**Character 2 — 中间小格，左手拿起杯子**

```text
In the small middle panel, waist-up, front view: an adult woman with long curly hair clipped up at the back and a plain light T-shirt has just picked up the plain mug with her left hand. Her right hand still holds the small keyring.
```

**Character 3 — 右侧小格，表情特写**

```text
In the small right panel, tight facial close-up, front view: an adult woman with long curly hair clipped up at the back gives a faint, satisfied smile.
```

**UC:**

```text
lowres, artistic error, film grain, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, chromatic aberration, dithering, logo, too many watermarks, negative space, blank page
```

中间格两只手都可见，须同时写左手的新动作和右手已成立的持物状态。左侧格用 `empty left hand` 交代当时左手状态，杯子还在桌上；右侧格只见脸，省略画外的手与道具。

<a id="comic-examples.s09"></a>

### 例七：全彩四格，默认 2×2 从左往右

情境：雨天下班，一人忘了带伞，同伴递伞，两人共撑一把伞回家。用户没指定版式，按默认 2×2、从左往右读：左上 → 右上 → 左下 → 右下。全彩，有字。

```text
2girls, manga. Read left to right, then top to bottom. The page is divided into four panels: two panels side by side across the top and two panels side by side across the bottom.
very aesthetic, masterpiece
-1::clear sky, sunlight::
```

**Character 1 — 左上格，发现没带伞**

```text
In the top left panel, medium shot, eye-level view: an adult woman with a low auburn ponytail and a grey office blazer over a white blouse stands under the entrance canopy of an office building, rummaging through her open shoulder bag with a troubled look. Heavy rain falls beyond the canopy edge. A thought bubble above her reads "……伞呢？"
```

**Character 2 — 右上格，同伴递伞**

```text
In the top right panel, medium shot, three-quarter view: an adult woman with wavy shoulder-length pink hair and a dark green field jacket holds out a closed yellow umbrella toward the left with a small smile. A speech bubble above her reads "一起走吧。"
```

**Character 3 — 左下格，伞下两双脚（匿名局部，合一个框）**

```text
In the bottom left panel, low-angle close-up: two pairs of feet in ankle boots walk side by side through shallow puddles under the lower edge of one yellow umbrella, raindrops splashing around them. Only the feet, the ankles, and the umbrella edge are visible.
```

**Character 4 — 右下格，左边的人**

```text
In the bottom right panel, medium shot, back view: an adult woman with a low auburn ponytail and a grey office blazer over a white blouse walks on the left under a shared yellow umbrella, her outer shoulder dark with rain. She glances toward the woman on her right with a small laugh.
```

**Character 5 — 右下格，右边的人**

```text
In the bottom right panel, medium shot, back view: an adult woman with wavy shoulder-length pink hair and a dark green field jacket holds the shared yellow umbrella on the right, her outer shoulder dark with rain. A speech bubble above her reads "伞有点小。"
```

**UC:**

```text
lowres, artistic error, film grain, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, chromatic aberration, dithering, logo, too many watermarks, negative space, blank page
```

附注（给用户，放在代码块外；本例用角色位置功能指定分格）：角色位置：在角色提示词区把位置从 AI's Choice 改成 Custom，点 Character Positions 打开画布，这样放：Character 1 左上，Character 2 右上，Character 3 左下，Character 4 右下格靠左，Character 5 右下格靠右。

本页两个人、四格、五个提示框，主串用 `2girls`。未指定版式，按默认 2×2、从左往右读，四格依次称呼 top left、top right、bottom left、bottom right。左下格只拍两人的脚和伞沿，是匿名局部，合一个框；右下格两名可识别人物各一个框，定位句完全相同。全彩只写 `manga`；有字页质量尾不带 `no text`；UC 是删去漫画冲突项后的基础串；雨天不要晴空和日光，写成主串最后的负权重行，不进 UC。

<a id="comic-examples.s07"></a>

### 更多布局与叙事示例

[布局与叙事示例](#comic-composition.preamble) 补充布局段、角色框开头、文字载体及连续性组织的用法。人物、场景和动作仍按现有技能规范填写；示意片段不替代完整的成品提示词。

<a id="comic-examples.s08"></a>

### 按请求缩小交付

用户只要“两条一句话的故事点子”时，只交两条点子，不附页格规划或 NAI 字段。
用户只要求把中间格“左手端杯”改成“刚放稳杯子”时，只返回该框或指定短语：

```text
has just set the mug securely on the table with her left hand
```

其他原有服饰、右手持物、台词、空格和权重均不改；不因为示例中完整导出含质量尾与 UC，就给局部修改补齐整页字段。用户冻结文字的转换也不追加新的声效。

<a id="comic-composition.preamble"></a>

## 漫画布局与叙事示例

以下简化示例用于说明布局段、角色框开头、文字载体和镜头衔接，不代表已出图验证。画面中的角色外貌、动作和场景仍按 [适配器](comics.md#comic-adapter.preamble) 与基础写法填写；示例中的具体格型和情节均可替换。

<a id="comic-composition.s01"></a>

### 布局段

布局先给总格数，再用位置、相对大小和分组说明画格之间的关系。人数标签沿用 “写法规范与交付边界”（`nai5-writing`：`references/conventions.md#comic-entry.preamble`）；阅读方向默认从左往右、上→下，四格默认 2×2，见 [字段模板与先后顺序](comics.md#comic-adapter.s02)。普通页面不描写分隔线。

<a id="comic-composition.s01.h01"></a>

#### 开场与收束各留一格

```text
The page is divided into four panels: a shallow full-width panel at the top, two side-by-side panels in the middle, and a larger full-width panel at the bottom.
```

可用顶部交代目标，中排分别给关键物件与人物反应，底部展示结果。总格数为四，不因上下通栏横跨两列就重复计数。这是分镜或用户指定这种版式时的写法；未指定时四格默认 2×2。

<a id="comic-composition.s01.h02"></a>

#### 主画面配短反应

```text
The page is divided into three panels: a large vertical panel on the left and two small panels stacked on the right.
```

从左往右读时先进入左侧主画面，再看右侧上、下两格的反应；用户指定右读时整体左右对调。若希望先交代过程再看结果，应随之调整区域与读序，不能只换大小词而保留矛盾的阅读路线。

<a id="comic-composition.s01.h03"></a>

#### 横向行组安排停顿

```text
The page is divided into five panels arranged in three tiers: two panels at the top, a thin horizontal panel in the center, and two panels at the bottom.
```

这里是三行、五格。中央格可以安排短暂远景或空镜，让前后两组信息有停顿。`tiers` 计行组，`panels` 计画格，两者不可混用。

<a id="comic-composition.s01.h04"></a>

#### 重复机位中的变化

```text
The page is divided into four horizontal panels stacked in a single column.
```

同一机位可依次表现等待、发现异状、确认和反应，让微小变化容易比较；有新信息或收束需要时再换景别。各格用 top、upper-middle、lower-middle、bottom 等位置称呼，与主布局一致。竖排单列只在用户指定时用，四格未指定时默认 2×2。

<a id="comic-composition.s01.h05"></a>

#### 计数与定位检查

| 情况 | 处理 |
|---|---|
| 总数和区域枚举不一致 | 以已确定的分镜为准统一，两处不能各留一个版本 |
| 大格跨行或跨列 | 明确它是同一个画格，只计一次 |
| 小画面承担独立镜头或时刻 | 作为插格计入总数，无框也可能是独立插格 |
| 局部叠像只强调当前瞬间 | 先说明与主画面的关系，不自动增加叙事格 |
| 前景覆盖 | 底层格与覆盖画面分开记录，沿用覆盖的专用句式 |
| 一框出现两个画格开头 | 按实际画格分别组织，不用合写省略格位 |

<a id="comic-composition.s02"></a>

### 角色框开头与文字载体

普通框使用 `In the <位置/大小> panel, <视图/镜头>:`。只写足以定位和决定取景的词组，不必每次同时堆满景别、机位、角度与场景类型。

| 镜头任务 | 开头示意 |
|---|---|
| 信息物件的局部 | `In the middle left panel, close-up of a noticeboard:` |
| 建立人物距离 | `In the wide bottom panel, distant view:` |
| 窄格中的表情 | `In the narrow top right panel, facial close-up:` |
| 区分一组堆叠的小格 | `In the lower small panel on the left, close-up:` |

以上仅为开头片段，完整内容接在冒号后。方位必须与主布局唯一对应；Character 编号只表示输入框次序，不替代阅读路线。若实际使用坐标，坐标与文字方位也应相容。

<a id="comic-composition.s02.h01"></a>

#### 文字先选载体

| 用途 | 简写示意 |
|---|---|
| 普通对白 | `speech bubble, "准备好了吗？"` |
| 急促喊话 | `jagged speech bubble, "停一下！"` |
| 思考 | `thought bubble, "原来如此。"` |
| 时间概括 | `Narrator box, "午后。"` |
| 实物上的字 | `text on the sign, "入口"` |
| 设备传来的声音 | `a speech bubble from the radio, "测试结束。"` |
| 动作声效 | `small sound effect beside the switch, "嗒"` |

对白放在说话者所属框，共享旁白或声效只写一次。多人、画外声或多泡先后有歧义时，才补说话者及必要的相对位置；气泡形状表达语气，不能代替归属。

声音内容取自现稿或用户明确的补充要求，表达方式服务已有节奏与氛围。需要静默时省略文字项。有字的省略号或问号仍需相应载体，不等于无字格。

<a id="comic-composition.s03.h02"></a>

#### 持物状态与裁切

一只手拿起文件夹，另一只手随后开门：两只手入镜时，开门这一新动作不能抹去原先持有文件夹的状态。切到脸部特写时省略画外的手；后来重新拍到手，再写当时实际的持物状态。放置或交接需要让读者理解何时发生。

状态空缺直接写“空手”等简短当前状态，不逐项列举不存在的物品。故事事实在画外继续存在，裁切只改变当前提示词的描述范围。

<a id="comic-composition.s03.h03"></a>

#### 大格、插格和覆盖

`splash panel` 可以表示强调性大格，不自动等于无框前景覆盖。需要一个连续人物形象叠在多个底层格前方时，明确用 `unframed foreground overlay` 说明位置与跨度；它可以只覆盖局部区域。

插格与叠像是否另计，依据是是否承担独立叙事镜头/时刻，而不是仅看边线。取景、时间与覆盖关系不确定时先解决分镜，不靠堆叠近义词让模型自行猜测。

<a id="comic-composition.s04"></a>

### 如何核对效果

检查提示词时，先核对人数、格数、局部称呼、时刻与可见状态是否一致；查看成图时，再分别检查布局、镜头、文字载体和说话者归属。画面可读，不代表每条指令都准确落实。

分析带元数据的图片时，区分数据能否读取、记录是否对应当前图片、具体指令是否生效。图生图底图和位置设置等条件也可能影响结果；缺少可比实验时，不将单次成图归因于一个短语。

示例用于表达已经确定的编排，不是固定版式库或稳定成功率承诺。两阶段流程、人数去重、逐人分框、角色事实、实际预设与 UC 条件、拟声词规则均以技能入口及适配器为准。


<a id="writing-layout-record-example"></a>

## 旧布局记录例的写法语境

此原块含角色框操作，因此完整迁到写法侧；它说明已定布局的转写记录，不是创作阶段必须照填的表。格数、范围和读向依本次分镜，不能把示例的六格布局当默认。原记录按当时约定写的是右读；现在默认从左往右读。

```text
载体／方向：单页；右→左，上→下；6 格。
布局：上排全宽一格；中排两格；下排三格。
顺序：上方全宽格 → 中排右格 → 中排左格 → 下排右格 → 下排中格 → 下排左格。
重点：上方全宽格建立；下排左格的未完成动作作为出口。
越界留位：下排左格的左边线外保留页面留白；具体部位与动作写入角色框。
文字留位：只列含文字画格的位置/大小称呼、载体与位置。
时序：六格顺序发生，破框不连接另一时刻。
```
