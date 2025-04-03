# Nuxt 教程互动环境

## 关于本仓库

本仓库为 [Nuxt 教程互动环境](https://github.com/nuxt/learn.nuxt.com) 的中文翻译版本。
- 如发现中文翻译错误或有优化建议，欢迎直接向本仓库提交 PR；
- 如需修复 Bug 或添加新功能，请前往原仓库提交 PR。待官方合并后，我们会第一时间同步更新至本仓库。

[英文文档](./README-EN.md)

> [!警告]
> 本项目的架构已经准备就绪，但教程内容仍在开发中，欢迎贡献！

这是一个用于学习 Nuxt 的互动教程和实践环境。由 [Nuxt](https://nuxt.com/docs) 和 [WebContainers](https://webcontainers.io/) 提供支持。

[📖 learn.nuxt.com](https://learn.nuxt.com).

> 灵感来源于 [learn.svelte.dev](https://learn.svelte.dev)。

## 项目开发过程

Anthony Fu 正在直播中从零开始构建这个项目。
你可以在 [YouTube](https://www.youtube.com/playlist?list=PL4ETc_mXFfxUGiY852jH3ctljnI2e9Rax) 上观看完整过程的录像。

## 贡献指南

### 开发环境

要在本地运行此项目，你需要安装 [Node.js v22.0+](https://nodejs.org/en/) 和 [pnpm](https://pnpm.io/)。

克隆仓库后，运行以下命令安装依赖：

```bash
pnpm install
```

然后，运行以下命令启动开发服务器：

```bash
pnpm dev
```

开发服务器将在 [http://localhost:3000](http://localhost:3000) 运行。

### 内容结构

教程内容位于 `content/` 目录中。每个路由包含一个数字前缀（`1.`）来指示顺序，这个前缀在最终的 URL 中会被移除。对于每个路由，我们使用带有 `index.md` 的文件夹来提供额外文件。可以在 `index.md` 文件同目录下放置 `.template` 文件夹，为互动环境提供模板。

- `.template/index.ts` - 指示该指南的元数据，如启用/禁用功能、文件过滤器等。
- `.template/files/**` - 当用户导航到该指南时，将被复制到互动环境的文件，与 `template/basic/` 下的基本模板合并。
- `.template/solutions/**` - 该指南中任务的可选解决方案，与指南文件合并。

## 待办事项

- [ ] 内容
  - [ ] 允许每个指南配置文件过滤器
  - [ ] 切换解决方案时保存用户更改
  - [ ] 教程任务的验证功能
  - [x] 搜索功能
    - [x] 命令面板中的搜索
    - [x] 搜索按钮
  - [x] 导航
    - [x] 指南大纲的下拉菜单
    - [x] 面包屑导航
    - [x] 上一页/下一页按钮
  - [x] 嵌入 Nuxt 文档（更新 CORS 头）
  - [x] 在指南之间导航时只进行必要的更改
  - [x] 在不同指南上切换互动环境
  - [x] 允许每个指南切换功能
  - [x] 每个指南的解决方案
  - [x] "编辑此页面"按钮
- [x] SEO
  - [x] OG 图像
  - [x] Meta 标签
  - [x] 网站地图
- [x] Command K 系统
- [ ] 关于页面
- [ ] 欢迎屏幕
- [ ] 尝试使用 https://ark-ui.com/docs/components/splitter
- [x] 显示互动环境的发布时间
- [x] 显示容器中的 Nuxt 和 Vue 版本
- [x] 模板的自定义打包器（替换 `import.meta.glob`，创建静态虚拟模块）
- [x] Monaco 编辑器和 Volar
  - [x] 将 Volar 连接到 WebContainer 文件系统
- [x] 文件树
- [x] [添加交互式 shell](https://webcontainers.io/tutorial/7-add-interactivity)
- [x] 基本编辑器
- [x] 将逻辑从 Vue SFC 重构到组合式函数
- [x] 重构以添加 Pinia
- [x] 框架到父级的通信
- [x] 同步基本样式
- [x] 重启服务器按钮
- [x] 打开/关闭终端面板
- [x] 提取"互动环境注入"工具
- [x] 将项目下载为 zip

## 许可证

[MIT](./LICENSE)
