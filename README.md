# kkgindex · 咳咳怪的主页

基于 [Forty by HTML5 UP](https://html5up.net) 模板的个人主页 / 站点导航，纯静态页面，可直接部署到 GitHub Pages、Vercel、Netlify 或任意静态服务器。

## 项目结构

```
kkgindex/
├── index.html          # 主页（Banner + 站点导航磁贴）
├── landing.html        # 模板示例：落地页
├── generic.html        # 模板示例：通用页
├── elements.html       # 模板示例：组件演示页
├── images/             # 站点图片（全部本地化，无外链）
│   ├── banner-bg.webp  # 首屏 Banner 背景图
│   ├── tile-*.webp/jpg # 导航磁贴封面图
│   └── pic*.jpg        # 示例页占位图
└── assets/
    ├── css/            # 编译后的样式（main.css / noscript.css）
    ├── js/             # jQuery 及模板脚本（全部本地引用）
    └── sass/           # 样式源码（如需修改样式请编辑此处后重新编译）
```

## 优化说明

本次优化在保留原有视觉与交互的前提下进行了以下改进：

### 性能与可靠性
- **资源全部本地化**：原页面引用 `s2.loli.net` 图床 5 张图片、`js.007.al` CDN 的 jQuery，
  现全部改为本地文件，消除第三方依赖（图床失效 / CDN 不稳定 / 跨境请求慢等风险）。
- **脚本延迟加载**：所有 `<script>` 添加 `defer`，HTML 解析不再被 JS 阻塞。
- **首屏图片预加载**：`<link rel="preload">` 提前加载 Banner 背景图（LCP 关键资源）。
- **清理无用资源**：将 `bg_1~bg_5` 中已使用的背景图整理为带语义名称的 `banner-bg` / `tile-*` 文件，删除重复副本及未被引用的 `pic01/02/04/05/06`、`banner.jpg`；项目体积从约 10MB 降至约 5MB。

### SEO 与可访问性
- 补充 `lang="zh-CN"`、`meta description`、`canonical`、Open Graph、Twitter Card、`theme-color`。
- 图片补充 `alt` 文本与 `decoding="async"`。
- 导航与菜单补充 `aria-label`。
- 修复“未完待续”磁贴的空链接（`href=""` 会刷新当前页，现改为不可点击标题）。
- 统一 HTML 缩进格式。

## 如何修改

- **修改站点链接 / 文案**：编辑 `index.html` 中 `#menu` 与 `#one` 区块。
- **修改样式**：编辑 `assets/sass/` 下的源文件后重新编译为 `assets/css/main.css`：
  ```bash
  npm install -g sass
  sass assets/sass/main.scss assets/css/main.css --style compressed
  ```
- **更换站点域名**：搜索 `index.html` 中的 `333361.xyz`（canonical / og:url / og:image）。

## 部署

任意静态托管直接上传本目录即可，无需构建步骤。例如 GitHub Pages：

1. 将仓库推送到 GitHub
2. Settings → Pages → 选择分支与根目录
3. 访问 `https://<用户名>.github.io/<仓库名>/`

## 许可

- 页面模板：[Forty by HTML5 UP](https://html5up.net)，CCA 3.0 许可（保留署名）
- 站点图片：[みふる（pixiv:488766）](https://www.pixiv.net/users/488766/)，版权归原作者所有
