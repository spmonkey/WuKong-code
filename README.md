# Wukong Code — 大模型编程助手

> 基于 **Python FastAPI** 的独立 Web 应用，直接对接大模型 API（OpenAI 兼容 / Anthropic Messages），
> 支持多会话管理、流式输出、MCP 协议、文件操作等能力。

---

## 快速启动

下载 `WukongCode-Setup-1.0.1.exe`，双击安装后从开始菜单启动。

浏览器打开 `http://localhost:9090`

---

## 首次使用

1. 启动服务后，浏览器打开 `http://localhost:9090`
2. 点击左侧 **⚙ 设置** 按钮
3. 选择 API 格式（OpenAI 兼容 或 Anthropic）
4. 填写 Base URL / API Key / Model
5. 可选：点击"探测模型列表"自动发现可用模型
6. 保存后即可开始聊天

> ⚠️ 当前配置已清空，API Key / Base URL / Model 需自行填写。

---

## 常见配置示例

| 厂商 | API 格式 | Base URL | Model 示例 |
|------|----------|----------|-----------|
| OpenAI | OpenAI 兼容 | `https://api.openai.com/v1` | `gpt-4o` |
| DeepSeek | OpenAI 兼容 | `https://api.deepseek.com/v1` | `deepseek-chat` |
| 通义千问 | OpenAI 兼容 | `https://dashscope.aliyuncs.com/compatible-mode/v1` | `qwen-plus` |
| 智谱 GLM | OpenAI 兼容 | `https://open.bigmodel.cn/api/paas/v4` | `glm-4` |
| Anthropic | Anthropic | `https://api.anthropic.com` | `claude-sonnet-4-20250514` |
| Ollama 本地 | OpenAI 兼容 | `http://localhost:11434/v1` | `llama3.2` |

---

## 功能特性

### 核心功能
- **多会话管理**：左侧栏新建/切换/删除会话，上下文独立保存到 `data/sessions.json`
- **流式输出**：大模型回复逐字推送，打字机效果
- **Markdown 渲染**：代码高亮、表格、列表、引用
- **配置持久化**：API 配置保存到 `data/config.json`
- **双格式支持**：OpenAI 兼容格式 + Anthropic Messages 格式
- **模型探测**：自动探测支持的模型列表
- **MCP 协议支持**：通过 `data/mcp.json` 配置 MCP 服务端，支持 stdio 和 URL 两种模式
- **LLM 响应缓存**：基于 SHA256 哈希的 LRU 缓存（最多 500 条），跨会话相同提问可命中
- **工作区文件操作**：read_file / edit / write / glob / grep 五件套
- **深色主题**：暗色界面

### 安全机制
- 命令权限分级：只读命令自动放行、写操作需审批、破坏性命令硬拦截
- edit/write 操作走审批流（diff 预览 → 用户确认 → 落盘）
- 敏感 API Key 日志脱敏（`sk-****` / `Bearer ****`）

---

## 提示词预设

项目内置提示词预设，可在设置面板中切换。预设内容存储在 `data/prompts.json`，支持自定义添加。

---

## 配置

### 端口

默认 `9090`，可在设置面板或 `data/config.json` 中修改 `port` 字段。

### 配置文件参考

```json
{
  "base_url": "https://api.openai.com/v1",
  "api_key": "",
  "model": "gpt-4o",
  "api_format": "openai",
  "port": 9090,
  "reasoning_effort": "",
  "workspace": "",
  "permission_mode": "normal",
  "check_command": ""
}
```

---

## 许可

MIT License — 详见 [LICENSE.txt](LICENSE.txt)
