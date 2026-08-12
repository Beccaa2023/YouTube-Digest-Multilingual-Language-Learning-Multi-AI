# YouTube Digest — Multilingual & Multi-AI
[English](https://github.com/Beccaa2023/YouTube-Digest-Multilingual-Language-Learning-Multi-AI/edit/main/README.md) | [简体中文](https://github.com/Beccaa2023/YouTube-Digest-Multilingual-Language-Learning-Multi-AI/edit/main/README.zh-CN.md)

A Chrome extension for turning YouTube videos into multilingual learning and reading resources.

YouTube Digest provides transcript retrieval, translation, bilingual reading, AI-powered video analysis, and timestamped notes. It supports multiple source and target languages and multiple AI providers.

## Features

### Multilingual subtitles

- Automatically detects the video's original subtitle language when possible.
- Supports native subtitle tracks in any language available through the configured transcript provider.
- Source languages are not limited to English, Chinese, or Portuguese.
- Users can manually select another available subtitle language.

### Many-to-many translation

Translation is designed as a many-to-many system:

```text
Any supported source language
            ↓
      Selected target language
```

For example:

- Portuguese → Chinese
- Portuguese → English
- English → Portuguese
- Chinese → English
- Spanish → Portuguese
- Japanese → Chinese

The actual available source languages depend on the subtitle tracks available for the video.

### Preferred languages

Users can configure multiple preferred languages.

A default language is used when the extension initializes, but it does not restrict the user to that language.

For example:

```text
Preferred languages
├── Chinese (Simplified)  ← Default
├── English
└── Portuguese
```

This allows the same user to use Chinese as their default reading language while also switching to English or Portuguese when learning languages.

### Transcript reading modes

The transcript interface provides three modes:

- **Original** — display the original transcript.
- **Translation** — display the selected translation.
- **Bilingual** — display the original and translation together.

### Multi-AI providers

YouTube Digest supports multiple AI providers.

Currently supported providers include:

- DeepSeek
- OpenAI

The provider and model can be configured in Settings.

The extension uses a Bring Your Own Key (BYOK) model. Users provide their own API keys.

AI features can be used for:

- Video overview
- Chapter generation
- Key quotes
- Selected-text explanations
- Translation
- Note processing

### Timestamped notes

Users can create notes associated with timestamps in the video.

## Language System

The extension separates source languages and target languages.

### Source language

The source language is the language of the transcript being processed.

When set to `Auto`, the extension attempts to identify the video's original/native subtitle language.

If multiple subtitle tracks are available, users can select another available source language manually.

### Target language

The target language is the language used for translation.

Users can configure multiple preferred target languages and select the language they want to use for a particular video.

### Default language

The default language controls the initial language used by the extension.

It is an initialization preference, not a permanent user language setting.

For example:

```text
Default: Chinese (Simplified)

Other preferred languages:
- English
- Portuguese
```

The user can switch between them whenever needed.

## AI Providers

### DeepSeek

DeepSeek can be configured as an AI provider for translation and analysis features.

### OpenAI

OpenAI can also be configured as an AI provider.

The API endpoint and model configuration should match the selected provider.

### API Keys

YouTube Digest follows a Bring Your Own Key model.

You provide your own API keys for the services you use.

The extension does not provide AI credits or operate a shared AI proxy.

Use the Settings page to configure and test your API connections.

## Transcript Provider

YouTube Digest currently uses Supadata to retrieve YouTube transcripts.

The extension requests native subtitle content rather than automatically falling back to AI speech transcription.

Therefore, a video must have an available native subtitle track supported by the configured transcript provider.

The actual languages available for a particular video depend on the subtitle tracks provided by YouTube and the transcript service.

## Installation

### 1. Download the extension

Download the latest release from this repository.

### 2. Extract the ZIP file

Extract the downloaded archive to a local folder.

### 3. Open Chrome Extensions

Open:

```text
chrome://extensions
```

### 4. Enable Developer mode

Enable **Developer mode** in the upper-right corner.

### 5. Load the extension

Click **Load unpacked** and select the extracted folder containing:

```text
manifest.json
```

### 6. Configure the extension

Open YouTube Digest Settings and configure:

- Supadata API key
- AI provider
- AI model
- AI provider API key
- Preferred languages
- Default language

## Usage

1. Open a YouTube video.
2. Open YouTube Digest from the Chrome toolbar.
3. Select or confirm the source subtitle language.
4. Select the desired target language.
5. Choose one of:
   - Original
   - Translation
   - Bilingual
6. Use the AI analysis features when needed.
7. Add timestamped notes while watching.

## Privacy

YouTube Digest does not require a YouTube Digest account.

API keys are stored locally in the browser extension storage.

The extension does not use advertising, analytics, or telemetry for its own service.

Transcript and AI requests are sent directly to the corresponding third-party service configured by the user.

Users should review the privacy policies of Supadata and their selected AI provider before using the extension.

See [PRIVACY.md](PRIVACY.md) for more information.

## Limitations

### Subtitle availability

The extension depends on native YouTube subtitle tracks available through the transcript provider.

If a video has no suitable native subtitle track, the extension may not be able to retrieve a transcript.

### Language availability

The extension is designed to work with languages beyond English, Chinese, and Portuguese.

However, available languages depend on the subtitle tracks provided for the individual video and the capabilities of the transcript provider.

### AI provider availability

AI features require a valid API key for the selected provider.

Different providers may support different models, parameters, limits, and response formats.

## Development

This project is based on the original YouTube Digest project by [zarazhangrui](https://github.com/zarazhangrui/youtube-digest).

This repository maintains the multilingual and multi-AI development branch.

### Run tests

```bash
npm test
```

### Check the project

```bash
npm run check
```

### Package the extension

```bash
npm run package
```

## Project Structure

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

## Version

Current release:

```text
v1.2
```

This version introduces:

- Multilingual source and target language support
- Configurable preferred languages
- Default language initialization
- Original / Translation / Bilingual reading modes
- Multiple AI providers
- DeepSeek support
- OpenAI support
- Improved translation workflow
- AI provider connection testing

## License

See [LICENSE](LICENSE) for license information.

## Security

Please see [SECURITY.md](SECURITY.md) for information about reporting security issues.
