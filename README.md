# 工作日志网站

使用 Hugo + Hugo Book 主题构建的个人工作日志与报告展示网站。

## 功能特点

- 📖 简约文档风格
- 🌙 支持深色模式（自动切换）
- 🔍 内置搜索功能
- 🏷️ 标签和分类支持
- 📱 响应式设计

## 快速开始

### 本地开发

```bash
cd my-log-site
hugo server
```

访问 http://localhost:1313

### 构建静态文件

```bash
hugo
```

输出目录: `public/`

## 内容管理

### 创建新日志

```bash
hugo new content posts/2026-03-03-new-post.md
```

### 创建新报告

```bash
hugo new content reports/my-report.md
```

### Front Matter 模板

```yaml
---
title: "标题"
date: 2026-03-02
description: "描述"
tags: ["标签1", "标签2"]
categories: ["分类"]
draft: false
---
```

## 目录结构

```
my-log-site/
├── content/
│   ├── posts/          # 工作日志
│   ├── reports/       # 报告文档
│   └── about/         # 关于页面
├── static/             # 静态资源
├── themes/            # 主题
├── hugo.yaml          # 配置文件
└── public/            # 构建输出
```

## 配置说明

编辑 `hugo.yaml` 自定义网站设置：

- `title`: 网站标题
- `BookTheme`: 主题 (light/dark/auto)
- `BookSearch`: 启用搜索
- `BookToc`: 显示目录

## 部署

### 本地部署

直接使用 `public/` 目录部署到任意静态托管服务：

- Vercel
- Netlify
- GitHub Pages
- Cloudflare Pages

### GitHub Pages 示例

1. 创建 GitHub 仓库
2. 推送代码
3. 在仓库设置中启用 GitHub Pages
4. Source 选择 "main branch /docs folder" 或使用 Actions

## 技术栈

- **Hugo**: 静态网站生成器
- **Hugo Book**: 文档主题

## 许可证

MIT License
