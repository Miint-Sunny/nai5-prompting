# NovelAI V5 构思与写法 · 单文件版 · v1.2e-nightly

本分支提供一个入口与完整合订稿，包含全部通用方法。主要维护形式是 [`main` 的拆分版](https://github.com/Miint-Sunny/nai5-prompting/tree/main)，本分支由相同方法源自动生成。

<a id="quick-start"></a>

## 配置与开始使用

本项目提供技能文档和参考资料，配置只需放置完整技能目录，无需构建或安装项目依赖。

**未指定形式时，默认配置全部 11 个拆分技能，使用时优先从拆分技能中按需读取。** 本分支的单文件版仅在用户明确指定时配置或调用。

推荐把[项目地址](https://github.com/Miint-Sunny/nai5-prompting)发给 agent，请它按照 [INSTALL.md](INSTALL.md)完成配置。用户明确选择本形式时，可发送：

```text
请按照项目中的 INSTALL.md，为当前 agent 配置单文件版：
https://github.com/Miint-Sunny/nai5-prompting/tree/single

保留完整技能目录和资源，完成后告知配置位置和可用状态。
```

备用方式：下载[本形式的完整包](packs/v1.2e/nai5-single-v1.2e.zip)，交给 agent 配置；或解压后，将完整 `nai5-prompting` 文件夹复制到[客户端技能目录](INSTALL.md#manual-paths)。配置完成后直接描述任务，如客户端提示刷新或重启，按其提示完成。

`SKILL.md` 是供 agent 读取的入口文档，无需双击运行。默认拆分版的说明和 11 项职责清单见[主线使用说明](https://github.com/Miint-Sunny/nai5-prompting#quick-start)。

## 阅读与切换

三种当前安装包均集中在 `packs/v1.2e/`：[拆分版](packs/v1.2e/nai5-split-v1.2e.zip) · [合并版](packs/v1.2e/nai5-merged-v1.2e.zip) · [单文件版](packs/v1.2e/nai5-single-v1.2e.zip)。历史版本从 [Releases](https://github.com/Miint-Sunny/nai5-prompting/releases) 获取。

- [技能入口](SKILL.md)；正文：[完整构思与写法](references/NAI5_All_Prompting.md)。
- [拆分版](https://github.com/Miint-Sunny/nai5-prompting/tree/main) · [合并版](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) · [单文件版](https://github.com/Miint-Sunny/nai5-prompting/tree/single)。默认使用拆分版，另外两种形式按用户明确选择使用。

合并版与单文件版均使用 `nai5-prompting` 名称。明确切换时先核对已有配置，避免重复读取；已同时配置多种形式时，普通任务仍优先使用拆分技能。

已有构思、方案或定稿时，直接进入对应阶段；仅请求构思时交付方案，请求提示词时进入写法。普通任务使用当前技能正文和用户提供的资料；历史作品与维护记录仅在明确要求核对、分析或制作变体时读取。本分支不包含个人或群偏好。

本项目提供方案和提示词。生成图片时，将最终提示词用于 NovelAI；自动填写或生图需要环境另行提供相应工具。

## 版本与维护

当前为 **v1.2e-nightly（2026-10-09）**，方法快照为 `v1.2-next-preview.11-20261009`。本次说明修订不改变已发布的技能正文和安装包。三个附件集中在 [v1.2e Release](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2e)，稳定 Latest 为 v1.1。

[发布说明](RELEASE_NOTES.md)记录修订和实际验证范围；[主线与版本](BRANCHES.md)说明分支关系；[来源](SOURCE.json)与[校验清单](SHA256SUMS.txt)用于核对本分支文件。本轮说明修订未新增模型测试、生图或客户端导入测试。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE) 随包保留，项目贡献按 GNU GPL version 3（GPL-3.0-only）提供。
