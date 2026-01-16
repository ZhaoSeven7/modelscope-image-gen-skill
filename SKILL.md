---
name: modelscope-image-gen
description: 使用 ModelScope Z-Image-Turbo 模型快速生成 AI 图像。支持中英文提示词，10-30 秒生成高质量图片。当用户需要创建图像、生成视觉内容或需要 AI 插图时使用此技能。
---

# ModelScope AI 图像生成器

使用 ModelScope 的 **Z-Image-Turbo** 模型从文本描述生成 AI 图像 - 快速、高质量的文本到图像 AI。

## 技能功能

此技能使用 **Tongyi-MAI/Z-Image-Turbo** 模型将自然语言描述转换为图像。
- ⚡ **快速生成** - 针对速度优化
- 🎨 **高质量** - 优秀的视觉效果
- 🌏 **中英文支持** - 同时支持两种语言
- 💡 **易于使用** - 只需描述你想要的

## 配置要求

⚠️ **重要提示**：此技能需要 ModelScope API 密钥才能运行。

### 快速配置

1. **获取 API 密钥**：访问 https://www.modelscope.cn/ 免费注册
2. **获取令牌**：前往 https://www.modelscope.cn/my/myaccesstoken
3. **创建配置**：在此 SKILL.md 同级目录创建 `config.json` 文件
4. **添加密钥**：在配置文件中粘贴你的 API 密钥

### 配置文件格式

创建 `config.json`：
```json
{
  "api_key": "YOUR_MODELSCOPE_API_KEY_HERE"
}
```

**示例**：
```json
{
  "api_key": "ms-xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
}
```

### 配置文件位置

配置文件应与 SKILL.md 在同一目录：
```
modelscope-image-gen/
├── SKILL.md
└── config.json  ← 在此创建文件并添加 API 密钥
```

## 使用方法

### 基本图像生成

只需描述你想要的图像：

**用户**："生成一张日落的海洋图片"

**你需要**：
1. 检查 config.json 是否存在并包含有效 API 密钥
2. 如果缺失，提示用户进行配置
3. 使用提示词调用 ModelScope API
4. 将生成的图像保存到用户的 vault
5. 报告成功并告知文件位置

### 示例提示词

**简单**：
```
生成一张金色的猫的图片
```

**详细**：
```
创建一个雄伟的山地日出景观，
黄金时刻光照，戏剧性的云彩，
雪山峰，写实风格，高细节
```

**艺术风格**：
```
生成梵高风格的星夜，
油画，鲜艳色彩，后印象派
```

### 支持的语言

Z-Image-Turbo 模型同时支持：
- 🇨🇳 **中文**："生成一张金色的猫的图片"
- 🇺🇸 **英文**："Generate a picture of a golden cat"

## 工作流程

当用户请求生成图像时：

1. **检查配置**
   - 在技能目录查找 `config.json`
   - 验证 `api_key` 字段存在且不为空
   - 如果缺失或无效，要求用户配置

2. **处理请求**
   - 从用户提示词中提取图像描述
   - 识别任何风格关键词或规格
   - 准备 API 请求

3. **生成图像**
   - 使用提示词调用 ModelScope API
   - 使用异步模式以获得更好性能
   - 轮询完成状态（通常 10-30 秒）
   - 优雅地处理任何错误

4. **保存结果**
   - 下载生成的图像
   - 使用描述性文件名保存到用户的 vault
   - 格式：`{描述}-{时间戳}.jpg`
   - 默认位置：`./generated-images/`

5. **报告成功**
   - 告知用户图像保存位置
   - 提供生成详情（模型、时间等）
   - 询问是否需要生成更多或优化结果

## API 集成

此技能使用以下参数调用 ModelScope API：

### 端点
```
POST https://api-inference.modelscope.cn/v1/images/generations
```

### 请求头
```python
headers = {
    "Authorization": f"Bearer {api_key}",
    "Content-Type": "application/json",
    "X-ModelScope-Async-Mode": "true"
}
```

