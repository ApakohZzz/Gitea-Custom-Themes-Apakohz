# gitea-apokoh-themes

自用 Gitea 自定义主题集合，针对 Gitea 1.27.x。

## openai-theme

OpenAI 2026 品牌视觉风格的深色主题。

- 配色：纯黑底 `#0f0f0f` + 中性灰白主色 `#ececf1`（OpenAI 2026-05 改版后已弃用绿色作为主色，仅保留为历史签名色）
- 字体：Inter（OpenAI Sans 未公开时的最佳开源替代）+ JetBrains Mono
- 组件：胶囊按钮（9999px）、14px 大圆角卡片、扁平+hover 浮起、精准命中 `.overflow-menu-items` 分段控件
- 图标：统一 16px，Gitea 茶 logo 灰度化融入单色体系
- 动效：页面淡入、下拉弹出、卡片 hover 上浮、输入框聚焦光环

### 安装

```bash
# 1. 放置主题文件到 Gitea custom 目录
# Docker 部署：容器内 /data/gitea/public/assets/css/
# 二进制部署：$GITEA_CUSTOM/public/assets/css/
curl -L -o theme-openai-theme.css https://raw.githubusercontent.com/ApakohZzz/gitea-apokoh-themes/main/openai-theme/theme-openai-theme.css
cp theme-openai-theme.css /path/to/gitea/custom/public/assets/css/

# 2. 在 app.ini 的 [ui] 段注册
# [ui]
# DEFAULT_THEME = openai-theme
# THEMES = openai-theme,gitea-light,gitea-dark,gitea-auto

# 3. 重启 Gitea（Docker: docker restart gitea）
```

文件名 `theme-openai-theme.css` 对应主题名 `openai-theme`。
