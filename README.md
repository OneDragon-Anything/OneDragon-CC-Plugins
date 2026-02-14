# OneDragon-CC-Plugins

辅助一条龙开发的 Claude Code 工具集。

## 安装使用

### 添加市场

```bash
# 从 GitHub 添加（正式版本）
claude plugin marketplace add https://github.com/OneDragon-Anything/OneDragon-CC-Plugins.git

# 从本地路径添加（开发测试）
claude plugin marketplace add .
```

### 安装插件

```bash
claude plugin install uv-pyright-lsp@onedragon-cc-plugins
claude plugin enable uv-pyright-lsp@onedragon-cc-plugins
```

## 开发指南

### 本地测试

开发时直接测试，无需安装：

```bash
claude --plugin-dir . plugins/uv-pyright-lsp
```

这样可以使用相同的市场名称 `onedragon-cc-plugins`，只是来源不同（本地路径 vs GitHub URL），方便切换开发和正式版本。

参考官方文档 https://code.claude.com/docs/en/plugins

## License

MIT
