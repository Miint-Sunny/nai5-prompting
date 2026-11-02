<a id="writing-costume"></a>

# 服装写法：已定服装转换、术语核对与片段排错

本文件用于将已确定的服装设计转换为 NAI Diffusion V5 容易识别、关系清晰、便于排错的提示词片段，或对现有服装串做部件修改与实图排错。基础语法、原串锁定与完整画面规则见 [提示词写法总纲](writing-core.md#writing-core)；若服装方案本身尚未定稿，先阅读 [角色与服装设计](character-and-costume-design.md#costume-design)。

---

<a id="costume-entry.s03"></a>

## 1. 服装提示词的专用交付边界

当用户要求“写服装提示词”“把这套衣服转成 NAI 提示词”或同义片段任务时，本节优先于完整画面字段模板：

1. **单代码块交付**：默认只输出**一个可直接复制的代码块**，格式为：
   ```text
   [角色已知且必要的固定可见外貌锚点], [服装提示词]
   ```
   - 不把 OC 名字本身当作模型已知角色标签。
   - 用户明确“只要衣物串、不带角色”时，省略角色外貌槽，仅输出 `[服装提示词]`。
   - 用户未提供外貌资料时，只写已有事实，不编造发色、瞳色或体型补槽。
2. **不包含非服装字段**：片段内不写人数标签（`1girl` 等）、通用姿势、表情、镜头、场景、背景、光影、氛围、画风、质量词或 `Undesired Content`。
   - **例外**：服装自带的包、背带、武器或标志大道具若必须说明携带方式，可保留一句最短的正向佩戴/手持/肩扛关系（如斜背、肩扛、挂在腰侧），不扩写成战斗动作或通用姿势。
3. **不附带冗余报告**：默认不在代码块外附设计摘要、术语映射表、参数或排错长文；用户明确索要术语核查或解释时，放在代码块外说明。
4. **外貌与衣物的衔接检查**：转换时检查帽子/兜帽是否遮住关键发型、衣领如何接住长发、袖口与手套是否影响手臂、袜靴如何衔接腿脚，以及配色是否保留角色识别锚点。翅膀、尾巴、角和兽耳作为固定可见特征照常写入，**默认不为它们描述衣物开洞、分片、系带或防穿模结构**。

---

<a id="costume-writing.s01"></a>

## 2. 视觉意图清单（动笔前核对）

将中文服装设计稿拆解为可见的部件与关系，按以下 9 项顺序检查遗漏（只列本套服装实际存在的项目）：

1. 服装原型或主单品（如 sailor uniform、tailcoat、pleated dress）。
2. 整体轮廓与长度（如 fitted、oversized、cropped、high-waisted、ankle-length）。
3. 领型、领口、袖型、袖口（如 Mandarin collar、off-shoulder、puff sleeves、bell cuffs）。
4. 外层与内层关系（谁穿在外面、谁露出领口或下摆、谁塞进腰头）。
5. 腰部、下装与开衩/褶结构（如 corset belt、knife pleats、high side slit）。
6. 腿饰和鞋履（如 thighhighs、garter straps、platform ankle boots）。
7. 材质、图案、滚边与装饰工艺（如 matte leather、sheer chiffon、gold embroidery、lace trim）。
8. 标志配件（如胸针、颈环、斜挎包、腰挂配件）。
9. 穿着状态与不对称细节（单侧滑落、敞开、挽袖、半塞入、衣摆掀起，以及配件的佩戴关系）。

### 逐件整理原则
- 每件衣物按 `部件｜左右及数量｜颜色与材质｜形态与长度｜相对位置｜穿着状态` 归并成**一条一次性定义**。
- 颜色紧贴它所修饰的衣物（如 `navy jacket, ivory blouse, burgundy ribbon`），不要把一串颜色词和一串单品词分开放置。
- 一个视觉事实只保留一个主要表达，不在后文用宽泛标签或重复句二次召回同一部件。

---

<a id="costume-writing.s02"></a>

## 3. 现实术语与 Danbooru 标签核对

### 3.1 用 FASHIONPEDIA 确认现实结构名
不确定某个服装结构在英文里叫什么时，优先按 FASHIONPEDIA 体系确认：
- 服装大类与轮廓（silhouette & length）
- 领口与领型（neckline、collar、lapel）
- 袖型与袖口（sleeve、cuff）
- 开合、袋型、省道与褶（opening、closure、pocket、pleat、dart）
- 面料、纺织与装饰工艺（fabric、textile、trim、embellishment）

### 3.2 对齐 Danbooru 标签与自然语言回退
- **匹配优先级**：精确规范标签 → 已确认别名对应的规范标签 → 语义较宽但稳定的类别词 + 自然语言说明。
- **不自造下划线标签**：无法确认 Danbooru 是否存在某个标签时，用普通英文类别词配合可观察结构说明，不自行拼造蛇形标签并声称“已验证”。
- 用户明确要求展示术语核查表时，可在代码块外按以下结构列出：
  ```text
  视觉意图 | 现实服装术语 | Danbooru 规范标签 | 置信度/依据 | 无标签时的回退写法
  ```

---

<a id="costume-writing.s06"></a>

## 4. 服装片段写法规则

1. **部件一次性直接定义**：
   采用 `[颜色/材质/剪裁] + [部件主名词] + [with 细节]` 的紧凑名词短语：
   ```text
   dark-purple knee-high boots with segmented mother-of-pearl armor panels, outward-curling cuffs, low tarnished-silver wedge heels
   ```
   不要先写 `knee boots`，后面再用完整句重复靴子的颜色、护甲、鞋口和鞋跟。
2. **以部件为主语，避免角色引导句**：
   需要用自然语言写复杂结构或层叠关系时，**让服装部件本身做句子主语**，不要写 `She wears...` 或 `The character has...`：
   ```text
   Six overlapping petal-shaped panels form a layered black overskirt around the waist,
   ```
   句子已经完整定义该部件后，不在前后另列 `layered skirt, overskirt` 重复召回。
3. **标签与句子的分工**：
   - **用标签/紧凑短语**：稳定服装类别、颜色、材质、图案、独立配饰。
   - **用不加引号的自然语言短句**：内外层谁盖住谁、谁塞入腰头、单侧滑落、左右不对称、无单一标签的自定义裁片、帽兜与长发关系、配件佩戴方向。
4. **按从上到下的穿着位置排序**：
   ```text
   [角色固定外貌锚点], [服装原型与核心结构], [头颈 → 上身内外层 → 腰胯 → 下装 → 腿脚 → 标志配件], [必要的层叠与佩戴关系句]
   ```
5. **正向定义目标形态**：
   直接描述部件的实际形态；未采用的样式、隐藏不可见的内搭安全层或穿脱设定不写进片段。不写 `"luxurious, premium, detailed, fashionable"` 这类无具体部位指向的空洞形容词。

---

<a id="costume-writing.full-export"></a>

## 5. 将服装放入完整画面

当用户需要包含动作、场景、镜头的完整画面提示词（而非单独服装片段）时，切换回完整画面导出：
- **普通插画**（见 [普通插画写法](writing-illustration.md#writing-illustration)）：主串写人数、动作、镜头、场景与光影；角色外貌与服装分行写进对应的 `Character N:` 栏。
- **漫画分格**（见 [漫画分格写法](writing-comic.md#writing-comics)）：按各格镜头取景裁剪出**本格实际可见的服装子集**，写进对应 `Character N:` 框（脸部特写只写衣领/肩部，不塞画外的长裤和靴子）。
- **服装印字与徽记**：保留印字原文与载体（如 `text "04" printed on the left sleeve`）；若用户要求提供 UC，从 UC 中删去 `logo`，并提醒关闭官网质量词开关。
- **定向排除衣物元素**：本图明确不要的衣物结构写成 `Base Prompt:` 最后的负权重行（如 `-1::cape, headwear::`），不塞进 UC。

---

<a id="costume-writing.s08"></a>

## 6. 易误用服装词与实图排错

### 6.1 常见标签语义陷阱
- **`loose socks`**：指日本JK堆堆袜/泡泡袜，**不表示“袜子松脱滑落”**。
- **`single thighhigh`**：指只穿一只过膝袜（另一条腿裸露），**不表示“穿了一双但其中一只滑落”**。
- **`uneven legwear`**：表示左右腿袜子高度或款式不同；若要表达“一侧袜子滑落到小腿”，建议配合短句：`One sock has slipped down to her calf while the other stays pulled up.`
- **`dress` / `gown` / `robe` / `kimono`**：剪裁与文化语境不同，不可随意混作近义词替换。
- **`sheer` / `translucent` / `transparent`**：透明度递增；使用时必须指明**哪一层、哪一个部件**半透明（如 `sheer black organza sleeves`），避免整件衣服被画成全透明。
- **`print` / `embroidery` / `applique` / `lace trim` / `frill`**：分属印花、刺绣、贴布绣、蕾丝滚边和荷叶边，排错时注意区分平面图案与立体边缘工艺。

### 6.2 实图迭代排错顺序
对照生成图与已定设计，已经画对的部位保持不动，每轮优先按以下顺序修正一个失败层级：
1. **检查主体归属**：颜色和材质是否紧贴所修饰的部件？
2. **删除冲突词**：同一部位是否同时写了两个主名词或冲突长度？
3. **复杂关系改短句**：内外层颠倒、单侧滑落、持握位置不对时，用部件作主语写清空间关系。
4. **调整顺序**：将核心轮廓和最醒目的外层部件提前。
5. **最后小幅加权**：仅对仍被吞掉的关键结构做局部 `{...}` 加权。
