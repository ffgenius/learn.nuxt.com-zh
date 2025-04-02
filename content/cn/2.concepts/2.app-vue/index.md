---
ogImage: true
---

# 应用程序入口

在 Nuxt 中，`app.vue` 作为应用程序的入口点。

你可以定义一个最小化的 `app.vue` 来管理你的应用程序并开始实现你自己的逻辑（可选）。

在此示例中，**`app.vue`** 只是在屏幕上渲染一条消息。

`pages/` 目录（将在下一章介绍）是可选的。如果它不存在，Nuxt 将不会将 `vue-router` 作为依赖项包含在内。

这对于不需要路由的登陆页面或应用程序很有用。

此外，你可以使用 `nuxt.config.ts` 配置你的应用程序（它也支持 `nuxt.config.js` 和 `nuxt.config.mjs`）。

默认情况下，Nuxt 的配置适用于大多数用例，但你可以根据需要覆盖设置。

有关更详细的配置选项，请参阅 [Nuxt 文档](https://nuxt.com/docs/getting-started/configuration)。

要获取 Nuxt 应用程序的更多功能，让我们继续学习[路由](/concepts/routing)部分，了解如何使我们的应用程序支持多个页面。
