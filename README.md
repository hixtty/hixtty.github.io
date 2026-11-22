# Hixtty 的博客

个人博客，使用 [Hugo](https://gohugo.io/) + [Stack](https://github.com/CaiJimmy/hugo-theme-stack) 构建，
通过 GitHub Actions 自动部署到 GitHub Pages。

- 站点地址：<https://hixtty.github.io/>
- 主题版本：Stack v4（由 Hugo Modules 管理）

## 本地开发

需要：

- Git
- [Hugo extended](https://gohugo.io/installation/)（主题要求 0.157.0 及以上）
- [Dart Sass](https://github.com/sass/dart-sass/releases)（Stack 主题编译 SCSS 需要）
- Go（Hugo Modules 拉取主题时需要）

Windows 安装 Hugo：

```powershell
winget install --id Hugo.Hugo.Extended --exact
```

Dart Sass 下载 `windows-x64.zip` 后解压，把包含 `sass.bat` 的目录加入 `PATH`。

启动本地预览：

```bash
hugo server -D
```

默认地址是 <http://localhost:1313/>。

## 写文章

```bash
hugo new content post/my-new-post/index.md
```

新文章默认是草稿（`draft: true`），本地用 `hugo server -D` 可以预览，发布前把 `draft` 改成 `false`。

把封面图放在同一目录，并在 front matter 里写 `image: cover.jpg` 即可。

## 配置位置

- `config/_default/config.toml`：站点地址、标题、语言
- `config/_default/params.toml`：侧边栏、首页组件、评论等
- `config/_default/menu.toml`：社交链接
- `content/page/`：关于、归档、搜索、友链等独立页面

## 部署

推送到 `main` 分支后，`.github/workflows/deploy.yml` 会自动构建并发布到 GitHub Pages。

首次使用时，需要在仓库 `Settings -> Pages -> Build and deployment -> Source` 选择 `GitHub Actions`。

## 更新主题

```bash
hugo mod get -u github.com/CaiJimmy/hugo-theme-stack/v4
hugo mod tidy
```

主题基于 GPL-3.0 许可，页脚的 “Theme Stack designed by Jimmy” 署名请保留。
