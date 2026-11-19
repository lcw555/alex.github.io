# lcw555.github.io

个人博客源码。Astro + Fuwari 主题，GitHub Actions 自动部署到 GitHub Pages。

线上地址：https://lcw555.github.io

## 写一篇新文章

在 `src/content/posts/` 下新建 `.md` 文件，开头写 frontmatter：

```markdown
---
title: 文章标题
published: 2026-11-19
description: 一句话摘要，会显示在列表和 SEO 里
tags: [标签1, 标签2]
category: 分类
draft: false
---
```

`draft: true` 的文章不会发布。写完 commit 到 `main`，一分钟内自动上线。

也可以本地跑：

```bash
pnpm install
pnpm new-post   # 按提示生成模板文件
pnpm dev        # 本地预览 http://localhost:4321
```

## 站点信息配置

大部分个人信息都在 `src/config.ts` 里：站名、副标题、头像、导航栏、社交链接、主题色。

- 头像：`public/avatar.svg`
- 站点图标：`public/favicon.svg`
- 站点域名：`astro.config.mjs` 的 `site` 字段
- 关于页：`src/content/spec/about.md`

## 部署

推送到 `main` 触发 `.github/workflows/deploy.yml`：装依赖 → 构建 → 上传 artifact → 发布到 Pages。

依赖锁定在 `pnpm-lock.yaml`，CI 用 `--frozen-lockfile` 安装；升级依赖请本地 `pnpm update` 后一并提交锁文件。

首次使用需在仓库 **Settings › Pages › Source** 选择 **GitHub Actions**。

## 致谢

主题来自 [Fuwari](https://github.com/saicaca/fuwari)（MIT）。
