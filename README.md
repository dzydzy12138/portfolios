# Yzd 作品集

Yzd 的建模设计师个人主页，使用 Vue 3、TypeScript 和 Vite 构建。

网站地址：<https://dzydzy12138.github.io/portfolios/>

推送到 `main` 分支后，GitHub Actions 会自动构建并发布网站。

## 本地运行

```sh
npm install
npm run dev
```

## 生产构建

```sh
npm run build
```

## GitHub Pages

在 GitHub 仓库的 **Settings → Pages → Build and deployment** 中，将 **Source** 设为 **GitHub Actions**。之后每次推送到 `main` 都会自动发布；首次部署完成后可通过上方网站地址访问。

## 更新作品集

在 `src/App.vue` 的 `projects` 列表中添加真实项目。作品卡片、空状态和项目总数会根据列表内容自动更新。
