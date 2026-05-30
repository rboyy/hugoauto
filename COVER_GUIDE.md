# 封面图片配置指南

## 问题诊断

本地可以显示封面，但 GitHub Pages 上不显示，常见原因：

1. **外部图片链接问题**：
   - CORS（跨域资源共享）限制
   - 图片服务不稳定或被 GitHub Pages 拦截
   - HTTPS/HTTP 混合内容问题

2. **路径问题**：
   - 相对路径 vs 绝对路径
   - baseURL 配置

## 推荐解决方案

### 方案一：使用本地图片（推荐）

#### 1. 创建图片目录
```
/static/
└── images/
    └── cover1.jpg    # 你的封面图片
```

#### 2. 在文章 Front Matter 中配置
```yaml
---
title: 文章标题
cover:
  image: "/images/cover1.jpg"
  hidden: false
  hiddenInList: false
  hiddenInSingle: false
---
```

#### 3. 优点
- ✅ 稳定，不受外部服务影响
- ✅ 不会有 CORS 问题
- ✅ 图片资源与代码一起管理
- ✅ 可以使用 Hugo 的图片处理功能

---

### 方案二：使用可靠的外部图床

如果必须使用外部链接：
- ✅ 使用 GitHub 仓库自己托管的图片（raw.githubusercontent.com）
- ✅ 使用 Imgur、Cloudinary 等稳定图床
- ✅ 确保链接是 HTTPS

示例：
```yaml
cover:
  image: "https://raw.githubusercontent.com/你的用户名/仓库名/main/images/cover.jpg"
```

---

### 方案三：使用 Page Bundle 组织

把图片和文章放在同一个目录：

```
/content/
└── posts/
    └── my-post/
        ├── index.md
        └── cover.jpg
```

配置：
```yaml
cover:
  image: "cover.jpg"
  relative: true
```

---

## 当前配置检查

### ✅ 已修复的问题
1. `hugo.yaml` 中 cover 配置的缩进错误
2. 启用了封面显示

### 📋 下一步操作

1. **准备封面图片**，放到 `/static/images/` 目录
2. **更新文章配置**，把外部链接替换为本地路径
3. **测试本地预览**，确保正常显示
4. **提交并推送**到 GitHub

---

## PaperMod 封面处理逻辑（源代码分析）

根据 [PaperMod 模板](themes/PaperMod/layouts/_partials/cover.html)：

```go
{{- $imgdl := (.Params.cover.image) | absURL }}
```

- PaperMod 会自动用 `absURL` 处理图片地址
- 如果图片在 `static/` 目录，会正确映射
- 如果是外部链接，会原样使用

---

## 快速测试

要验证 GitHub Pages 上是否工作：

1. 本地构建测试：
```bash
hugo --minify
```

2. 检查生成的 `public/` 目录中图片引用是否正确

---

## 故障排除

### 1. 图片路径错误
检查浏览器开发者工具 Network 面板，看图片请求是否 404

### 2. CORS 问题
检查 Console 是否有跨域错误，换成本地图片解决

### 3. baseURL 问题
确保 `hugo.yaml` 中的 `baseURL` 与你的 GitHub Pages 地址一致：
```yaml
baseURL: "https://rboyy.github.io/"
```
