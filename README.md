# 我的博客（Hexo + GitHub Pages）

基于 Hexo 8 的静态博客，使用 **Landscape** 主题，通过 **GitHub Actions** 自动部署到 GitHub Pages（用户页）。

## 本地预览

```bash
npm install        # 首次或加依赖后
npx hexo server    # 本地预览，默认 http://localhost:4000
```

> 依赖已经安装好，直接 `npx hexo server` 即可。

## 写新文章

```bash
npx hexo new "文章标题"
```

生成在 `source/_posts/文章标题.md`，用 Markdown 编写即可。

## 部署到 GitHub Pages（只需做一次）

1. 在 GitHub 新建仓库，名称**必须**为 `<你的用户名>.github.io`（例如用户名 `octocat` → 仓库名 `octocat.github.io`）。
2. 打开 `_config.yml`，把第 16 行左右的

   ```yaml
   url: https://YOUR_GITHUB_USERNAME.github.io/
   ```

   改成你的真实用户名，例如 `url: https://octocat.github.io/`。
3. 在本地博客目录下连接远程仓库并推送（本仓库已 `git init` 并提交）：

   ```bash
   git remote add origin https://github.com/<你的用户名>/<你的用户名>.github.io.git
   git branch -M main
   git push -u origin main
   ```

4. 推送后进入仓库 **Settings → Pages → Build and deployment → Source**，选择 **GitHub Actions**。
5. 等待 Actions 构建完成（Actions 标签页可见进度），随后访问 `https://<你的用户名>.github.io/` 即可。

之后每次改完文章，只需 `git add -A && git commit -m "更新" && git push`，部署会自动完成。

## 目录说明

- `source/_posts/`：你的文章（Markdown）
- `themes/landscape`（由 npm 包 `hexo-theme-landscape` 提供）与 `_config.landscape.yml`：主题配置
- `.github/workflows/pages.yml`：自动构建并发布到 Pages 的工作流

## 换主题（可选）

如需更换为 Butterfly / NexT / Fluid 等，安装主题 npm 包后修改 `_config.yml` 的 `theme:` 字段即可，部署流程不变。
