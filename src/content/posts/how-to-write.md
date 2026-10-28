---
title: 这个博客怎么写文章
published: 2026-10-23
description: 给自己留的备忘：文章放哪、开头那段配置能写什么、支持哪些语法。忘了就回来翻。
tags: [备忘, 使用方法]
category: 随笔
---

写给未来的自己。免得每次想发文章都要翻文档。

## 文章放在哪

```
src/content/posts/
```

新建一个 `.md` 文件就是一篇新文章。文件名最好是英文，会成为网址的一部分。

也可以用命令行创建（会带上模板）：

```bash
pnpm new-post my-new-post
```

## 开头那段配置

每篇文章最上面夹在 `---` 之间的部分，叫 frontmatter。最少只要两行：

```yaml
---
title: 文章标题
published: 2026-10-23
---
```

常用的还有这些：

| 字段 | 作用 |
|---|---|
| `title` | 标题，必填 |
| `published` | 发布日期，必填 |
| `description` | 摘要，显示在列表卡片和搜索结果里 |
| `tags` | 标签，写成 `[标签1, 标签2]` |
| `category` | 分类，只能填一个 |
| `image` | 封面图，相对路径，比如 `./images/cover.avif` |
| `pinned` | 设为 `true` 就置顶 |
| `draft` | 设为 `true` 就只是草稿，不会发布 |
| `password` | 设置后文章需要密码才能看 |

## 正文能写什么

普通 Markdown 都支持：标题、列表、表格、链接、加粗、引用。

**代码块**会带语法高亮和行号：

````markdown
```js
console.log("hello");
```
````

**提示框**用 GitHub 的写法：

```markdown
> [!NOTE]
> 这是一条提示。

> [!WARNING]
> 这是一条警告。
```

**数学公式**用 `$` 包裹，行内 `$a^2 + b^2 = c^2$`，独立成行用两个美元符号。

**图表**支持 Mermaid 和 PlantUML，写代码块时语言填 `mermaid` 或 `plantuml` 就行。

## 图片放哪

在文章同目录下建个 `images` 文件夹，图片丢进去，正文里这样引用：

```markdown
![说明文字](./images/1.avif)
```

构建时会自动压缩成 WebP，不用自己处理。

## 改完怎么发布

改完推送到 GitHub，托管平台会自动重新构建，一两分钟后线上就更新了。

本地想看效果就先跑 `pnpm dev`，改文件浏览器会自动刷新。
