# JourneyMind Blog

JourneyMind 是 mi179 的个人项目与技术笔记站，基于 Hexo，部署到 Cloudflare Pages。

## 本地开发

```bash
npm ci
npm run build
npm run preview
```

## Cloudflare Pages

- Repository: `mi179/cf-pages-blog`
- Production branch: `master`
- Build command: `npm ci && npm run build`
- Build output directory: `public`
- Custom domain: `https://blog.journeymind.blog`

## 内容边界

- 项目官网放在对应项目仓库，例如 CampusNet Guard 的官网在 `mi179/campusnet-guard/site/`。
- 博客负责项目故事、复盘、教程和长期笔记。
- 不在博客仓库保存 token、私钥、服务器密码或未脱敏配置。