### 请求体
```json
{
  "model": "Tongyi-MAI/Z-Image-Turbo",
  "prompt": "一只金色的猫"
}
```

### 响应处理流程
1. 提交生成请求 → 获取 `task_id`
2. 每 5 秒轮询任务状态端点：`/v1/tasks/{task_id}`
   - **必需请求头**：`X-ModelScope-Task-Type: image_generation`
3. 当状态为 "SUCCEED" 时，从 `output_images[0]` 获取图像 URL
4. 从 URL 下载图像并保存到 vault

### 完整 API 示例

**步骤 1：提交任务**
```bash
curl -X POST "https://api-inference.modelscope.cn/v1/images/generations" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -H "X-ModelScope-Async-Mode: true" \
  -d '{
    "model": "Tongyi-MAI/Z-Image-Turbo",
    "prompt": "一只金色的猫"
  }'
```

**响应**：
```json
{
  "task_id": "5075521",
  "request_id": "45287537-e13b-44bd-91ab-7eb193e86b29"
}
```

**步骤 2：轮询任务状态**
```bash
curl "https://api-inference.modelscope.cn/v1/tasks/5075521" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -H "X-ModelScope-Task-Type: image_generation"
```

**响应（完成时）**：
```json
{
  "task_status": "SUCCEED",
  "output_images": [
    "https://muse-ai.oss-cn-hangzhou.aliyuncs.com/img/d2fd4ef091f244eaa4c102b96cddf930.png"
  ],
  "time_taken": 18812.86
}
```

**步骤 3：下载图像**
```bash
curl -o "output.jpg" "https://muse-ai.oss-cn-hangzhou.aliyuncs.com/img/..."
```

### Python 实现示例

```python
import requests
import time
import json

base_url = 'https://api-inference.modelscope.cn/'
api_key = "YOUR_API_KEY"

common_headers = {
    "Authorization": f"Bearer {api_key}",
    "Content-Type": "application/json",
}

# 步骤 1：提交任务
response = requests.post(
    f"{base_url}v1/images/generations",
    headers={**common_headers, "X-ModelScope-Async-Mode": "true"},
    data=json.dumps({
        "model": "Tongyi-MAI/Z-Image-Turbo",
        "prompt": "一只金色的猫"
    }, ensure_ascii=False).encode('utf-8')
)

response.raise_for_status()
task_id = response.json()["task_id"]

# 步骤 2：轮询完成状态
while True:
    result = requests.get(
        f"{base_url}v1/tasks/{task_id}",
        headers={**common_headers, "X-ModelScope-Task-Type": "image_generation"},
    )
    result.raise_for_status()
    data = result.json()

    if data["task_status"] == "SUCCEED":
        image_url = data["output_images"][0]
        # 下载并保存图像
        image_response = requests.get(image_url)
        with open("result_image.jpg", "wb") as f:
            f.write(image_response.content)
        print("✅ 图像已保存为 result_image.jpg")
        break
    elif data["task_status"] == "FAILED":
        print("❌ 图像生成失败。")
        break

    time.sleep(5)  # 等待 5 秒后再次轮询
```

## 错误处理

### 缺少 API 密钥

如果 config.json 缺失或 api_key 为空：

```
❌ API 密钥未配置

要使用此技能，你需要 ModelScope API 密钥：

1. 获取免费 API 密钥：https://www.modelscope.cn/
2. 在此技能文件夹中创建 config.json
3. 添加密钥：{"api_key": "your-api-key-here"}

配置文件应位于：
.claude/skills/modelscope-image-gen/config.json
```

### API 错误

如果 API 调用失败：

```
❌ 图像生成失败

可能原因：
- API 密钥无效
- 网络连接问题
- ModelScope 服务不可用
- 提示词包含不当内容

请检查：
✓ API 密钥有效
✓ 有网络连接
✓ 提示词符合内容规范
```

### 生成失败

如果 task_status 为 "FAILED"：

```
❌ 图像生成失败

Z-Image-Turbo 模型无法生成图像。
请尝试：
- 使用不同的提示词
- 简化描述
- 检查内容是否违反政策
```

