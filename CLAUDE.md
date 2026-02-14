# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

OneDragon-CC-Plugins 是一个用于 Claude Code 的插件市场，包含一条龙项目开发所需的工具集。

## 插件开发规范

### 目录结构

```
OneDragon-CC-Plugins/              # 市场根目录
├── .claude-plugin/              # 市场配置目录
│   └── marketplace.json       # 市场清单文件
├── plugins/                    # 插件集合目录
│   │── plugin-a/     # 单个插件
│   └── plugin-b/     # 单个插件
└── README.md
```

### 市场清单 (marketplace.json)

位置：`.claude-plugin/marketplace.json`

必需字段：
- `name`: 市场标识符（kebab-case）
- `owner`: 维护者信息（`name`, `email`）
- `plugins`: 插件数组

可选字段：
- `metadata.description`: 市场描述
- `metadata.pluginRoot`: 插件根目录前缀（默认为 `./`）


### 单个插件目录结构

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json      # Plugin metadata (required)
├── .mcp.json            # MCP server configuration (optional)
├── commands/            # Slash commands (optional)
├── agents/              # Agent definitions (optional)
├── skills/              # Skill definitions (optional)
└── README.md            # Documentation
```

### 插件清单 (plugin.json)

位置：`plugins/{plugin-name}/.claude-plugin/plugin.json`

必需字段：
- `name`: 插件名称（kebab-case）

常用字段：
- `version`: 版本号
- `description`: 插件描述
- `author`: 作者信息
- `license`: 许可证
- `keywords`: 关键词数组

组件配置字段：
- `lspServers`: LSP 服务器配置
- `commands`: 命令路径或数组
- `agents`: 代理路径或数组
- `hooks`: 钩子配置或路径
- `mcpServers`: MCP 服务器配置

### 添加新插件流程

1. **创建插件目录**
   ```bash
   mkdir -p plugins/new-plugin/.claude-plugin
   ```

2. **编写 plugin.json**
   ```json
   {
     "name": "new-plugin",
     "version": "0.1.0",
     "description": "插件描述"
   }
   ```

3. **在市场清单中注册**
   编辑 `.claude-plugin/marketplace.json`，添加到 `plugins` 数组：
   ```json
   {
     "name": "new-plugin",
     "source": "./plugins/new-plugin",
     "description": "插件描述"
   }
   ```

4. **验证**
   ```bash
   claude plugin validate .
   ```

### 注意事项

- 所有路径在 `marketplace.json` 中相对于 `metadata.pluginRoot`（默认 `./`）
- 插件名称必须使用 kebab-case（小写字母和连字符）
- `source` 字段支持相对路径、GitHub 仓库或 Git URL
- 插件目录必须在 `plugins/` 下，不能在 `.claude-plugin/` 内
