# YouTube Digest — 多语言与多 AI

一个用于将 YouTube 视频转换为多语言学习与阅读资源的 Chrome 扩展。

YouTube Digest 提供字幕获取、翻译、双语阅读、AI 视频分析以及带时间戳的笔记功能。支持多种源语言、目标语言以及多个 AI 服务商。

## 功能

### 多语言字幕

- 尽可能自动识别视频的原始字幕语言。
- 支持字幕服务提供的视频原生字幕语言。
- 源语言不限于英语、中文或葡萄牙语。
- 用户可以手动选择视频提供的其他字幕语言。

### 多对多翻译

翻译采用多对多语言设计：

```text
任意支持的源语言
        ↓
   用户选择的目标语言
```

例如：

- 葡萄牙语 → 中文
- 葡萄牙语 → 英语
- 英语 → 葡萄牙语
- 中文 → 英语
- 西班牙语 → 葡萄牙语
- 日语 → 中文

实际可用的源语言取决于视频提供的字幕语言。

### 首选语言

用户可以配置多个首选语言。

其中一个语言可以设为默认语言，用于扩展初始化时的默认选择，但这并不意味着用户只能使用这一种语言。

例如：

```text
首选语言
├── 简体中文  ← 默认
├── English
└── Português
```

这样，同一个用户可以以中文作为默认阅读语言，同时在需要时切换到英语或葡萄牙语进行学习。

### 字幕阅读模式

字幕界面提供三种模式：

- **Original** — 显示原始字幕。
- **Translation** — 显示所选目标语言的翻译。
- **Bilingual** — 同时显示原文和翻译。

### 多 AI 服务商

YouTube Digest 支持多个 AI 服务商。

目前支持：

- DeepSeek
- OpenAI

用户可以在 Settings 中选择 AI 服务商和模型。

扩展采用 BYOK（Bring Your Own Key）模式，用户使用自己的 API Key。

AI 功能包括：

- 视频概览
- 视频章节
- 关键引用
- 选中文本解释
- 翻译
- 笔记处理

### 时间戳笔记

用户可以为视频中的特定时间点创建笔记。

这样可以在学习或复习时快速返回对应的视频位置。

## 语言系统

扩展将源语言和目标语言分开处理。

### 源语言

源语言是当前字幕的语言。

选择 `Auto` 时，扩展会尽可能识别视频的原始/原生字幕语言。

如果视频提供多个字幕语言，用户也可以手动选择其他可用的源语言。

### 目标语言

目标语言是翻译所使用的语言。

用户可以配置多个首选目标语言，并针对具体视频选择需要使用的语言。

### 默认语言

默认语言决定扩展初始化时优先使用的语言。

它只是初始化偏好，而不是永久的用户语言设置。

例如：

```text
默认语言：简体中文

其他首选语言：
- English
- Português
```

用户可以根据需要随时切换。

## AI 服务商

### DeepSeek

可以将 DeepSeek 配置为 AI 服务商，用于翻译和视频分析等功能。

### OpenAI

也可以使用 OpenAI 作为 AI 服务商。

API Endpoint 和模型配置需要与所选择的服务商相匹配。

### API Key

YouTube Digest 采用 BYOK（Bring Your Own Key）模式。

用户使用自己的 API Key。

扩展不提供 AI 使用额度，也不运行共享的 AI 代理服务。

可以在 Settings 中配置并测试 API 连接。

## 字幕服务

YouTube Digest 使用 Supadata 获取 YouTube 字幕。

扩展请求的是原生字幕，而不是自动回退到 AI 语音转录。

因此，视频需要存在字幕服务能够获取的原生字幕轨道。

具体视频能够使用哪些语言，取决于 YouTube 提供的字幕以及字幕服务的支持情况。

## 安装

### 1. 下载扩展

从本仓库下载最新版本。

### 2. 解压 ZIP 文件

将下载的 ZIP 文件解压到本地文件夹。

### 3. 打开 Chrome 扩展页面

打开：

```text
chrome://extensions
```

### 4. 开启开发者模式

打开右上角的 **Developer mode（开发者模式）**。

### 5. 加载扩展

点击 **Load unpacked（加载已解压的扩展）**，选择包含以下文件的文件夹：

```text
manifest.json
```

### 6. 配置扩展

打开 YouTube Digest Settings，并配置：

- Supadata API Key
- AI 服务商
- AI 模型
- AI 服务商 API Key
- 首选语言
- 默认语言

## 使用方法

1. 打开 YouTube 视频。
2. 从 Chrome 工具栏打开 YouTube Digest。
3. 确认或选择源字幕语言。
4. 选择目标语言。
5. 选择：
   - Original
   - Translation
   - Bilingual
6. 根据需要使用 AI 分析功能。
7. 观看视频时可以添加带时间戳的笔记。

## 隐私

YouTube Digest 不要求用户创建 YouTube Digest 账户。

API Key 存储在浏览器扩展的本地存储中。

扩展本身不使用广告、分析或遥测服务。

字幕和 AI 请求会直接发送到用户配置的相应第三方服务。

使用扩展前，请自行查看 Supadata 以及所选 AI 服务商的隐私政策。

更多信息请参阅 [PRIVACY.md](PRIVACY.md)。

## 限制

### 字幕可用性

扩展依赖字幕服务能够获取的 YouTube 原生字幕。

如果视频没有合适的原生字幕轨道，扩展可能无法获取字幕。

### 语言可用性

扩展设计上并不限制英语、中文或葡萄牙语，可以处理其他语言。

但是，具体可用语言取决于每个视频提供的字幕以及字幕服务的能力。

### AI 服务商

AI 功能需要所选服务商的有效 API Key。

不同 AI 服务商可能支持不同的模型、参数、使用限制和响应格式。

## 开发

本项目基于 [zarazhangrui](https://github.com/zarazhangrui/youtube-digest) 的原始 YouTube Digest 项目开发。

本仓库主要维护多语言和多 AI 功能的开发版本。

### 运行测试

```bash
npm test
```

### 检查项目

```bash
npm run check
```

### 打包扩展

```bash
npm run package
```

## 项目结构

```text
.
├── background.js
├── content.js
├── manifest.json
├── options.html
├── options.js
├── options.css
├── settings.js
├── sidepanel.html
├── sidepanel.js
├── sidepanel.css
├── prompts/
│   └── translation.md
└── tests/
```

## 版本

当前版本：

```text
v1.2
```

本版本主要加入：

- 多语言源语言与目标语言支持
- 可配置的首选语言
- 默认语言初始化
- Original / Translation / Bilingual 阅读模式
- 多 AI 服务商支持
- DeepSeek 支持
- OpenAI 支持
- 改进的翻译流程
- AI 服务商连接测试

## License

许可证信息请参阅 [LICENSE](LICENSE)。

## Security

安全问题请参阅 [SECURITY.md](SECURITY.md)。
