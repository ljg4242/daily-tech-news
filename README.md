# 每日科技资讯

自动抓取 14 个科技 RSS 源，并生成中文简讯后发布为静态站。

## 运行原理（简版）

当前流水线采用 **脚本主导、AI 只负责改写** 的方式：

1. 抓取脚本从 14 个 RSS 源获取新增文章
2. 将单站原始数据写入临时文件
3. AI 只生成 `rewrites JSON`（中文标题 + 中文简讯）
4. 脚本把改写结果套回原始数据
5. 由脚本统一合并到 `data/YYYY-MM-DD.json`
6. 重建 `data/index.json`，然后 `git commit` / `git push`

也就是说：

- **AI 不直接写站点文件**
- **最终 JSON 的写入、合并、索引更新、推送都由脚本完成**

这样可以避免模型误把当天数据写成空骨架或覆盖旧数据。

## 数据

- `data/YYYY-MM-DD.json` — 每日一期，包含「主要」和「更多」两个板块
- `data/index.json` — 可用日期索引

## 数据源

**主要：** MacRumors, 9to5Mac, 9to5Google, Ars Technica, Android Authority, Engadget, The Verge

**更多：** IGN, Solidot, 小众软件, 蓝点网, cnBeta, 36氪, IT之家

## 技术栈

- 数据采集：RSS + Python 脚本
- 中文改写：AI（当前使用 OpenClaw 默认模型）
- 数据落盘与推送：Python 脚本 + Git
- 托管：Vercel（静态站）
