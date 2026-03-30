# 每日科技资讯

自动抓取 14 个科技 RSS 源，AI 生成中文简讯。

## 数据

`data/YYYY-MM-DD.json` — 每日一期，包含「优选站点」和「更多」两个板块。

## 数据源

**优选站点：** MacRumors, 9to5Mac, 9to5Google, Ars Technica, Android Authority, Engadget, The Verge

**更多：** IGN, Solidot, 小众软件, 蓝点网, cnBeta, 36氪快讯, IT之家

## 技术栈

- 数据采集：OpenClaw Agent + RSS
- 简讯生成：AI（MiMo）
- 托管：Vercel（静态站）
