# 🎨 Claude AI Image Generator

[![[0d356e72fcfaae41be0d7adf6fad1c69_MD5.svg]]](LICENSE)
[![[a1720128ec364d402c5af22ed69b3f67_MD5.svg]]](https://claude.ai/)

---

**[English](#english) | [中文](#中文)**

<a name="english"></a>

## ✨ Features

Generate AI images directly in Claude using ModelScope's **Z-Image-Turbo** model.

- ⚡ **Fast** - Generate images in 10-30 seconds
- 🎨 **High Quality** - Professional-grade results
- 🌏 **Bilingual** - Supports English & Chinese
- 💡 **Easy** - AI one-click installation or 2-step manual setup

## 📋 Prerequisites

Before installing, you need to get your **ModelScope API Key**:

1. Visit [ModelScope](https://www.modelscope.cn/) and sign up (free)
2. Get your API token from [here](https://www.modelscope.cn/my/myaccesstoken)
3. Copy your API key (starts with `ms-`)

> 💡 **Keep your API key secure** - Never share it with others!

## 🚀 Quick Start

Choose your installation method:

### ⭐ Option A: AI One-Click Installation (Recommended) **EASIEST**

Simply tell Claude:

```
Please help me download and install the modelscope-image-gen skill from:
https://github.com/ZhaoSeven7/modelscope-image-gen-skill

Then add my ModelScope API key to the config file.
My API key is: ms-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

**That's it!** Claude will handle everything:
- ✅ Download the project
- ✅ Install to the correct location
- ✅ Configure your API key
- ✅ Verify installation

### 📦 Option B: Manual Installation (2 Steps)

**Step 1: Download & Install**

Download the project and copy to Claude skills directory:

**For Claude Code**:
```bash
# Navigate to your skills directory
cd ~/.claude/skills

# Clone the project
git clone https://github.com/ZhaoSeven7/modelscope-image-gen-skill.git modelscope-image-gen

# Or download ZIP and extract
```

**For Windows Users** (Claude Code):
1. Download ZIP from [GitHub](https://github.com/ZhaoSeven7/modelscope-image-gen-skill)
2. Extract to: `C:\Users\YourUsername\.claude\skills\modelscope-image-gen`

**For Claude.ai**:
1. Download ZIP from GitHub
2. Extract to a folder
3. Open Claude.ai → Settings → Skills → Upload Custom Skill
4. Select the extracted `skill` folder

**Step 2: Configure**

Open `config.json` and replace `YOUR_MODELSCOPE_API_KEY_HERE` with your API key:

**Windows**: Right-click config.json → Open with Notepad → Edit → Save

**macOS/Linux**:
```bash
nano ~/.claude/skills/modelscope-image-gen/config.json
```

Or ask Claude: "Please add my API key ms-xxxx to the config file"

### ✅ Verify Installation

In Claude, try:
```
Generate a simple test image of a red circle
```

If successful, an image will be saved to your vault!

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
│   ├── config.json           # Configuration file (add your API key here)
│   └── config.example.json   # Configuration template (backup)
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

![robotic-cat-cyberpunk-20260116-141457](https://img.ilovelinlin.top/docs/robotic-cat-cyberpunk-20260116-141457.jpg)
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
→ Create or update `config.json` with your API key

**"Image Generation Failed"**
→ Check:
- API key is valid at [ModelScope](https://www.modelscope.cn/my/myaccesstoken)
- Internet connection is stable
- Prompt follows content guidelines

**"API Error" or "401 Unauthorized"**
→ Your API key may be invalid or expired. Try:
1. Visit [ModelScope](https://www.modelscope.cn/my/myaccesstoken) to verify your key
2. Ask Claude to help update: "Please update my API key in the config file. My new key is: ms-xxxx"
3. Check if your API key has expired and needs renewal

**"Config file not found"**
→ Make sure `config.json` exists in the skill folder. If missing, you can:
1. Copy `config.example.json` to `config.json`
2. Or ask Claude: "Please create a config.json file for me"

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
- 💡 **简单** - AI 一键安装或 2 步手动配置

## 📋 准备工作

安装前，您需要先获取 **ModelScope API 密钥**：

1. 访问 [ModelScope](https://www.modelscope.cn/) 并注册（免费）
2. 从[这里](https://www.modelscope.cn/my/myaccesstoken)获取 API 令牌
3. 复制您的 API 密钥（以 `ms-` 开头）

> 💡 **请妥善保管您的 API 密钥** - 勿与他人分享！

## 🚀 快速开始

选择您的安装方式：

### ⭐ 方式 A：AI 一键安装（推荐）**最简单**

直接告诉 Claude：

```
请帮我下载并安装 modelscope-image-gen 技能：
https://github.com/ZhaoSeven7/modelscope-image-gen-skill

然后在配置文件中添加我的 ModelScope API 密钥。
我的 API 密钥是：ms-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

**就这样！** Claude 会自动处理所有事情：
- ✅ 下载项目
- ✅ 安装到正确位置
- ✅ 配置您的 API 密钥
- ✅ 验证安装

### 📦 方式 B：手动安装（2 步）

**第 1 步：下载并安装**

下载项目并复制到 Claude 技能目录：

**Claude Code**：
```bash
# 进入技能目录
cd ~/.claude/skills

# 克隆项目
git clone https://github.com/ZhaoSeven7/modelscope-image-gen-skill.git modelscope-image-gen

# 或下载 ZIP 并解压
```

**Windows 用户**（Claude Code）：
1. 从 [GitHub](https://github.com/ZhaoSeven7/modelscope-image-gen-skill) 下载 ZIP
2. 解压到：`C:\Users\你的用户名\.claude\skills\modelscope-image-gen`

**Claude.ai**：
1. 从 GitHub 下载 ZIP
2. 解压到文件夹
3. 打开 Claude.ai → 设置 → 技能 → 上传自定义技能
4. 选择解压后的 `skill` 文件夹

**第 2 步：配置**

打开 `config.json` 并将 `YOUR_MODELSCOPE_API_KEY_HERE` 替换为您的 API 密钥：

**Windows**：右键 config.json → 打开方式 → 记事本 → 编辑 → 保存

**macOS/Linux**：
```bash
nano ~/.claude/skills/modelscope-image-gen/config.json
```

或告诉 Claude："请帮我在配置文件中添加我的 API 密钥 ms-xxxx"

### ✅ 验证安装

在 Claude 中尝试：
```
生成一张简单的测试图片，一个红色圆圈
```

如果成功，图像会保存到您的 vault！

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
│   ├── config.json           # 配置文件（在此添加您的 API 密钥）
│   └── config.example.json   # 配置模板（备份）
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
![robotic-cat-cyberpunk-20260116-141457](https://img.ilovelinlin.top/docs/robotic-cat-cyberpunk-20260116-141457.jpg)
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
→ 创建或更新 `config.json` 并添加您的 API 密钥

**"图像生成失败"**
→ 检查：
- API 密钥在 [ModelScope](https://www.modelscope.cn/my/myaccesstoken) 是否有效
- 网络连接是否稳定
- 提示词是否符合内容规范

**"API 错误"或"401 未授权"**
→ 您的 API 密钥可能无效或已过期。尝试：
1. 访问 [ModelScope](https://www.modelscope.cn/my/myaccesstoken) 验证密钥
2. 请求 Claude 帮忙更新："请帮我在配置文件中更新我的 API 密钥。新密钥是：ms-xxxx"
3. 检查 API 密钥是否已过期需要续期

**"找不到配置文件"**
→ 确保 `config.json` 存在于技能文件夹中。如果缺失，您可以：
1. 复制 `config.example.json` 为 `config.json`
2. 或告诉 Claude："请帮我创建一个 config.json 文件"

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
