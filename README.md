# 自行车骑鹈鹕 · odd little journeys

> 让模型，载我们去。

一册不断生长的 AI 生成作品集。每个词条都是一次生成模型的实验：一帧会动的、不太合理的小场面，配上一句漫不经心的注脚。

当前由 **GitHub Actions** 自动部署到 **GitHub Pages**。

## 📖 在线阅读

访问 GitHub Pages：<https://<你的用户名>.github.io/<仓库名>/>

## 📁 项目结构

```text
.
├── index.html                  # 主页 · 作品集画廊（数据驱动，核心入口）
├── README.md
└── .github/
    └── workflows/
        └── deploy.yml          # GitHub Pages 自动部署工作流
```

作品页面建议放在 `works/xxx/index.html`（例如 `works/gpt6astra/index.html`），主页通过相对链接指向它们。GitHub Pages 的根目录就是仓库根目录，因此相对路径即可正常访问。

## 🆕 如何新增作品

1. 把你生成的作品页面保存到仓库，例如 `works/新作品名/index.html`。
2. 打开 `index.html`，在页面底部脚本的 `works` 数组里新增一条记录：

   ```js
   {
     num: 'NO. 002',                       // 编号
     title: '作品标题',                     // 可用 <span class="coral">…</span> 着色
     desc: '一行简短的介绍文字',
     link: 'works/新作品名/index.html',     // 相对链接
     model: 'GPT-6 ASTRA',                 // 生成该作品的模型名称
     thumb: 'pelican'                      // 预览图标识，见下方说明
   }
   ```

3. `thumb` 字段对应 `thumbScope` 对象里的内联 SVG 缩略图。内置了 `pelican` 一款；如需新增预览图，在 `thumbScope` 里按同样方式添加一个标识即可（也可替换为自制的 SVG / 图片）。
4. 推送到 `main` 分支，便会自动构建并部署。

保存后保存即可刷新主页预览效果；链接与标题会自动生成到画廊卡片上。

## 🚀 在 GitHub 上启用 GitHub Pages

首次部署需要先把仓库 Pages 来源设为 **GitHub Actions**：

1. 将本仓库推送到 GitHub（见下方「部署流程」）。
2. 打开仓库 **Settings → Pages**。
3. 在 **Build and deployment → Source** 处选择 **GitHub Actions**（无需小动作别的，工作流会接管）。
4. 稍等片刻，Actions 里的 `Deploy to GitHub Pages` 完成后即可通过 `https://<用户名>.github.io/<仓库名>/` 访问。

之后每次推送到 `main`，都会自动重新部署。

## 📤 部署流程

仓库刚开始未初始化 git、也没有 GitHub 远端。按下面步骤走一遍即可完成首次发布（需要 GitHub 账号，命令行未安装 `gh` 时也可用网页方式创建仓库后推送）：

```bash
# 1. 初始化并提交
git init
git add .
git commit -m "init: 自行车骑鹈鹕 作品集 + 主页 + Pages 工作流"

# 2. 关联远程仓库（把下面的地址换成你实际创建的仓库）
git remote add origin https://github.com/<用户名>/<新仓库名>.git
git branch -M main
git push -u origin main

# 3. 去仓库 Settings → Pages 把 Source 设为 GitHub Actions 即可
```

## ✨ 当前收录

| No. | 作品 | 模型 | 说明 |
| --- | --- | --- | --- |
| 001 | 今天，换你载我。 | GPT-6 Astra | 会动的动画：自行车骑着鹈鹕飞过海面，可切换日夜、调速、乘风加速 |

---

一点想象力，一场轻盈的出逃。**DRAWN IN CODE · 自行车骑鹈鹕**