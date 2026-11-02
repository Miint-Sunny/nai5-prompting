# 技能包下载

推荐将[项目地址](https://github.com/Miint-Sunny/nai5-prompting)发给 agent，请它按照[配置指南](../INSTALL.md)完成配置。此目录提供手动下载的备用方式；技能文件无需构建或安装项目依赖。

## 当前版本：v1.2.8

用户未指定形式时，配置完整拆分版；使用时优先从拆分技能中按需读取。极简版、合并版和单文件版仅在用户明确指定时选择；strict 版给导入拆分版失败的环境（比如 Gemini 网页）；strict-safe 版（Gemini 防拦截）只在 Gemini 里被安全拦截时选择。

| 文件 | 内容 |
| --- | --- |
| **[nai5-split-v1.2.8.zip](v1.2.8/nai5-split-v1.2.8.zip)** | 全部 11 个拆分技能，默认选择 |
| [nai5-merged-v1.2.8.zip](v1.2.8/nai5-merged-v1.2.8.zip) | 一个入口与构思、写法两卷 |
| [nai5-single-v1.2.8.zip](v1.2.8/nai5-single-v1.2.8.zip) | 一个入口与完整合订稿 |
| [nai5-mini-v1.2.8.zip](v1.2.8/nai5-mini-v1.2.8.zip) | 极简版：一个技能 `nai5-mini`，只写普通单幅插画 |
| [nai5-strict-v1.2.8.zip](v1.2.8/nai5-strict-v1.2.8.zip) | strict 版：11 个技能合成一个技能 `nai5-art-studio`，正文和拆分版相同；导入拆分版失败或一次只能装一个技能时用（比如 Gemini 网页） |
| [nai5-strict-safe-v1.2.8.zip](v1.2.8/nai5-strict-safe-v1.2.8.zip) | strict-safe 版（Gemini 防拦截）：一个技能 `nai5-art-studio-safe`，Gemini 按通用版重写、已跟进 v1.2.8，strict 版在 Gemini 里被安全拦截时换用 |

下载后可将 ZIP 交给 agent 配置，或解压后按[手动配置目录](../INSTALL.md#manual-paths)放置。仅支持逐个导入的客户端，可使用 `v1.2.8/individual/` 中的 11 个小包；完整职责和下载清单见[主线说明](https://github.com/Miint-Sunny/nai5-prompting#split-skills)。

`packs/` 用于存放分发文件，`v1.2.8/` 是其下的版本目录。当前仓库仅保留当前版本的包，历史版本从 [Releases](https://github.com/Miint-Sunny/nai5-prompting/releases) 获取。

[返回使用说明](../README.md#quick-start)

旧的 Gemini 适配包（1.2、1.2.5）不再随新版提供：1.2 包在 v1.2 至 v1.2.6 的 [Release](https://github.com/Miint-Sunny/nai5-prompting/releases) 附件里，1.2.5 包在 v1.2.5 的附件里。
