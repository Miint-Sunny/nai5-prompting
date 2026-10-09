# NovelAI V5 构思与写法 · 合并版（构思／写法两卷） · v1.2e-nightly

这是 `merged` 分支，提供一个入口与构思、写法两卷；写法卷包括漫画、服装与照图反推等专项内容。 **主要维护版本是 [`main` 的拆分版](https://github.com/Miint-Sunny/nai5-prompting/tree/main)**；本分支由同一批方法源通过脚本生成，内容与拆分版同步。

## 下载与阅读

- [下载合并版（构思／写法两卷）](downloads/nai5-merged-v1.2e.zip)。
- [技能入口](SKILL.md)；正文：[构思卷](references/通用构思.md) · [写法卷](references/通用写法.md)。
- [拆分版（主要版本）](https://github.com/Miint-Sunny/nai5-prompting/tree/main) · [合并版](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) · [单文件版](https://github.com/Miint-Sunny/nai5-prompting/tree/single)。三种形式选择一种即可。

本版安装为 `nai5-prompting`。合并版与单文件版同名，导入另一种时替换；从拆分版切换时停用原拆分技能，避免重复启用。导入上方 ZIP，不使用 GitHub 自动生成的整个仓库源码 ZIP。

已有想法、方案或定稿时直接接续对应阶段；只要构思就交构思，需要提示词再进入写法。普通生成使用本包方法与当前资料，历史作品及维护记录只在用户明确要求核对、指定作品分析或变体任务时读取。本分支不含任何人的偏好。

## 来源与维护

修改拆分版使用的共同方法后，脚本同步生成本分支。本版为 **v1.2e-nightly（2026-10-09）**，三个安装包也集中在 [v1.2e Release](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2e)。方法快照为 `v1.2-next-preview.11-20261009`；本次修订完整写词、漫画逐框交付、服装限定词保留与照图反推的整理步骤。v1.1 仍是稳定 Latest。

[发布说明](RELEASE_NOTES.md)记录修订和实际验证范围；[主线与版本](BRANCHES.md)说明分支关系；[来源](SOURCE.json)和[校验清单](SHA256SUMS.txt)用于核对本分支文件。本轮新增 GPT-6-Luna / xhigh 通用拆分技能测试，含实际看图反推；未生图或做客户端实际导入。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE) 随包保留，项目贡献依 GNU GPL version 3（GPL-3.0-only）提供。
