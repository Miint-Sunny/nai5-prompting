# Gemini 适配版维护说明（`gemini/nai5-art-studio`）

本目录维护面向 **Gemini Apps（`gemini.google.com`）** 的 NovelAI Diffusion V5 提示词与画面创作技能适配版，工作分支为独立分支 `gemini`（不影响 `main`、`merged`、`single`、`mini`、`develop` 等现有版本分支，也不改动根目录通用 `skills/`）。

发布时 Gemini 有两版：常规版 `nai5-gemini-v<版本>.zip` 每次发版从通用拆分版自动封装（技能名 `nai5-art-studio`，内容和通用版相同）；本目录是防拦截版 `nai5-gemini-safe-<版本>.zip`（技能名 `nai5-art-studio-safe`），两版可以同时装。

---

## 一、适配基线与版本追踪

后续上游 `skills/` 更新时，直接以本节记录的基线提交对比差异（`git diff <baseline_commit>..main -- skills/`），增量同步至 `gemini/nai5-art-studio/`。

| 追踪项 | 当前记录值 |
| --- | --- |
| **适配目标平台** | Gemini Apps（`gemini.google.com` 网页端与客户端 Skills） |
| **依据的通用版版本** | `v1.2.7`（见根目录 [`SOURCE.json`](../SOURCE.json)） |
| **依据的公开仓 `main` 提交** | `8cedae6ff12ffa378f621f56bbb5d3cb7809e12d`（`chore: add Gemini 1.2.5 adaptation download`；其中 `skills/` 与 v1.2.7 标签相同） |
| **对应的 `v1.2.7` 标签提交** | `1285cb02226a4b3c4f7637832fe32e81f3e5b57a`（`Release v1.2.7: write action prefixes only when people interact`） |
| **上游方法仓 `source_commit`** | `eac1c293e1cf82d53766f8028f121a3a85c7ea29`（`2026-10-30T18:02:05+08:00`） |
| **首轮适配原则** | 仅以 `skills/` 通用拆分版 v1.2.7（11 个技能）为唯一内容基线独立重写，未读取或参考 `packs/v1.2.7/nai5-art-studio-gemini*` 或 `gemini/archive/*` 中的既有包 |

---

## 二、目录结构与交付物

```text
gemini/
├── PROMPT.md                           # 长期维护指令与适配原则
├── README.md                           # 本文件：基线记录、模块映射、导入与维护说明
├── VERIFICATION.md                     # 验证记录：session-595e368e 排查报告、链接检查与 5 组文字试用
├── UPSTREAM_ISSUES.md                  # 通用版 skills/ v1.2.7 发现的问题清单（供上游单独处理）
├── .gitignore                          # 本地打的 ZIP 和 archive/ 不进分支
└── nai5-art-studio/                    # Gemini 适配版技能源码目录
    ├── SKILL.md                        # 主入口：阶段判断、按需读取路由、核心契约与安全可用性规则
    ├── LICENSE.txt                     # GPL-3.0-only 许可全文
    ├── NOTICE.txt                      # 版权与第三方材料归属说明（含 Elowwwen MIT 致谢）
    └── references/
        ├── ideas-and-art.md            # 主题构思、单张叙事、色彩与画风选择
        ├── scene-and-composition.md    # 场景空间设计、构图、机位与动作阶段
        ├── character-and-costume-design.md # OC 角色核心、服装衣橱设计与真实背景考据
        ├── comic-storyboard.md         # 漫画故事导演、页格版式、连续性与三部分文字分镜
        ├── writing-core.md             # NAI V5 核心语法、字段分工、质量词/UC 与精确局改契约
        ├── writing-illustration.md     # 单人/多人插画完整模板、局部主串模式与 source#/target#/mutual#
        ├── writing-costume.md          # 已定服装转提示词片段、FASHIONPEDIA/Danbooru 核对与排错
        ├── writing-comic.md            # 整页/分组漫画提示词编译、按格分框、色彩转换与 2×2 默认四格
        ├── reverse-prompt.md           # 照图反推提示词、三种来源标注与视觉落点判断
        └── sources.md                  # 官方文档依据（N1–N8）、教程出处与实图反馈汇总
```

---

## 三、通用版 11 个拆分技能到 Gemini 版的映射关系

Gemini Apps 采用「单技能包（Single `SKILL.md` + `references/`）」导入机制。为避免单次任务读取过多无关规则导致上下文膨胀或触发安全误判，本适配版将通用版 11 个技能（共 38 个 Markdown 文件、约 308 KB）整合重构为 **1 个精简路由入口 + 10 个按任务职责解耦的参考文件（共 108 KB）**：

