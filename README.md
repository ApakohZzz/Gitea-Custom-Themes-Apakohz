# Codex themes for Gitea

为 Gitea 1.27.x 设计的 Codex 风格明暗双主题。默认使用 `codex-dark`：暖石墨色分层、清晰边界和克制的青绿色交互色，适合长时间编码和代码审查；`codex-light` 提供温和明亮的配套外观。

## 设计目标

- **长时间阅读舒适**：避免纯黑背景，以暖石墨色建立低眩光层级。
- **开发信息优先**：仓库文件、工单、合并请求、Actions 和设置页都保留 Gitea 原有信息密度。
- **少装饰、强层级**：普通内容依靠间距和细边框分层，只给浮层使用阴影。
- **宽屏不过度拉伸**：代码仓库最大宽度 1320px，首页动态最大宽度 1180px。
- **可访问性**：保留清晰焦点环、可辨识状态色和 `prefers-reduced-motion` 支持。

## 文件

```text
codex-dark/
└── theme-codex-dark.css

codex-light/
└── theme-codex-light.css
```

- `codex-dark`：默认暗色主题，显示名称为 “Codex Dark”。
- `codex-light`：配套浅色主题，显示名称为 “Codex Light”。

每个大版本使用独立主题名，避免 Gitea 对同名主题静态资源的长时间缓存影响升级。

## 安装

将主题放入 Gitea 的 custom 目录：

```bash
install -m 0644 codex-dark/theme-codex-dark.css \
  /data/gitea/public/assets/css/theme-codex-dark.css
install -m 0644 codex-light/theme-codex-light.css \
  /data/gitea/public/assets/css/theme-codex-light.css
```

在 `app.ini` 的 `[ui]` 段注册并设为默认主题：

```ini
[ui]
DEFAULT_THEME = codex-dark
THEMES = codex-dark,codex-light,openai-theme,gitea-light,gitea-dark,gitea-auto
```

配置发生变化时需要重启 Gitea。仅替换已经注册的 CSS 文件时，刷新浏览器即可看到新版本；如果浏览器命中旧缓存，请强制刷新。

## 兼容性

- 目标版本：Gitea 1.27.x
- 主题类型：暗色
- 浏览器：现代 Chromium、Firefox、Safari

## 回滚

部署前保留当前文件副本：

```bash
cp theme-codex-dark.css theme-codex-dark.css.bak.$(date +%Y-%m-%d-%H%M)
cp theme-codex-light.css theme-codex-light.css.bak.$(date +%Y-%m-%d-%H%M)
```

需要回滚时将 `DEFAULT_THEME` 改回 `openai-theme` 或内置主题，或将备份文件复制回 `theme-codex-dark.css` / `theme-codex-light.css`，然后重启 Gitea。
