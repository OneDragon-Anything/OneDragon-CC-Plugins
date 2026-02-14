# uv-pyright-lsp

基于 [claude-plugins-official/pyright-lsp](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/pyright-lsp) 改造。

## 改造原因

官方插件需要全局安装 `pyright-langserver`，但个人开发习惯：

1. **项目隔离环境**：每个项目使用独立的虚拟环境
2. **不激活虚拟环境**：开发时不会激活 venv
3. **使用 uv 启动**：利用 uv 快速启动，自动在项目隔离环境中运行

## 使用前提

项目已使用 uv 管理依赖，并已安装 pyright：

```bash
uv add pyright --dev
```

## 工作原理

```bash
uv run pyright-langserver --stdio
```

通过 `uv run` 启动 pyright-langserver，确保：
- 在项目的虚拟环境中运行
- 使用项目特定的 pyright 版本
- 不需要全局安装 pyright

## 配置

支持标准 pyright 配置文件：

**pyproject.toml**（推荐）：
```toml
[tool.pyright]
include = ["src"]
exclude = ["**/node_modules", "**/__pycache__"]
```

**pyrightconfig.json**：
```json
{
  "include": ["src"],
  "exclude": ["**/node_modules", "**/__pycache__"]
}
```

## License

MIT