| 通用版 `skills/` (v1.2.7) | Gemini 适配版 `gemini/nai5-art-studio/` | 适配与解耦调整说明 |
| --- | --- | --- |
| `nai5-ideas` + `nai5-art-style` | [`references/ideas-and-art.md`](nai5-art-studio/references/ideas-and-art.md) | 合并构思选向、单张视觉叙事与色彩/光影/画风演进；删除无实际指导作用的口号与容易引发内容安全误判的敏感词举例 |
| `nai5-scene-design` + `nai5-illustration-composition` | [`references/scene-and-composition.md`](nai5-art-studio/references/scene-and-composition.md) | 合并空间功能区、构图层次、动作阶段与多角色动势；将重复 3 份的 `background.md` 抽离合并至角色与服装设计 |
| `nai5-character-design` + `nai5-costume-design` (+ `background.md`) | [`references/character-and-costume-design.md`](nai5-art-studio/references/character-and-costume-design.md) | 合并 OC 角色设计、服装设计工具箱与时代/职业背景资料核对，统一幻想特征（兽耳/翅膀/尾巴不写衣物开洞）口径 |
| `nai5-comic-storyboard` | [`references/comic-storyboard.md`](nai5-art-studio/references/comic-storyboard.md) | 将 `story.md`、`layout.md`、`continuity.md` 整合为单文件，明确「三部分文字分镜审阅」与「跳过分镜直出提示词」两条路径 |
| `nai5-writing` (`conventions.md` 通用部分) | [`references/writing-core.md`](nai5-art-studio/references/writing-core.md) | 只保留所有写词任务共用的字段契约、行尾逗号规则、质量词/UC 预设冲突表、V5 权重/文字/透明语法与精确局改规则；**移出原混在 `conventions.md` 里的 70 行漫画专属黑白转换规则** |
| `nai5-writing` (`illustration.md`) | [`references/writing-illustration.md`](nai5-art-studio/references/writing-illustration.md) | 专注普通单人/多人插画；**新增「局部主串（只要动作与场景）」显式交付模板**；同步 v1.2.7 多人互动 `source#`/`target#`/`mutual#` 与非互动省略规则；修复上游句例自相矛盾的引号与句号问题；剔除高风险部位焦点词枚举 |
| `nai5-costume-writing` | [`references/writing-costume.md`](nai5-art-studio/references/writing-costume.md) | 保留服装片段单代码块交付、9 项视觉意图清单、FASHIONPEDIA + Danbooru 核对、部件作主语一次性定义与易错词排错 |
| `nai5-comic-writing` + `conventions.md` 漫画色彩节 | [`references/writing-comic.md`](nai5-art-studio/references/writing-comic.md) | 合并漫画提示词编译、按格分框规则、跨格可见子集、文字载体、**漫画专属色彩模式转换（全彩/半黑白/纯黑白）**与经典示例，普通插画任务不再被动加载漫画规则 |
| `nai5-reverse-prompt` | [`references/reverse-prompt.md`](nai5-art-studio/references/reverse-prompt.md) | 保留原文/用户给的/推测三来源区分、盲推对照流程、手掌/手背与俯仰角判断及 7 类不从画面硬推的边界 |
| 各包分散的 `sources.md` (共 10 份) | [`references/sources.md`](nai5-art-studio/references/sources.md) | 去重合并为单一来源索引，日常任务无需加载，仅在用户要求查证官方能力或方法出处时按需读取 |

---

## 四、针对 Gemini 平台与实测问题的关键优化

1. **按需单跳加载，降低单次任务上下文体积约 70%**：
   - 在通用版中，写一条普通单人插画提示词往往会加载 `conventions.md` (43.1 KB) + `illustration.md` (72.5 KB) + `scene.md` + `composition.md` = **131.7 KB**。
   - 在本适配版中，[`SKILL.md`](nai5-art-studio/SKILL.md) 明确规定**每次只读与当次任务直接对应的 1～2 个参考文件**。写普通插画只需读取 `SKILL.md` (8.7 KB) + `writing-core.md` (12.5 KB) + `writing-illustration.md` (13.7 KB) = **34.9 KB**，彻底避免漫画规则、灰阶转换与大段重复口号污染上下文。
