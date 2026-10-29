# Xiaohan 的个人主页

这是 Xiaohan 的个人主页，使用 Jekyll 构建并部署在 GitHub Pages。

- 线上地址：<https://xiaohan66652.github.io/xiaohan-66652.github.io/>
- GitHub：<https://github.com/xiaohan66652>
- 主题来源：[Hux Blog](https://github.com/Huxpro/huxpro.github.io)

## 页面结构

- `index.html`：首页，包含个人介绍、关注方向、项目、文章和联系方式。
- `about.html`：关于页，中英文内容分别存放在 `_includes/about/zh.md` 和 `_includes/about/en.md`。
- `_posts/`：文章目录。目前已放入两篇起步文章，可以继续添加 Markdown 文件。
- `_config.yml`：站点名称、简介、邮箱、GitHub 用户名和部署路径。
- `css/personalize.css`：个人主页新增的视觉样式，方便后续统一调整。
- `laser-calculator.html`：超快激光参数计算器，线上地址为 `/laser-calculator/`。
- `_doc/demo-content/`：原主题附带的示例文章和素材，仅作参考，不会参与网站构建。

## 常用修改

修改站点简介、邮箱或社交账号时，编辑 `_config.yml`：

```yml
title: Xiaohan
description: "Xiaohan 的个人主页，记录学习、项目与思考。"
email: xiaohan66652@hotmail.com
github_username: xiaohan66652
```

当前仓库不是 `xiaohan66652.github.io` 这个用户根仓库，而是名为 `xiaohan-66652.github.io` 的项目仓库，因此以下配置必须保持：

```yml
url: "https://xiaohan66652.github.io"
baseurl: "/xiaohan-66652.github.io"
```

如果以后把仓库改名为 `xiaohan66652.github.io`，线上地址会变成 `https://xiaohan66652.github.io/`，那时需要把 `baseurl` 改成空字符串。

## 添加文章

在 `_posts/` 中新建文件名格式为 `YYYY-MM-DD-title.md` 的文件：

```markdown
---
layout: post
title: "文章标题"
subtitle: "一句简短介绍"
date: 2026-10-30 10:00:00 +0800
author: Xiaohan
header-img: "img/home-bg-o.jpg"
header-mask: 0.42
tags:
    - 学习笔记
---

正文从这里开始。
```

文章会自动出现在首页的“最近写下的文字”和“文章”页面，也会进入站内搜索。

## 添加一个独立工具页

像激光计算器这样的独立 HTML 工具，可以放在项目根目录，并在文件最上方加入：

```yaml
---
layout: null
permalink: /laser-calculator/
---
```

`layout: null` 表示不使用博客的默认排版，`permalink` 用来指定访问地址。HTML 内的 CSS 和 JavaScript 可以直接保留。

如果工具在子目录中，资源路径要相对于工具文件本身；需要链接回主页时，使用：

```html
<a href="{{ site.baseurl }}/">返回个人主页</a>
```

完成后，在 `index.html` 的“正在生长的项目”区域增加一个链接，再像下面这样提交即可。

## Git 与 GitHub

本仓库已经设置好远程地址、提交身份和 Git Credential Manager。以后修改完网站，在项目文件夹中打开 PowerShell，依次运行：

```sh
git status
git add -A
git commit -m "说明这次修改了什么"
git push
```

第一次推送时，如果弹出 GitHub 登录窗口，选择 `Sign in with your browser` 并在浏览器中登录你的账号。授权成功后，Git 会保存登录状态。

常用检查命令：

```sh
git status       # 查看哪些文件改了
git log --oneline -5
git remote -v
```

正常更新只需 `git push`，不要习惯性使用 `git push --force`。强制推送会覆盖远程历史，只适合确认远程内容可以完全替换的情况。

## 本地预览

需要先安装 Ruby 和 Bundler，然后运行：

```sh
bundle install
bundle exec jekyll serve
```

浏览器打开 <http://127.0.0.1:4000/xiaohan-66652.github.io/>。

## 发布

将修改后的文件推送到 GitHub 仓库的默认分支，并在仓库 `Settings → Pages` 中确认发布来源为对应的分支和根目录。GitHub Pages 完成构建后，访问线上地址即可。
