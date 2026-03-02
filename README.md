# 工作日志网站

使用 Hugo + Hugo Book 主题构建的个人工作日志与报告展示网站。

---

## 在线访问

**网站地址：** https://my-log-site.vercel.app

---

## 项目位置

```
~/Documents/Learning/Logs/
```

---

## 快速开始

### 本地开发

```bash
cd ~/Documents/Learning/Logs
hugo server
```

访问 http://localhost:1313

### 构建静态文件

```bash
hugo
```

输出目录: `public/`

---

## 如何更新日志

### 方式一：手动创建新日志

```bash
# 创建新的工作日志
hugo new content posts/2026-03-03-new-post.md

# 创建新的报告文档
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

---

## 如何部署到线上

### 步骤 1：推送代码到 GitHub

```bash
cd ~/Documents/Learning/Logs

# 添加更改
git add .

# 提交更改
git commit -m "更新日志内容"

# 推送到 GitHub
git push
```

### 步骤 2：Vercel 自动部署

推送到 GitHub 后，Vercel 会自动检测并部署。

---

## 日常更新流程

```bash
# 1. 进入项目目录
cd ~/Documents/Learning/Logs

# 2. 创建新日志（可选）
hugo new content/posts/2026-03-03-my-log.md

# 3. 编辑内容
# 使用任意编辑器打开 content/posts/2026-03-03-my-log.md

# 4. 本地预览
hugo server
# 访问 http://localhost:1313 检查

# 5. 推送到 GitHub（自动部署到线上）
git add .
git commit -m "新增日志"
git push
```

---

## 目录结构

```
Logs/
├── content/
│   ├── posts/          # 工作日志
│   ├── reports/        # 报告文档
│   └── about/          # 关于页面
├── static/             # 静态资源
├── themes/            # Hugo 主题
├── hugo.yaml          # 配置文件
├── README.md          # 本文件
└── public/            # 构建输出
```

---

## 技术栈

- Hugo: 静态网站生成器 (v0.157.0)
- Hugo Book: 文档主题
- Vercel: 静态网站托管
- GitHub: 代码托管

---

## 许可证

MIT License
