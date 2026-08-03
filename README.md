# ChatGPT Work theme for Gitea

一套为 Gitea 1.27.x 从零设计的浅色工作台主题。它借鉴 ChatGPT 与 Codex 的视觉克制，但不复制产品界面：暖灰画布、白色工作面、清晰文字层级、低噪声边框，以及仅用于关键交互的低饱和绿色。

## 设计目标

- **长时间阅读舒适**：避免纯黑或纯白大面积高反差，正文和代码保持清楚。
- **开发信息优先**：仓库文件、工单、合并请求、Actions 和设置页都保留 Gitea 原有信息密度。
- **少装饰、强层级**：普通内容依靠间距和细边框分层，只给浮层使用阴影。
- **宽屏不过度拉伸**：代码仓库最大宽度 1320px，首页动态最大宽度 1180px。
- **可访问性**：保留清晰焦点环、可辨识状态色和 `prefers-reduced-motion` 支持。

## 文件

```text
chatgpt-work/
└── theme-chatgpt-work.css
```

主题名为 `chatgpt-work`。它使用独立文件名，避免 Gitea 对旧主题静态资源的长时间缓存影响升级，也不会覆盖已有主题的回滚文件。

## 安装

将主题放入 Gitea 的 custom 目录：

```bash
install -m 0644 chatgpt-work/theme-chatgpt-work.css \
  /data/gitea/public/assets/css/theme-chatgpt-work.css
```

在 `app.ini` 的 `[ui]` 段注册并设为默认主题：

```ini
[ui]
DEFAULT_THEME = chatgpt-work
THEMES = chatgpt-work,openai-theme,gitea-light,gitea-dark,gitea-auto
```

配置发生变化时需要重启 Gitea。仅替换已经注册的 CSS 文件时，刷新浏览器即可看到新版本；如果浏览器命中旧缓存，请强制刷新。

## 兼容性

- 目标版本：Gitea 1.27.x
- 主题类型：浅色
- 浏览器：现代 Chromium、Firefox、Safari

## 回滚

部署前保留当前文件副本：

```bash
cp theme-chatgpt-work.css theme-chatgpt-work.css.bak.$(date +%Y-%m-%d-%H%M)
```

需要回滚时将 `DEFAULT_THEME` 改回原主题，或将备份文件复制回 `theme-chatgpt-work.css`，然后重启 Gitea。
