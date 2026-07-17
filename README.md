# Guoqiang Jia — Academic Homepage

这是 Guoqiang Jia 的学术个人主页源码，线上地址：[https://iqiang111.github.io](https://iqiang111.github.io/)。

站点基于 Jekyll 和 [Minimal Light](https://github.com/yaoyao-liu/minimal-light) 构建，由 GitHub Pages 自动生成和发布。

## 站点内容

- 学术主页：个人简介、研究方向、教育经历和联系方式。
- Weekly：使用 Markdown 记录每周进展、复盘和下一步计划。
- 自动适配桌面端、移动端以及系统深色模式。

主页不显示 Weekly 内容或导航。点击主页头像下方的姓名可进入 Weekly；在 Weekly 页面点击头像或姓名可返回主页。

> 隐藏入口只降低了被随手发现的概率，并不提供访问控制。公开仓库中的 Markdown 和 GitHub Pages 页面仍可通过直接 URL 访问，不应写入敏感信息。

## 目录结构

```text
.
├── index.md                  # 学术主页内容
├── _config.yml              # 站点和 GitHub Pages 配置
├── _weekly/                 # 已发布的周记
├── _templates/weekly.md     # 新周记模板
├── weekly/index.html        # Weekly 归档页
├── _layouts/                # 主页与周记页面布局
├── _sass/                   # 主题和 Weekly 样式
└── assets/                  # 字体、头像、favicon 和脚本
```

## 更新学术主页

编辑根目录的 `index.md`。Weekly 功能不需要、也不会向该文件插入内容。

## 发布一篇 Weekly

1. 复制模板，并用发布日期命名：

   ```powershell
   Copy-Item _templates/weekly.md _weekly/2026-07-24.md
   ```
2. 编辑文件头：

   ```yaml
   ---
   title: "这一周的主题"
   date: 2026-07-24
   period: "2026.07.20 — 2026.07.26"
   summary: "一两句话概括本周最重要的进展或变化。"
   tags:
     - Weekly
   ---
   ```

   文件名应与 `date` 保持一致。以上示例发布后地址为 `/weekly/2026-07-24/`。`period` 和 `tags` 可以删除。
3. 按三个固定部分写正文：

   - `本周进展`：把行动、当前状态和结果写在一起。
   - `复盘与调整`：记录有效做法、问题或时间损失，以及准备进行的调整。
   - `下周计划`：只保留可以明确验证是否完成的事项。
4. 提交并推送：

   ```powershell
   git add .
   git commit -m "weekly: add 2026-07-24"
   git push origin main
   git push iqiang111.github.io main
   ```

GitHub Pages 会自动更新 Weekly 归档页和文章详情页，不需要提交生成后的 HTML。

## 主要配置

个人信息、社交链接、头像、深色模式和 Weekly collection 均在 `_config.yml` 中维护。当前周记永久链接规则为：

```yaml
collections:
  weekly:
    output: true
    permalink: /weekly/:name/
```

## License

本项目沿用 [CC0 1.0 Universal](LICENSE) 许可。
