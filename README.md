# KoalaRewardsHub 需求文档

文档站点基于 [Docsify](https://docsify.js.org/)，部署在 **GitHub Pages**。

- 在线地址（部署后）：`https://<你的用户名>.github.io/KoalaRewardsHubDoc/`
- 本地预览：在项目根目录执行 `npx docsify serve docs`，浏览器打开 http://localhost:3000

---

## GitHub Pages 部署配置

### 1. 在 GitHub 仓库里开启 Pages

1. 打开仓库 **Settings** → 左侧 **Pages**（Code and automation 下）
2. **Build and deployment** 里：
   - **Source** 选 **Deploy from a branch**
   - **Branch** 选 `main`（或你当前用的默认分支）
   - **Folder** 选 **/docs**
3. 点 **Save** 保存

### 2. 等待发布

推送代码后，GitHub 会自动用 `docs` 目录发布。几分钟后访问：

- 用户/组织页：`https://<用户名>.github.io/KoalaRewardsHubDoc/`
- 自定义域名（若已配置）：你设置的域名

### 3. 本项目已做的配置

- **`docs/.nojekyll`**：关闭 Jekyll，避免下划线等文件被忽略
- **`docs/404.html`**：自定义 404，错误链接会跳回文档首页

无需再改仓库或 GitHub 其它设置，按上面选好 Source = 分支 + `/docs` 即可。
