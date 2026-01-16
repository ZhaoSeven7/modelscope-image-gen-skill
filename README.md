# 🎨 Claude AI Image Generator

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude](https://img.shields.io/badge/Claude-Skills-blue.svg)](https://claude.ai/)

---

**[English](#english) | [中文](#中文)**

<a name="english"></a>

## ✨ Features

Generate AI images directly in Claude using ModelScope's **Z-Image-Turbo** model.

- ⚡ **Fast** - Generate images in 10-30 seconds
- 🎨 **High Quality** - Professional-grade results
- 🌏 **Bilingual** - Supports English & Chinese
- 💡 **Easy** - Only 3 steps to set up

## 🚀 Quick Start

### 1. Get API Key

Visit [ModelScope](https://www.modelscope.cn/), sign up (free), and get your API token from [here](https://www.modelscope.cn/my/myaccesstoken).

### 2. Install Skill

**For Claude Code**:
```bash
cp -r skill ~/.claude/skills/modelscope-image-gen
```

**For Claude.ai**:
Settings → Skills → Upload Custom Skill → Select `skill` folder → Upload

### 3. Configure

Create `config.json` in the skill folder:
```json
{
  "api_key": "your-api-key-here"
}
```

## 💡 Usage

Just describe what you want:

```
Generate a picture of a golden cat
```

Or more detailed:

```
Create a cyberpunk city at night,
neon lights, rain, highly detailed,
photorealistic, 8K
```

Chinese also works:

```
生成一张金色的猫的图片
```

## 📁 Project Structure

```
modelscope-image-gen-skill/
├── skill/
│   ├── SKILL.md              # Claude skill definition
│   └── config.example.json   # Config template
├── README.md                 # This file
├── LICENSE
└── .gitignore
```

## 🖼️ Example

**Prompt**: "A cute robotic cat, cyberpunk style, holographic screens, highly detailed"

```
┌─────────────────────────────────┐
│  [Image Generated in ~19 sec]   │
│  Size: 929 KB                    │
│  Model: Z-Image-Turbo           │
└─────────────────────────────────┘
```

*Generated in ~19 seconds | 929 KB*

> 💡 **Note**: When using this skill locally, actual generated images will be saved to your vault. The example above demonstrates the generation speed and quality.

## ⚙️ Configuration

`config.json` options:
```json
{
  "api_key": "required",
  "output_dir": "./generated-images",  // optional
  "timeout": 60                         // optional
}
```

## 🔧 Troubleshooting

**"API Key Not Configured"**
→ Create `config.json` with your API key

**"Image Generation Failed"**
→ Check:
- API key is valid at [ModelScope](https://www.modelscope.cn/my/myaccesstoken)
- Internet connection is stable
- Prompt follows content guidelines

## 📚 Resources

- [ModelScope](https://www.modelscope.cn/)
- [Get API Key](https://www.modelscope.cn/my/myaccesstoken)
- [Z-Image-Turbo Model](https://www.modelscope.cn/models/Tongyi-MAI/Z-Image-Turbo)

## 📄 License

MIT License - Free to use and modify

---

<a name="中文"></a>

## ✨ 功能特性

直接在 Claude 中使用 ModelScope 的 **Z-Image-Turbo** 模型生成 AI 图像。

- ⚡ **快速** - 10-30 秒生成图像
- 🎨 **高质量** - 专业级效果
- 🌏 **双语** - 支持中英文
- 💡 **简单** - 仅需 3 步配置

## 🚀 快速开始

### 1. 获取 API 密钥

访问 [ModelScope](https://www.modelscope.cn/)，注册（免费），从[这里](https://www.modelscope.cn/my/myaccesstoken)获取 API 令牌。

### 2. 安装技能

**Claude Code**:
```bash
cp -r skill ~/.claude/skills/modelscope-image-gen
```

**Claude.ai**:
设置 → 技能 → 上传自定义技能 → 选择 `skill` 文件夹 → 上传

### 3. 配置

在技能文件夹中创建 `config.json`：
```json
{
  "api_key": "你的-api-密钥"
}
```

## 💡 使用方法

只需描述你想要的内容：

```
生成一张金色的猫的图片
```

或更详细：

```
创建一个赛博朋克夜景城市，
霓虹灯，下雨，高度详细，
写实风格，8K
```

英文也可以：

```
Generate a picture of a golden cat
```

## 📁 项目结构

```
modelscope-image-gen-skill/
├── skill/
│   ├── SKILL.md              # Claude 技能定义
│   └── config.example.json   # 配置模板
├── README.md                 # 本文件
├── LICENSE
└── .gitignore
```

## 🖼️ 示例

**提示词**："A cute robotic cat, cyberpunk style, holographic screens, highly detailed"

```
┌─────────────────────────────────┐
│   [图片约 19 秒生成]            │
│   大小: 929 KB                   │
│   模型: Z-Image-Turbo           │
└─────────────────────────────────┘
```

*约 19 秒生成 | 929 KB*

> 💡 **提示**：本地使用此技能时，实际生成的图像会保存到您的 vault 中。上图仅用于展示生成速度和质量。

## ⚙️ 配置选项

`config.json` 选项：
```json
{
  "api_key": "必填",
  "output_dir": "./generated-images",  // 可选
  "timeout": 60                         // 可选
}
```

## 🔧 故障排除

**"API 密钥未配置"**
→ 创建包含 API 密钥的 `config.json`

**"图像生成失败"**
→ 检查：
- API 密钥在 [ModelScope](https://www.modelscope.cn/my/myaccesstoken) 是否有效
- 网络连接是否稳定
- 提示词是否符合内容规范

## 📚 相关资源

- [ModelScope 官网](https://www.modelscope.cn/)
- [获取 API 密钥](https://www.modelscope.cn/my/myaccesstoken)
- [Z-Image-Turbo 模型](https://www.modelscope.cn/models/Tongyi-MAI/Z-Image-Turbo)

## 📄 许可证

MIT 许可证 - 可自由使用和修改

---

**Version**: 1.0.0 | **Last Updated**: 2026-01-16

[**⬆️ Back to Top**](#-claude-ai-image-generator)

**Happy Image Generating! 🎨**
