---
title: "你好，Hugo"
date: 2026-11-11T12:00:00+08:00
draft: false
tags: ["Hugo", "博客"]
categories: ["随笔"]
summary: "用 Hugo + PaperMod 重新搭起个人博客，这里是我的第一篇测试文章。"
---

## 为什么换成 Hugo

之前的博客是用 Hexo 搭的，这次换成了 Hugo。原因很简单：

- **构建快**：几百篇文章也能在毫秒级完成渲染
- **单二进制**：不需要 Node.js 运行时，装一个 `hugo` 就能跑
- **部署简单**：推到 GitHub 后由 Actions 自动构建并发布到 Pages

## 本地预览

```bash
hugo server -D
```

打开 <http://localhost:1313> 就能看到效果。

## 写新文章

```bash
hugo new content posts/my-new-post.md
```

编辑 `content/posts/my-new-post.md`，把 `draft` 改成 `false`，提交推送即可。

## 代码块测试

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, Hugo!")
}
```

后面会慢慢把旧博客的文章迁移过来。