2. **四层防 `PROHIBITED_CONTENT` 护栏（来自 `session-595e368e` 实测复盘）**：
   - **第一层（标签槽与自然语言句主语分离）**：`1girl` / `girl` 仅限用于 Danbooru 标签位；**所有英文自然语言句子统一以 `The character`、`The figure`、`a woman`、`she`（多人用 `The character on the left`）作主语**，不在描写姿态、躺卧、身体接触或衣物的自然语言长句里使用 `The girl` / `a young girl`，从源头避免英文自然语言安全分类器对未成年人词汇的误判。
   - **第二层（清理参考文档中的非必要敏感词枚举）**：剔除了上游参考文档中无需出现即可讲清语法的部位焦点标签枚举（原 `illustration.md` §3.6 中的 `ass focus`、`breast focus`、`navel focus`、`thigh focus`、`armpit focus` 及 `ideas.md` 中的敏感分级词）。
   - **第三层（躺卧/睡姿的「几何支撑」写法与服装「制版裁片」写法）**：在 [`SKILL.md`](nai5-art-studio/SKILL.md) 与 [`writing-illustration.md`](nai5-art-studio/references/writing-illustration.md) 中规定：写躺卧、慵懒、贴身或睡姿时，用外在轮廓、骨骼重心支撑（`arm support, head rest`）与自然光影表达，用户未明确点名时**不主动叠加 `parted lips`、`half-closed eyes`、`sweat`、`heavy breathing`**，也不将肢体陷入柔软织物、手抚脸颊/躯干/臀胯等细节串联成感官特写句；服装与腿饰统一以裁片结构本身作主语。
   - **第四层（思考链零敏感词复述）**：要求内部思考（Thinking）直接聚焦构图几何、支撑点与标签装配，不在思考过程中自我盘问“是否涉黄/擦边/违规”或枚举负面敏感词。
3. **补齐「局部主串（只要动作与场景）」契约**：
   - 针对用户已有角色栏、要求“只要动作和场景，不用写 UC 和质量词，单人”的高频场景，在 [`writing-core.md`](nai5-art-studio/references/writing-core.md) 与 [`writing-illustration.md`](nai5-art-studio/references/writing-illustration.md) 中专门定义了局部主串模板：只输出一个 `Base Prompt:` 代码块，允许保留与动作联动的可变物种特征（如 `drooping rabbit ears`），不锁死发色/瞳色/固定服装，也不强塞空的 `Character 1:` 栏。

---

## 五、在 Gemini Apps（`gemini.google.com`）中导入与使用

1. 打开 [`gemini.google.com/skills`](https://gemini.google.com/skills)（或左侧菜单 **Skills** → **+** 创建/导入技能）。
2. 从 [Releases](https://github.com/Miint-Sunny/nai5-prompting/releases) 下载防拦截版 `nai5-gemini-safe-<版本>.zip` 上传，或者直接选择本目录的 `nai5-art-studio/` 文件夹上传。
   - 官方要求 `SKILL.md` 放在上传内容的最外层，隐藏文件可能让上传失败（[帮助页](https://support.google.com/gemini/answer/17094296)）。发布用的 ZIP 由维护者从本目录打包：不套外层文件夹、不带隐藏文件，许可文件带 `.txt` 扩展名；技能名 `nai5-art-studio-safe`，可以和常规版 `nai5-art-studio` 同时装。
3. 保存并开启技能后，即可在对话中直接处理：
   - 画面点子、场景构图、OC 角色与服装设计、四格/多格漫画分镜；
   - 单人/多人插画提示词、局部动作与场景主串、服装提示词片段、整页/分组漫画提示词、照图反推与局部精确改词。

---

## 六、后续上游版本升级维护流程

当仓库 `main` 分支的 `skills/` 更新到新版本（例如 `v1.2.8` 或 `v1.3.0`）时：

1. 查看根目录 `SOURCE.json` 与 `RELEASE_NOTES.md`，确认新版本号与提交哈希。
2. 运行差异对比：
   ```bash
   git diff 8cedae6ff12ffa378f621f56bbb5d3cb7809e12d..<new_main_commit> -- skills/
   ```
3. 按本文第三节的模块映射表，将上游新增或修订的规则同步到 `gemini/nai5-art-studio/` 对应的参考文件中。
4. 运行链接与锚点校验脚本，更新 [`VERIFICATION.md`](VERIFICATION.md) 中的验证记录与本文件中的基线提交哈希，发布用的 ZIP 由维护者用方法仓的 `pack_gemini_safe.py` 从本目录打包（`SKILL.md` 在最外层）。

---

## 七、本地文件

本地还留着 `archive/`（旧 1.2.5 包副本，未作为本轮改写参考）、通用拆分版 v1.2.7 ZIP 和本地打的 ZIP，供对照，不进分支（见 `.gitignore`）。
