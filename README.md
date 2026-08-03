# Codex Work themes for Gitea

为 Gitea 1.27.x 设计的 Codex / ChatGPT Work 风格主题集合。默认推荐 `codex-work-unified`：使用暖石墨色分层、清晰边界和克制的青绿色交互色，面向长时间编码和代码审查。

## 设计目标

- **长时间阅读舒适**：避免纯黑背景，以暖石墨色建立低眩光层级。
- **开发信息优先**：仓库文件、工单、合并请求、Actions 和设置页都保留 Gitea 原有信息密度。
- **少装饰、强层级**：普通内容依靠间距和细边框分层，只给浮层使用阴影。
- **宽屏不过度拉伸**：代码仓库最大宽度 1320px，首页动态最大宽度 1180px。
- **可访问性**：保留清晰焦点环、可辨识状态色和 `prefers-reduced-motion` 支持。

## 文件

```text
codex-work-unified/
└── theme-codex-work-unified.css

chatgpt-work/
└── theme-chatgpt-work.css
```

- `codex-work-unified`：推荐的暗色主题；独立名称用于绕开旧 CSS 的长缓存。
- `chatgpt-work`：上一版浅色主题，保留为可选方案。

每个大版本使用独立主题名，避免 Gitea 对同名主题静态资源的长时间缓存影响升级。

## 安装

将主题放入 Gitea 的 custom 目录：

```bash
install -m 0644 codex-work-unified/theme-codex-work-unified.css \
  /data/gitea/public/assets/css/theme-codex-work-unified.css
```

在 `app.ini` 的 `[ui]` 段注册并设为默认主题：

```ini
[ui]
DEFAULT_THEME = codex-work-unified
THEMES = codex-work-unified,chatgpt-work,openai-theme,gitea-light,gitea-dark,gitea-auto
```

配置发生变化时需要重启 Gitea。仅替换已经注册的 CSS 文件时，刷新浏览器即可看到新版本；如果浏览器命中旧缓存，请强制刷新。

## 兼容性

- 目标版本：Gitea 1.27.x
- 主题类型：浅色
- 浏览器：现代 Chromium、Firefox、Safari

## 回滚

部署前保留当前文件副本：

```bash
cp theme-codex-work-unified.css theme-codex-work-unified.css.bak.$(date +%Y-%m-%d-%H%M)
```

需要回滚时将 `DEFAULT_THEME` 改回 `chatgpt-work`、`openai-theme` 或内置主题，或将备份文件复制回 `theme-codex-work-unified.css`，然后重启 Gitea。
