<a id="writing-comics"></a>

# 漫画写法：整页与分组漫画提示词编译、色彩转换与排错

本文件用于将已确定的分镜与逐格内容编译为 NAI Diffusion V5 的整页或分组漫画提示词。基础语法、质量词与 UC 规则见 [提示词写法总纲](writing-core.md#writing-core)；若剧情或逐格镜头尚未确定，先阅读 [漫画分镜与台词设计](comic-storyboard.md#comic-storyboard)。

> **跳过分镜直出提示词的处理**：当用户明确要求跳过分镜、直接输出漫画提示词，且手里还没有逐格稿时，在同一轮回复中**先列出简短的逐格简稿（一格一行，标明是本次代补的）**，紧接着输出完整的漫画提示词字段。

---

<a id="comic-adapter.s01"></a>

## 1. 核心概念区分：身份、画格、覆盖与 Character 框

在 NAI V5 漫画工作流中，以下四个概念分别计数，切勿混同：

1. **故事身份（主串人数标签）**：
   - `Base Prompt:` 开头的人数标签按**本次生成单元（本页或本组）中实际出场的独立角色身份去重计算**，男女分别统计。
   - 同一女性在四格中出场四次 = `1girl`；两位女性轮流单人出镜或同格出镜 = `2girls`；一女一男 = `1girl, 1boy`。
   - **绝不按出场总次数、画格总数或 `Character N` 框数写人数标签**。
2. **画格称呼（位置与大小定位）**：
   - 用方位与大小唯一指向同页画格，如 `the top left panel`、`the narrow middle left panel`、`the full-width top panel`、`the huge bottom panel`。
   - **不使用 `Panel 1`、`Panel 2` 等数字编号**（数字编号无法告诉模型画格在页面哪里）。
   - **四格默认 2×2、从左往右读**：左上 `the top left panel` → 右上 `the top right panel` → 左下 `the bottom left panel` → 右下 `the bottom right panel`。竖排单列或右→左读序仅在用户明确指定时使用。
3. **无框前景覆盖（`unframed foreground overlay`）**：
   - 叠在底层画格前方的独立无框人物或画面，承载一个独立瞬间。
   - **不计入底层画格总数**（例如 3 个底层格 + 1 个前景覆盖，主串仍写 `divided into three panels`，再用一句话点明覆盖位置）。
4. **`Character N` 输入框**：
   - 前端第几个角色提示框。在漫画写法中，它代表**一次格内出场或一幅局部画面的容器**，编号并不等于画格号，也不等于故事总人数。
   - 同一角色在 3 格出场占 3 个框；两人同在一格占 2 个框；两只匿名手互动合占 1 个框。

---

<a id="comic-adapter.s04"></a>

## 2. 决定一格用几个 `Character` 框

| 该格可见内容 | 分框方式 |
| --- | --- |
| **1 名可识别人物** | **1 个框**：包含该格定位、镜头、该人物本框可见外貌衣物、动作、场景与台词 |
| **2 名或更多可识别人物同格** | **每人 1 个框**：所有同格框复用**完全相同的画格位置与大小称呼**（如都以 `In the bottom right panel, medium shot, back view:` 开头）；每框只写对应那一个人的外观、动作与属于他的台词；共享背景只在其中一个框写清，另一框只留必要空间锚点 |
| **匿名局部互动（如两只手拧瓶盖、手抓袖口、两双脚走过水洼，未拍到可识别人脸/主体）** | **合为 1 个框**：在一个框内写清两只手/脚分别从哪一侧入画、如何接触、露出的袖口/鞋靴与道具，**切勿按手的主人拆成两个框**（拆框会让模型画成两个独立窄格） |
| **1 名可识别人物 + 另一人的匿名局部手** | **1 个框**：以可识别主体组织，匿名手并入该框并写明入画方向与接触 |
| **单纯道具特写或环境空镜** | **1 个框**：只写可见物体与环境，不塞入人物外貌 |

> **注**：漫画模式按格分框定位，不使用普通多人插画的 `source#` / `target#` / `mutual#` 前缀，格内互动直接用自然语言方位与接触短句表达。

---

<a id="writing-comic-state"></a>

## 3. 跨格可见子集与状态连续性

1. **每个框都重填本格可见的外貌与服装子集**：
   - 模型在每个 `Character N` 框内需要独立读取该次出场的视觉特征。**后续格再次出场时，必须重新填入该镜头实际可见的发型、发色、瞳色与衣物**。
   - **不能写 `same girl`、`Character 1`、角色名字或“同上”来代替外貌与服装描述**。
   - **按取景裁剪可见子集**：全身/半身写清对应衣物；脸部特写只写脸、头发与入镜衣领，省略画外的长裤与鞋靴；匿名手部格只写手、前臂与入镜袖口。
2. **持续状态不因新动作重置**：
   - 前格右手拿起钥匙，本格左手拿起马克杯：只要两只手都在镜头内，本格必须写 `has just picked up the plain mug with her left hand. Her right hand still holds the small keyring.`
   - 空手状态直接用正向短语 `her empty left hand` 交代，不列一串“没有拿什么”的否定清单。
   - 毯子覆盖高度（如盖到下巴 vs. 滑到腰间）、书本开合、瓶盖旋紧/打开、包的开口机构等状态跨格保持前后一致。

---

<a id="comic-adapter.s02"></a>

## 4. 漫画完整导出模板与字段顺序

漫画完整导出按以下顺序输出，栏名带英文冒号写在代码块外上方，代码块内不写栏名：

### 4.1 `Base Prompt:`

```text
<本页去重人数标签>, <色彩模式与 manga 词>. Read left to right, then top to bottom.
The page is divided into <总格数英文词> panels: <各行组的格数、位置与相对大小>.
<前景覆盖声明（仅在采用无框前景覆盖时写，否则省略）>
<本页负权重排除行（按需，无则省略）>
```

- **常见布局句写法**：
  - **默认 2×2 四格**：`The page is divided into four panels: two panels side by side across the top and two panels side by side across the bottom.`
  - **上通栏 + 下两格（三格）**：`The page is divided into three panels: one large full-width top panel above two equal small bottom panels.`
  - **左大竖格 + 右上下两小格（三格）**：`The page is divided into three panels: a large vertical panel on the left and two small panels stacked on the right.`
  - **三行五格（1+2+2）**：`The page is divided into five panels: one full-width top panel, a narrow middle left panel beside a wide middle right panel, a narrow bottom left panel beside a wide bottom right panel.`
  - **单列竖排四格（仅用户指定时用）**：`The page is divided into four horizontal panels stacked in a single column.`

### 4.2 `Character 1:` ～ `Character N:`

- **普通画格框开头**：
  ```text
  In the <方位与大小> panel, <视图与镜头>: <本框可见主体与外貌衣物（自然语言句主语优先用 a woman / a character / a figure，避免用 a girl）>, <本格新动作与仍入镜的持续状态>, <本格场景、光线与文字载体>.
  ```
- **局部破框（肢体或发梢越过本格边框）**：
  仍使用所属画格的 `In the <方位与大小> panel, <视图与镜头>:` 开头，在冒号后的描述末尾加一句越界部位说明（如 `The top of her hair extends above the panel.`），不改写主串格数。
- **无框前景覆盖框开头**（见 [§1](#comic-adapter.s01)）：
  ```text
  In the <覆盖位置与跨度> foreground overlay across <被覆盖的底层画格称呼>, <视图与镜头>: <可见外貌衣物>, <单一明确动作瞬间与可见状态>.
  ```

### 4.3 `Undesired Content:`（仅在用户索要 UC 时输出）
- 沿用用户自己的 UC 或 [写法总纲基础串](writing-core.md#shared-quality)，**固定删去所有漫画冲突项**：
  - 所有漫画（含全彩）必删：`multiple views`、`halftone`、`screentone`、`extra characters`
  - 有留白需求时删：`negative space`
  - 任一格含对白、旁白、拟声词或道具文字时删：`logo`
- 删去上述词后，结果即：
  ```text
  2::extra fingers, extra toes, watermark, signature, deformed, ::, artistic error, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, dithering, too many watermarks
  ```

### 4.4 `补充:`（写在所有代码块外最后）
完整导出必须在 `补充:` 下提供以下三项操作说明（用户明确不要设置说明时除外）：
1. **简短版式与框对应表**：说明每个 `Character N` 框对应哪一格、在该格内的哪一侧。
2. **手动角色位置（Character Positions）操作说明**：提醒用户在角色提示词区把位置从 `AI's Choice` 改为 `Custom`，点击 `Character Positions` 打开画布，按各框所在画格区域放置点位（如 2×2 四格：框 1 左上、框 2 右上、框 3 左下、框 4 右下格靠左、框 5 右下格靠右）。
3. **官网预设开关提醒**：
   - 任一格有文字时：提醒**关掉官网的质量词开关（Quality Tags）**（因其自带 `no text`）。
   - 所有漫画导出：提醒把**官网的 UC 预设换成 `Light` 或 `None`**（`Heavy` 与 `Human Focus` 含 `multiple views, halftone, screentone`，`Furry Focus` 含 `comic, multiple scenes, sequence`，都会压制漫画分格与网点）。

---

<a id="comic-adapter.s05"></a>

## 5. 格内文字载体与静默格规则

| 文字用途 | 标准写法 |
| --- | --- |
| **普通对白** | `A speech bubble above her reads "……", its tail pointing to her mouth.` 或简写 `speech bubble, "……"` |
| **急促喊声 / 惊叫** | `jagged speech bubble, "……"` |
| **内心独白** | `thought bubble, "……"` |
| **旁白 / 时间地点说明** | `Narrator box, "五分钟后。"`（统一使用 `Narrator box`） |
| **道具上的字** | `The note on the table reads "……".` |
| **动作拟声词（SFX）** | `Small sound-effect lettering beside the latch reads "咔".` |
| **静默无字格** | **直接省略文字指令**（**切勿写 `no text` 或 `No text in this panel.`**） |

- **文字归属**：对白写进说话人所属的那个 `Character N` 框；同格共享的旁白或拟声词只选一个框写一次，不在同格两个框里重复。
- **后期排字模式**：若用户指定“无字底图 + 后期自己排字”，生成框只写留位要求（不放引号台词），并在 `补充:` 下另列 `画格位置/说话者或载体/台词原文` 对照清单。

---

<a id="comic-continuity.s03"></a>

## 6. 漫画色彩模式转换与输出前检查

漫画默认**全彩（`manga`）**。只有用户明确指定半黑白或纯黑白时，才按以下规则转换主串与所有 `Character N` 框的颜色词：

| 模式 | `Base Prompt:` 风格词 | 各 `Character N:` 框的颜色处理规则 |
| --- | --- | --- |
| **全彩（默认）** | `<人数标签>, manga.` | 保留所有角色发色、瞳色、服装原色、道具颜色与环境色彩 |
| **半黑白（仅保留发色与瞳色）** | `<人数标签>, manga, {{{greyscale with colored eyes,greyscale with colored hair}}}.` | **仅保留头发和眼睛的彩色词**；服装、配饰、金属（`gold`/`bronze` → `metallic`/`dark`）、道具、食物、深色液体、天空与环境光（`warm amber light` → `soft angled light`）的色相词全部转为明暗/质感词 |
| **纯黑白（全灰阶）** | `<人数标签>, manga, monochrome.` | **所有字段（含头发、眼睛、服装、道具、背景）全部去掉色相词**，转换为 `pale`、`light`、`medium-toned`、`dark`、`black`、`white` 等明暗对比锚点 |

### 黑白 / 半黑白转换关键防坑
- **去色相不等于删掉深浅锚点**：如果直接删掉发色词而没补 `pale hair` 或 `dark hair`，同一角色跨格或跨页很容易发生深浅发色互换。转换时必须把原有的浅色/深色转化为稳定的明暗词并跨格复用。
- **切回全彩时**：从设定原色恢复完整色彩，并清除主串中的 `monochrome` 或 `greyscale...` 词组。

---

<a id="comic-adapter.s07"></a>

## 7. 实图常见症状与排错速查

| 实图症状 | 优先排查与修正方式 |
| --- | --- |
| **一次双手互动被拆成两个窄格** | 检查是否把两只手按角色拆成了两个 `Character` 框 → 合并为一个局部互动框 |
| **每一格都塞进两位主角** | 检查主串是否把全员外貌写进了 `Base Prompt:`，或单人出场格混入了另一人描述 → 主串只留去重人数标签，外貌严格按各格实际出镜者写进对应框 |
| **场景或动作串格** | 检查主串布局枚举与各框 `In the ... panel` 称呼是否一一对应且唯一；检查是否在一个框里写了两个连续动作瞬间 |
| **台词串人、漏字或网点被压平** | 检查是否关掉官网质量词开关（含 `no text`），检查官网 UC 预设是否已改为 `Light` 或 `None`，检查手写 UC 是否已删去 `multiple views, halftone, screentone, logo` |
| **前景覆盖变成了旁边的独立分格** | 检查是否把覆盖计入了主串总格数，或给覆盖框写了独立背景 → 主串总格数只计底层格，覆盖框用 `unframed foreground overlay` 开头并去掉独立背景 |
| **旧持物消失或衣服/毯子高度突变** | 按阅读顺序检查各格状态：补回仍入镜手部的既有持物短语，统一毯子/衣物的身体位置锚点 |

---

<a id="comic-examples.s09"></a>

## 8. 完整导出示例：全彩 2×2 四格（含双人同格、匿名局部合框与 UC）

情境：雨天下班，一人忘带伞，同伴递伞，两人共撑一把黄伞离开。默认 2×2 从左往右读（左上 → 右上 → 左下 → 右下），共 2 名女性、4 个画格、5 个 `Character` 框（左下格拍两双脚为匿名局部合 1 框，右下格两人同框拆为 2 框）。

Base Prompt:

```text
2girls, manga. Read left to right, then top to bottom. The page is divided into four panels: two panels side by side across the top and two panels side by side across the bottom.
-1::clear sky, sunlight::
```

Character 1:

```text
In the top left panel, medium shot, eye-level view: a woman with a low auburn ponytail and a grey office blazer over a white blouse stands under the entrance canopy of an office building, rummaging through her open shoulder bag with a troubled look. Heavy rain falls beyond the canopy edge. A thought bubble above her reads "……伞呢？"
```

Character 2:

```text
In the top right panel, medium shot, three-quarter view: a woman with wavy shoulder-length pink hair and a dark green field jacket holds out a closed yellow umbrella toward the left with a small smile. A speech bubble above her reads "一起走吧。"
```

Character 3:

```text
In the bottom left panel, low-angle close-up: two pairs of feet in ankle boots walk side by side through shallow puddles under the lower edge of one yellow umbrella, raindrops splashing around them. Only the feet, the ankles, and the umbrella edge are visible.
```

Character 4:

```text
In the bottom right panel, medium shot, back view: a woman with a low auburn ponytail and a grey office blazer over a white blouse walks on the left under a shared yellow umbrella, her outer shoulder dark with rain. She glances toward the woman on her right with a small laugh.
```

Character 5:

```text
In the bottom right panel, medium shot, back view: a woman with wavy shoulder-length pink hair and a dark green field jacket holds the shared yellow umbrella on the right, her outer shoulder dark with rain. A speech bubble above her reads "伞有点小。"
```

Undesired Content:

```text
2::extra fingers, extra toes, watermark, signature, deformed, ::, artistic error, scan artifacts, worst quality, bad quality, jpeg artifacts, very displeasing, dithering, too many watermarks
```

补充:

角色位置：在角色提示词区把位置从 AI's Choice 改成 Custom，点 Character Positions 打开画布，按以下位置摆放：Character 1 放左上格，Character 2 放右上格，Character 3 放左下格，Character 4 放右下格靠左，Character 5 放右下格靠右。本页有文字，请关掉官网的质量词开关（Quality Tags）；同时把官网的 UC 预设换成 Light 或 None。
