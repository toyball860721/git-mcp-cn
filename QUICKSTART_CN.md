# GitMCP 中文精简版

> 🛑 别再让 AI 幻觉代码了 — 用 GitMCP 连接真实文档
> 
> 📦 基于 [idosal/git-mcp](https://github.com/idosal/git-mcp) (7,843⭐)
> 
> 🚀 3 分钟配置，让 AI 永远使用最新 API

---

## ⚡ 什么是 GitMCP？

**一句话：让 AI 直接读取 GitHub 仓库的最新文档，不再瞎编代码。**

### 没有 GitMCP vs 使用 GitMCP

| 场景 | 没有 GitMCP | 使用 GitMCP |
|------|-------------|-------------|
| 新库 | ❌ AI 没见过，不会用 | ✅ 实时读取文档 |
| API 更新 | ❌ 用旧版本，报错 | ✅ 总是最新版 |
| 小众库 | ❌ 训练数据没有 | ✅ 有文档就能用 |

---

## 🎯 两种使用模式

### 模式 1：指定仓库（推荐）

```
gitmcp.io/{owner}/{repo}
```

**例子：**
- `gitmcp.io/mrdoob/three.js` — Three.js 3D 库
- `gitmcp.io/vercel/next.js` — Next.js 框架
- `gitmcp.io/toyball860721/mcp-templates-pack` — 我的 MCP 模板包

**优点：** 安全、精准，AI 不会访问错仓库

### 模式 2：通用模式

```
gitmcp.io/docs
```

**优点：** 灵活，一个配置查所有仓库
**缺点：** 每次要让 AI 知道查哪个仓库

---

## 🛠️ 快速配置

### Cursor 用户（最简单）

编辑 `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "gitmcp": {
      "url": "https://gitmcp.io/mrdoob/three.js"
    }
  }
}
```

重启 Cursor，完成！

### Claude Desktop 用户

编辑配置文件：

```json
{
  "mcpServers": {
    "gitmcp": {
      "command": "npx",
      "args": ["mcp-remote", "https://gitmcp.io/mrdoob/three.js"]
    }
  }
}
```

### Windsurf 用户

编辑 `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "gitmcp": {
      "serverUrl": "https://gitmcp.io/mrdoob/three.js"
    }
  }
}
```

---

## 💡 使用示例

### 示例 1：Three.js 场景

**配置：** `gitmcp.io/mrdoob/three.js`

**提示词：**
```
帮我创建一个 Three.js 场景，包含一个旋转的立方体
```

**结果：** AI 使用最新 three.js API，代码可直接运行。

### 示例 2：Next.js 路由

**配置：** `gitmcp.io/vercel/next.js`

**提示词：**
```
用 Next.js 15 的 App Router 写一个登录页面
```

**结果：** AI 使用 Next.js 15 最新语法，不是旧版本。

### 示例 3：小众库

**配置：** `gitmcp.io/some-author/new-library`

**提示词：**
```
这个库怎么用？给我个入门示例
```

**结果：** 即使这个库只有 100 stars，AI 也能读懂文档教你用。

---

## 🎬 实际效果对比

### 没有 GitMCP

```
用户：用 three.js 创建一个场景
AI: （使用 2023 年的 API）
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(...);
// 可能用了已废弃的方法
```

### 使用 GitMCP

```
用户：用 three.js 创建一个场景
AI: （访问最新文档）
import * as THREE from 'three';
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(...);
// 使用 2026 年最新 API，包含最佳实践
```

---

## ❓ 常见问题

### Q: 需要付费吗？

A: 完全免费。

### Q: 需要注册吗？

A: 不需要，配置即用。

### Q: 支持私有仓库吗？

A: 目前只支持公开仓库。

### Q: 会泄露我的代码吗？

A: 不会，只读访问公开文档。

### Q: 支持哪些 AI？

A: Cursor、Claude Desktop、Windsurf、VSCode、Cline 等支持 MCP 的工具。

---

## 🔗 相关链接

- [完整中文文档](./README.md)
- [GitMCP 官网](https://gitmcp.io)
- [英文原版项目](https://github.com/idosal/git-mcp)

---

## ☕ 支持本项目

- [爱发电](https://afdian.com/a/toyball)
- [GitHub Sponsors](https://github.com/sponsors/toyball860721)

---

**🦞 中文维护者：[@toyball860721](https://github.com/toyball860721)**

*最后更新：2026-03-28*
