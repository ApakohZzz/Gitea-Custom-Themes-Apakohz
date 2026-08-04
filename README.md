# Codex themes for Gitea

[中文](#中文) · [English](#english)

## 中文

为 Gitea 1.27.x 设计的 Codex 风格明暗双主题。默认使用 `codex-dark`：暖石墨色分层、清晰边界和克制的青绿色交互色，适合长时间编码和代码审查；`codex-light` 使用同一套布局、交互和响应式规则，提供温和明亮的配套外观。

### 设计目标

- **长时间阅读舒适**：暗色模式避免纯黑背景，浅色模式使用低对比暖灰画布。
- **开发信息优先**：仓库文件、工单、合并请求、Actions 和设置页都保留 Gitea 原有信息密度。
- **少装饰、强层级**：普通内容依靠间距和细边框分层，只给浮层使用阴影。
- **宽屏不过度拉伸**：代码仓库最大宽度 1320px，首页动态最大宽度 1180px。
- **明暗模式结构一致**：两个主题共享卡片、菜单、控件、圆角、间距和响应式修复，仅视觉色板不同。
- **可访问性**：保留清晰焦点环、可辨识状态色和 `prefers-reduced-motion` 支持。

### 文件

```text
codex-dark/
└── theme-codex-dark.css

codex-light/
└── theme-codex-light.css
```

- `codex-dark`：默认暗色主题，显示名称为 “Codex Dark”。
- `codex-light`：配套浅色主题，显示名称为 “Codex Light”。

### 安装

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

### 兼容性

- 目标版本：Gitea 1.27.x
- 主题类型：明暗双主题
- 浏览器：现代 Chromium、Firefox、Safari

### 回滚

部署前保留当前文件副本：

```bash
cp theme-codex-dark.css theme-codex-dark.css.bak.$(date +%Y-%m-%d-%H%M)
cp theme-codex-light.css theme-codex-light.css.bak.$(date +%Y-%m-%d-%H%M)
```

需要回滚时将 `DEFAULT_THEME` 改回 `openai-theme` 或内置主题，或将备份文件复制回 `theme-codex-dark.css` / `theme-codex-light.css`。配置有变化时再重启 Gitea。

## English

Codex-inspired light and dark themes for Gitea 1.27.x. `codex-dark` is the default, with warm graphite layers, clear boundaries, and a restrained teal interaction color for long coding and review sessions. `codex-light` uses the same layout, interaction, and responsive rules with a calm light palette.

### Design goals

- **Comfortable for long sessions**: the dark theme avoids pure black, while the light theme uses a low-contrast warm-gray canvas.
- **Development content first**: repositories, issues, pull requests, Actions, and settings retain Gitea's native information density.
- **Minimal decoration, strong hierarchy**: spacing and quiet borders separate normal content; shadows are reserved for floating surfaces.
- **Controlled width on large screens**: repository content is capped at 1320px and dashboard activity at 1180px.
- **Consistent light and dark structure**: both themes share the same card, menu, control, radius, spacing, and responsive fixes; only the visual palette changes.
- **Accessible interaction**: clear focus rings, distinguishable status colors, and `prefers-reduced-motion` support are preserved.

### Files

```text
codex-dark/
└── theme-codex-dark.css

codex-light/
└── theme-codex-light.css
```

- `codex-dark`: the default dark theme, displayed as “Codex Dark”.
- `codex-light`: the matching light theme, displayed as “Codex Light”.

### Installation

Copy both stylesheets into Gitea's custom directory:

```bash
install -m 0644 codex-dark/theme-codex-dark.css \
  /data/gitea/public/assets/css/theme-codex-dark.css
install -m 0644 codex-light/theme-codex-light.css \
  /data/gitea/public/assets/css/theme-codex-light.css
```

Register the themes in the `[ui]` section of `app.ini` and choose the default:

```ini
[ui]
DEFAULT_THEME = codex-dark
THEMES = codex-dark,codex-light,openai-theme,gitea-light,gitea-dark,gitea-auto
```

Restart Gitea after changing its configuration. When only replacing an already registered CSS file, refresh the browser; use a hard refresh if an older static asset is still cached.

### Compatibility

- Target: Gitea 1.27.x
- Theme variants: light and dark
- Browsers: modern Chromium, Firefox, and Safari

### Rollback

Keep timestamped copies before deployment:

```bash
cp theme-codex-dark.css theme-codex-dark.css.bak.$(date +%Y-%m-%d-%H%M)
cp theme-codex-light.css theme-codex-light.css.bak.$(date +%Y-%m-%d-%H%M)
```

To roll back, select `openai-theme` or a built-in theme as `DEFAULT_THEME`, or restore the backup over `theme-codex-dark.css` / `theme-codex-light.css`. Restart Gitea only if its configuration changed.