## 最佳实践

### 提示词工程

帮助用户创建更好的提示词：

1. **添加具体细节**
   - 主体："一只猫" → "一只毛茸茸的橙色斑纹猫"
   - 场景："户外" → "在阳光明媚的花园里，有花朵"
   - 灯光："有光" → "黄金时刻阳光"

2. **包含风格**
   - "写实风格"、"油画"、"数字艺术"
   - "梵高风格"、"专业摄影"

3. **描述质量**
   - "高细节"、"专业级"、"4K"、"8K"

### 提示词转换示例

**修改前**：
```
一只狗
```

**修改后**：
```
一只金毛犬在草地上奔跑，
开心表情，晴天，绿草地，
写实风格，高细节，专业摄影
```

## 技术细节

### 模型信息
- **模型**：Tongyi-MAI/Z-Image-Turbo
- **类型**：文本到图像生成
- **速度**：快速（针对快速生成优化）
- **质量**：高质量结果
- **语言**：中文和英文

### API 详情
- **基础 URL**：https://api-inference.modelscope.cn/
- **异步模式**：启用（以获得更好性能）
- **轮询间隔**：5 秒
- **超时时间**：60 秒
- **输出格式**：JPG

### 速率限制
受 ModelScope API 速率限制约束。如果用户达到限制，请礼貌地告知。

## 示例

### 示例 1：简单生成

**用户**："生成一张红色圆圈的图片"

**流程**：
1. 检查 config.json ✓
2. 提取提示词："红色圆圈"
3. 调用 API
4. 轮询完成状态（15 秒）
5. 保存为：`red-circle-20260116-153045.jpg`
6. 响应："✅ 图像已生成！保存至：./generated-images/red-circle-20260116-153045.jpg"

### 示例 2：中文提示词

**用户**："生成一张金色的猫的图片"

**流程**：
1. 检查 config.json ✓
2. 提取提示词："金色的猫"
3. 使用中文提示词调用 API
4. 轮询完成状态（20 秒）
5. 保存为：`golden-cat-20260116-153100.jpg`
6. 响应："✅ 图片已生成！保存位置：./generated-images/golden-cat-20260116-153100.jpg"

### 示例 3：详细场景

**用户**："创建一个宁静的山湖日出，有山，写实风格，高细节"

**流程**：
1. 检查 config.json ✓
2. 提取包含所有细节的提示词
3. 使用完整描述调用 API
4. 轮询完成状态（25 秒）
5. 保存为：`peaceful-lake-sunrise-20260116-153125.jpg`
6. 响应："✅ 图像已生成！保存至：./generated-images/peaceful-lake-sunrise-20260116-153125.jpg"

## 与其他技能的集成

此技能与以下技能配合良好：
- **写作技能**：生成图像以说明文章
- **图表技能**：为技术图表创建概念艺术
- **文档技能**：为文档添加视觉内容

## 限制

- 需要有效 API 密钥（需免费注册）
- 需要网络连接
- 生成时间变化（通常 10-30 秒）
- 受 ModelScope 内容政策约束
- 可能适用速率限制

## 故障排除

**问题**："技能不工作"
**解决方案**：检查 config.json 是否存在并包含有效 API 密钥

**问题**："图像质量不佳"
**解决方案**：鼓励用户添加更多细节和风格规格

**问题**："生成时间太长"
**解决方案**：解释 10-30 秒是正常的；复杂提示词可能需要更长时间

**问题**："API 错误"
**解决方案**：验证 API 密钥有效且账户状态良好

## 资源

- ModelScope: https://www.modelscope.cn/
- 获取 API 密钥: https://www.modelscope.cn/my/myaccesstoken
- API 文档: https://www.modelscope.cn/docs
- 模型页面: https://www.modelscope.cn/models/Tongyi-MAI/Z-Image-Turbo

---

**版本**：1.0.0
**最后更新**：2026-01-16
**模型**：Tongyi-MAI/Z-Image-Turbo
