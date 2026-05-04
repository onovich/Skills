---
name: gh-pages-action-deployer
description: 专注为当前基于 Vite/React/前端 等Web工程建立官方推崇的基于 GitHub Actions 自动化工作流部署至 GitHub Pages 的托管方案。
---

# GitHub Pages Action Deployer Skill

## 目标与职责
免除开发者手动编译代码或繁琐的 `gh-pages` 分支推送。用 GitHub 官方最新提供的 `actions/deploy-pages@v4` 来无缝代理静态前端资源上线流程。

## 实施经验与标准化步骤

1. **工程路由配置 (Vite 示例)**
   - 托管在 GitHub Pages 的网站如果没有绑自定义一级域名，往往会携带二级目录（如 `/RepoName/`）。
   - 修正 `vite.config.js` 等打包器的路由基座为：`base: '/YourRepositoryName/'`，防止 `index.html` 引用的 JS 或 CSS 出现 404 FileNotFound。

2. **编写 Actions 自动化构建文件**
   - 建立 `.github/workflows/deploy.yml`。
   - 必须配置核心权限设定，这是官方动作运行的核心要求：
     ```yaml
     permissions:
       contents: read
       pages: write
       id-token: write
     ```
   - 确保 `Setup Node` 的版本能向下兼容最新的打包器生态（如指明 `node-version: 20` 防止 EBADENGINE 老旧报错）。
   - 工作流须划分 `build` 与 `deploy`：
     - `build`: 负责安装 (`npm ci`)，构建 (`npm run build`) 并归档输出制品 (`uses: actions/upload-pages-artifact@v3` with `path: dist`)。
     - `deploy`: `needs: build` 的强校验，然后发布为官方服务 (`uses: actions/deploy-pages@v4`)。

3. **指导用户手动配置控制台设定**
   - 虽然代码和流水线提交至远端，但 GitHub Repo 的安全策略不允许未经准许的 Actions 提供静态服务篡改。
   - 必须在处理结尾告知用户：前往 `Settings -> Pages -> Source` 将部署从默认分支修改勾选为 **「GitHub Actions」**。

4. **自定义域名 (CNAME) 处理**
   - 检查用户是否需要使用 CNAME 自定域。若在 `Deploy via Actions` 策略下需要绑定，请确保在仓库静态根目录下添加了 CNAME。（注：若是 `gh-pages` 策略才在 Action 中配置 `cname` 参数，必须保持警惕）。