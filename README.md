# Agent 全栈手册

AI Agent 全栈工程面试手册——覆盖 Agent 原理、工具/MCP、RAG、Memory、评测、流式交互、后端架构与源码深挖,261 道题都给出可口述、可追问的实战答案。

线上:<https://agent-guide-8js.pages.dev/>

## 结构

```
index.html            单文件应用(内联 CSS + JS,数据在 JS 的 chapters / productionDeepDive* 数组)
favicon.svg           站点图标(「图节点构成的 A」logo)
apple-touch-icon.png  iOS 主屏图标(由 src/icon.html 渲染)
og.png                社交分享卡片 1200×630(由 src/og.html 渲染)
src/og.html           OG 卡片渲染源
src/icon.html         apple-touch-icon 渲染源
```

单文件、零构建、零依赖,直接用浏览器打开 `index.html` 即可。

## 本地预览

```bash
python3 -m http.server 8080   # 然后访问 http://127.0.0.1:8080/
```

## 部署(Cloudflare Pages)

```bash
npx wrangler pages deploy . --project-name agent-guide --branch main
```

`.assetsignore` 已排除 `src/` 与文档,不会被发布。

## 重新生成 OG / icon 图

改完 `src/og.html` 或 `src/icon.html` 后,用无头浏览器渲染截图:

```bash
python3 -m http.server 8080
# OG: 视口 1200×630 截 src/og.html → og.png
# icon: 视口 180×180 截 src/icon.html → apple-touch-icon.png
```

## 设计

- 视觉:暖白纸底 + 石墨墨色 + 朱红主强调 + 靛蓝次强调,Space Grotesk(拉丁/数字)+ 苹方(中文)。
- 布局:顶栏(logo + 横滑章节导航)+ 居中单栏宽阅读。
- 答案范式:「判断先行的金字塔」——先给可被反驳的取舍判断,再 2-4 个带证据的支柱,取舍单独成段,结尾留追问钩子。
