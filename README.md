# NovelAI V5 构思与写法 · 合并版（构思／写法两卷） · v1.2e-nightly

本分支提供一个入口与构思、写法两卷，包含全部通用方法。主要维护形式是 [`main` 的拆分版](https://github.com/Miint-Sunny/nai5-prompting/tree/main)，本分支由相同方法源自动生成。

## 安装与开始使用

以下步骤适用于支持 Skill 安装、附件读取和文件管理的 agent。

1. [下载合并版（构思／写法两卷）安装包](downloads/nai5-merged-v1.2e.zip)。
2. 将 ZIP 拖入 agent 对话，请它将压缩包中的完整 `nai5-prompting` 技能安装到当前环境，保留全部目录和资源，并确认可被识别和调用。
3. 安装完成后，直接描述任务。agent 根据请求读取相关章节；如果客户端要求刷新或重启，按其提示完成。

**完整安装，按需读取。** 本形式包含一个完整技能，无需另外安装拆分版的 11 个技能。`SKILL.md` 是 agent 读取方法的入口文件，安装由 agent 处理，无需双击运行。

默认拆分版的安装请求和 11 项职责清单见 [主线使用说明](https://github.com/Miint-Sunny/nai5-prompting#quick-start)。

## 阅读与切换

- [技能入口](SKILL.md)；正文：[构思卷](references/通用构思.md) · [写法卷](references/通用写法.md)。
- [拆分版](https://github.com/Miint-Sunny/nai5-prompting/tree/main) · [合并版](https://github.com/Miint-Sunny/nai5-prompting/tree/merged) · [单文件版](https://github.com/Miint-Sunny/nai5-prompting/tree/single)。三种形式选择一种安装。

合并版与单文件版均使用 `nai5-prompting` 名称，切换时替换同名技能。与拆分版切换时，停用原形式，避免同时加载两份相同方法。

已有构思、方案或定稿时，直接进入对应阶段；仅请求构思时交付方案，请求提示词时进入写法。普通任务使用当前技能正文和用户提供的资料；历史作品与维护记录仅在明确要求核对、分析或制作变体时读取。本分支不包含个人或群偏好。

本项目提供方案和提示词。生成图片时，将最终提示词用于 NovelAI；自动填写或生图需要环境另行提供相应工具。

## 版本与维护

当前为 **v1.2e-nightly（2026-10-09）**，方法快照为 `v1.2-next-preview.11-20261009`。本次说明修订不改变已发布的技能正文和安装包。三个附件集中在 [v1.2e Release](https://github.com/Miint-Sunny/nai5-prompting/releases/tag/v1.2e)，稳定 Latest 为 v1.1。

[发布说明](RELEASE_NOTES.md)记录修订和实际验证范围；[主线与版本](BRANCHES.md)说明分支关系；[来源](SOURCE.json)与[校验清单](SHA256SUMS.txt)用于核对本分支文件。本轮说明修订未新增模型测试、生图或客户端导入测试。

Copyright (C) 2026 [Miint-Sunny](https://github.com/Miint-Sunny)。完整 [LICENSE](LICENSE) 与 [NOTICE](NOTICE) 随包保留，项目贡献按 GNU GPL version 3（GPL-3.0-only）提供。
