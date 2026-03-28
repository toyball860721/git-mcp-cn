# GitMCP 中文文档

> 🛑 **别再 vibe-hallucinating 了，开始 vibe-coding！**
> 
> 📦 **GitMCP** — 将任何 GitHub 项目变成 AI 可理解的文档中心
> 
> 🌟 原版项目：[idosal/git-mcp](https://github.com/idosal/git-mcp) (7,843⭐)
> 
> 📝 中文维护者：[@toyball860721](https://github.com/toyball860721)
> 
> ☕ 支持本项目：[爱发电](https://afdian.com/a/toyball) | [GitHub Sponsors](https://github.com/sponsors/toyball860721)

---

## 🤔 什么是 GitMCP？

GitMCP 是一个免费的开源远程 [Model Context Protocol (MCP)](https://docs.anthropic.com/en/docs/agents-and-tools/mcp) 服务器，它将**任何**GitHub 项目（仓库或 GitHub Pages）转换为文档中心。它使 Cursor 等 AI 工具能够访问最新的文档和代码，即使 LLM 从未见过它们，从而无缝消除代码幻觉。

### GitMCP 支持**两种模式**

| 模式 | URL 格式 | 使用场景 |
|------|----------|----------|
| **特定仓库** | `gitmcp.io/{owner}/{repo}` | 当你主要使用少数几个库时 |
| **特定仓库** | `{owner}.gitmcp.io/{repo}` | GitHub Pages 站点 |
| **通用服务器** | `gitmcp.io/docs` | 需要频繁切换不同仓库时 |

### 使用 GitMCP 的好处

- ✅ AI 助手直接从源头访问**最新**文档和代码
- ✅ 获取准确的 API 使用和可靠的代码示例
- ✅ 即使使用小众、新出或快速变化的库也能高效工作
- ✅ 显著减少幻觉，提高代码正确性

---

## ✨ 核心特性

| 特性 | 说明 |
|------|------|
| 📚 **任意 GitHub 项目的最新文档** | 让 AI 助手无缝访问 GitHub 项目的文档和代码，内置智能搜索功能 |
| 🧠 **不再幻觉** | AI 助手提供准确、相关的回答 |
| ☁️ **零配置** | GitMCP 在云端运行，无需下载安装 |
| 💬 **嵌入式聊天** | 直接在浏览器中与仓库文档聊天 |
| 🔒 **开放、免费、隐私** | 开源免费，不收集个人信息，不存储查询 |

---

## 🚀 快速开始

### 步骤 1：选择服务器类型

根据你的需求选择 URL：

- **GitHub 仓库**: `gitmcp.io/{owner}/{repo}`
- **GitHub Pages**: `{owner}.gitmcp.io/{repo}`
- **通用工具**（动态）: `gitmcp.io/docs`

### 步骤 2：连接你的 AI 助手

#### Cursor

编辑 `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "gitmcp": {
      "url": "https://gitmcp.io/{owner}/{repo}"
    }
  }
}
```

#### Claude Desktop

1. 打开 Claude Desktop → Settings → Developer → Edit Config
2. 替换配置：

```json
{
  "mcpServers": {
    "gitmcp": {
      "command": "npx",
      "args": ["mcp-remote", "https://gitmcp.io/{owner}/{repo}"]
    }
  }
}
```

#### Windsurf

编辑 `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "gitmcp": {
      "serverUrl": "https://gitmcp.io/{owner}/{repo}"
    }
  }
}
```

#### VSCode

编辑 `.vscode/mcp.json`:

```json
{
  "servers": {
    "gitmcp": {
      "type": "sse",
      "url": "https://gitmcp.io/{owner}/{repo}"
    }
  }
}
```

#### Cline

编辑 `cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "gitmcp": {
      "url": "https://gitmcp.io/{owner}/{repo}",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

#### Highlight AI

1. 打开 Highlight AI，点击侧边栏的插件图标 (@)
2. 点击 **Installed Plugins** → **Custom Plugin**
3. 点击 **Add a plugin using a custom SSE URL**
4. 填写：
   - Plugin name: `gitmcp`
   - SSE URL: `https://gitmcp.io/{owner}/{repo}`

#### Augment Code

1. 打开 Augment Code settings → MCP
2. 添加新 MCP 服务器：
   - Name: `git-mcp Docs`
   - Command: `npx mcp-remote https://gitmcp.io/{owner}/{repo}`

---

## 📖 使用示例

### 示例 1：Three.js 场景创建

```
使用 GitMCP 连接 three.js 仓库，帮我创建一个基本的 3D 场景
```

AI 会访问最新的 three.js 文档，给出准确的 API 用法。

### 示例 2：查询新库的用法

```
连接 gitmcp.io/some-author/new-library，这个库怎么用？
```

即使这个库很新，AI 也能访问最新文档。

### 示例 3：通用模式

```
使用 gitmcp.io/docs，帮我查一下 React 和 Vue 的最新 API 区别
```

AI 会提示你指定要查询的仓库。

---

## 🎯 对比演示

使用 GitMCP 前后对比（Three.js 场景创建）：

**没有 GitMCP:**
- ❌ AI 使用训练数据中的旧版本 API
- ❌ 可能给出已废弃的方法
- ❌ 需要手动纠正

**使用 GitMCP:**
- ✅ AI 访问最新文档
- ✅ API 用法准确
- ✅ 代码可直接运行

---

## 🔒 隐私说明

GitMCP:
- 不收集个人信息
- 不存储查询记录
- 支持自托管
- 完全开源

---

## 📚 进阶使用

### 自托管 GitMCP

如果你想自己托管 GitMCP:

```bash
git clone https://github.com/idosal/git-mcp.git
cd git-mcp
pnpm install
pnpm dev
```

### 徽章展示

在你的仓库 README 中添加：

```markdown
[![GitMCP](https://img.shields.io/endpoint?url=https://gitmcp.io/badge/your-username/your-repo)](https://gitmcp.io/your-username/your-repo)
```

---

## ❓ 常见问题

### Q: GitMCP 免费吗？

A: 完全免费，开源项目。

### Q: 需要注册账号吗？

A: 不需要，直接使用。

### Q: 支持私有仓库吗？

A: 目前仅支持公开仓库。

### Q: 文档更新频率？

A: 实时访问 GitHub，始终是最新版。

### Q: 可以用于商业项目吗？

A: 可以，MIT 许可证。

---

## 📖 更多资源

- [英文原版项目](https://github.com/idosal/git-mcp)
- [GitMCP 官网](https://gitmcp.io)
- [MCP 协议文档](https://docs.anthropic.com/en/docs/agents-and-tools/mcp)

---

## 🤝 参与贡献

欢迎提交 Issue 和 Pull Request 改进中文文档！

---

## 📄 许可证

本项目遵循原项目的 MIT 许可证。

---

## ☕ 支持作者

如果你觉得这个中文文档对你有帮助，欢迎支持：

- [爱发电](https://afdian.com/a/toyball)
- [GitHub Sponsors](https://github.com/sponsors/toyball860721)

**中文维护者持续更新中...** 🦞

*最后更新：2026-03-28*
