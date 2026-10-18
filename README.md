# NovelAI V5 构思与写法 · 极简版 · v1.2

本分支提供一个技能 `nai5-mini`：两份正文、全是平常话，只管**普通单幅插画**的构思和写法。主要维护形式是 [`main` 的拆分版](https://github.com/Miint-Sunny/nai5-prompting/tree/main)；极简版是独立维护的第二顺位形式，不从拆分版生成，漫画、OC 设计、服装和照图反推请用拆分版。

<a id="quick-start"></a>

## 配置与开始使用

本项目提供技能文档，配置只需放置完整技能目录，无需构建或安装项目依赖。

**未指定形式时，默认配置全部 11 个拆分技能。** 想要一个短的、只写普通插画的技能时，再选本分支的极简版。

推荐把[项目地址](https://github.com/Miint-Sunny/nai5-prompting)发给 agent，请它按照 [INSTALL.md](INSTALL.md)完成配置。明确选择极简版时，可发送：

```text
请按照项目中的 INSTALL.md，为当前 agent 配置极简版（nai5-mini）：
https://github.com/Miint-Sunny/nai5-prompting/tree/mini

保留完整技能目录，完成后告知配置位置和可用状态。
```

备用方式：下载[本形式的完整包](packs/v1.2/nai5-mini-v1.2.zip)，交给 agent 配置；或解压后，将完整 `nai5-mini` 文件夹复制到[客户端技能目录](INSTALL.md#manual-paths)。

## 阅读与切换

- [技能入口](skills/nai5-mini/SKILL.md)；正文：[写法](skills/nai5-mini/references/写法.md)。
- 四种当前安装包均集中在 `packs/v1.2/`：[拆分版](packs/v1.2/nai5-split-v1.2.zip) · [合并版](packs/v1.2/nai5-merged-v1.2.zip) · [单文件版](packs/v1.2/nai5-single-v1.2.zip) · [极简版](packs/v1.2/nai5-mini-v1.2.zip)。
- [拆分版](https://github.com/Miint-Sunny/nai5-prompting/tree/main) · [合并版](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) · [单文件版](https://github.com/Miint-Sunny/nai5-prompting/tree/single) · [极简版](https://github.com/Miint-Sunny/nai5-prompting/tree/mini)。

极简版和拆分版可以同时配置。同时装着时，普通任务仍用拆分版，用户点名要极简版才用它；同一次任务只用其中一个。

## 版本与维护

当前为 **v1.2（2026-10-19）**，正式版，Latest 从 v1.1 更新到这里；四个附件集中在 [v1.2 Release](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2)。相对 v1.2g 加了三条真出图验过的规则：每个人的表情和视线写进自己的角色栏；只有一个人时，题目要的状态或动作在角色栏再写一两个词；版权角色说了穿哪类衣服就写两三件单品。正式版候选对 v1.2g 极简版同题出图 184 张（13 道二次元题各 3 份词、7 道真图题各 1 份，每份 2 个种子，每块三位模型评委盲评）：候选 10.25 对 9.63（满分 15），被评最好 39 次对 20 次，三位评委一致赢 9 题对 3 题。

极简版 2026-10-17 从零起草：先定标准（必须做到的事、写法上的硬要求、测过的坑），三路独立起草、三个模型评审、合成、挑错、修订，再按盲评点名的缺口补了四句。对照测试用 16 道二次元题、DeepSeek Flash 写词、16 题 × 3 位评委盲评（满分 50）：拆分版 36.45，极简版 37.33；极简版的语法字段与简洁最高，需求还原最低，写一份的输出 token 约为拆分版的一半。v1.2g 只验证了文字；v1.2 的三条规则各做了只差一处、4 个种子的真出图对照，再整版同题出图核过不退步，记录见发布说明。

改极简版时一次只加测出来缺的句子，加完同题重跑并盲评；语法事实以拆分版的 `nai5-writing` 为准。[发布说明](RELEASE_NOTES.md)记录修订与验证范围；[主线与版本](BRANCHES.md)说明分支关系；[来源](SOURCE.json)与[校验清单](SHA256SUMS.txt)用于核对本分支文件。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE) 随包保留，项目贡献按 GNU GPL version 3（GPL-3.0-only）提供。
