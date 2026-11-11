# Musele 的博客

使用 [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 搭建的个人博客，通过 GitHub Actions 自动部署到 GitHub Pages。

- 站点地址：<https://musele.github.io/>
- 仓库地址：<https://github.com/musele/musele.github.io>

## 本地环境

需要 [Hugo Extended](https://gohugo.io/installation/) v0.169.0 或更高版本。

```bash
hugo version
```

如果提示命令不存在，在本机可用 mise 安装：

```bash
mise use -g hugo-extended@0.169.0
```

首次克隆仓库后拉取主题子模块：

```bash
git submodule update --init --recursive
```

## 本地预览

```bash
hugo server -D
```

浏览器打开 <http://localhost:1313>。`-D` 表示同时渲染草稿。

## 写文章

```bash
hugo new content posts/my-new-post.md
```

文章在 `content/posts/` 下，修改元信息并把 `draft` 改为 `false`：

```yaml
---
title: "文章标题"
date: 2026-11-11T12:00:00+08:00
draft: false
tags: ["标签"]
categories: ["分类"]
summary: "一句话摘要"
---
```

预览没问题后提交并推送：

```bash
git add .
git commit -m "post: 文章标题"
git push
```

推送后 GitHub Actions 自动构建并发布，几分钟内生效。

## 部署说明

工作流文件：`.github/workflows/hugo.yaml`

首次使用时，需要在 GitHub 仓库的 **Settings → Pages → Build and deployment** 中把 **Source** 设为 **GitHub Actions**。

之后每次推送到 `main` 都会自动部署，不需要提交 `public/` 目录（已在 `.gitignore` 中忽略）。

## 目录结构

```
content/
  posts/          # 文章
  about.md        # 关于页
  archives.md     # 归档页
  search.md       # 搜索页
themes/PaperMod/  # 主题（git submodule）
hugo.toml         # 站点配置
.github/workflows/hugo.yaml  # 自动部署
```

## 常用命令

| 命令 | 说明 |
| --- | --- |
| `hugo server -D` | 本地预览（含草稿） |
| `hugo new content posts/xxx.md` | 新建文章 |
| `hugo --gc --minify` | 本地构建到 `public/` |
| `git submodule update --remote themes/PaperMod` | 更新主题 |
