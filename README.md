# Wukong Code — 大模型编程助手可视化界面

> 独立开发的 Python Web 编程助手界面，直接对接大模型 API（OpenAI 兼容 / Anthropic Messages），
> 不依赖任何外部 CLI。

## 快速启动

```bash
cd /opt/claude/wukong_code
python3 main.py
```

浏览器打开 `http://localhost:9090`

## 首次使用

1. 点击左侧 **⚙ 设置** 按钮
2. 选择 API 格式（OpenAI 兼容 或 Anthropic）
3. 填写 Base URL / API Key / Model
4. 可选：点击"探测模型列表"自动发现可用模型
5. 保存后即可开始聊天

## 常见配置示例

| 厂商 | API 格式 | Base URL | Model 示例 |
|------|----------|----------|-----------|
| OpenAI | OpenAI 兼容 | `https://api.openai.com/v1` | `gpt-4o` |
| DeepSeek | OpenAI 兼容 | `https://api.deepseek.com/v1` | `deepseek-chat` |
| 通义千问 | OpenAI 兼容 | `https://dashscope.aliyuncs.com/compatible-mode/v1` | `qwen-plus` |
| 智谱 GLM | OpenAI 兼容 | `https://open.bigmodel.cn/api/paas/v4` | `glm-4` |
| Anthropic | Anthropic | `https://api.anthropic.com` | `claude-sonnet-4-20250514` |
| Ollama 本地 | OpenAI 兼容 | `http://localhost:11434/v1` | `llama3.2` |

## 功能

- **多会话管理**：左侧栏新建/切换/删除会话，上下文独立保存
- **流式输出**：大模型回复逐字推送，打字机效果
- **Markdown 渲染**：代码高亮、表格、列表、引用
- **配置持久化**：API 配置保存到 `data/config.json`
- **双格式支持**：OpenAI 兼容格式 + Anthropic Messages 格式
- **模型探测**：自动探测支持的模型列表
- **深色主题**：黑客风格界面，适配 Kali Linux

## 项目结构

```
/opt/claude/wukong_code/
├── main.py           # FastAPI 后端入口
├── llm_client.py     # 大模型 API 客户端（SSE 流式解析）
├── config.py         # 配置持久化模块
├── templates/
│   └── index.html    # 单页应用
├── static/
│   ├── css/style.css # 深色主题样式
│   └── js/app.js     # 前端逻辑
├── requirements.txt  # 依赖清单
└── README.md        # 本文件
```

## 端口

默认 `9090`，可在 `data/config.json` 中修改 `port` 字段。