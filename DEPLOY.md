# 发布到 Cloudflare Workers

## 电脑上操作

1. 在 GitHub 新建一个空仓库，把本目录整体推送到 `main` 分支。
2. 登录 Cloudflare Dashboard，进入 **Workers & Pages → Overview → Create application → Workers → Import a repository**。
3. 连接 GitHub，选择这个仓库。
4. 构建设置选择静态资产项目：
   - Build command：留空
   - Deploy command：`npx wrangler deploy`
   - Root directory：`/`
5. 点击 **Deploy**。首次成功后 Cloudflare 会给出一个 `workers.dev` 公开网址。
6. 在项目设置中确认 **Builds → Branch control → Production branch** 为 `main`。以后每次 push 都会自动构建并发布。

## 以后更新

只需要修改 `public/index.html` 后：

```bash
git add public/index.html
git commit -m "update travel handbook"
git push origin main
```

推送后 Cloudflare Workers Builds 会自动发布。公开网址不需要登录，也不需要安装 App。
