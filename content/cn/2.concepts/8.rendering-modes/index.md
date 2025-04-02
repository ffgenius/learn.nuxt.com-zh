---
ogImage: true
---

# 渲染模式

Nuxt 支持各种渲染模式。\
具体来说，这些包括通用渲染（Universal Rendering）、客户端渲染（Client-Side Rendering）和混合渲染（Hybrid Rendering）。

默认情况下，通用渲染被选定。\
这些模式可以通过 `nuxt.config` 轻松切换。

## 通用渲染

在通用渲染中，服务器返回完全渲染的 HTML。\
这使用户能够立即访问应用程序的内容。

加载 HTML 后，浏览器还会加载 JavaScript 代码来构建需要交互的动态 UI。\
这个过程称为"水合"（hydration）。

在这个例子中，我们在 `app.vue` 中将 `count` 状态记录到控制台。\
当访问页面时，你可以在终端（服务器）和浏览器控制台中看到输出。

这意味着 Nuxt 在服务器上执行 Vue.js 代码以生成 HTML，然后在浏览器中再次运行相同的代码。\
这就是为什么它被称为"通用渲染"。

通用渲染的主要优点和缺点如下：

### 优点

- 性能\
  由于 HTML 在服务器上生成并由浏览器读取，比在浏览器中使用 JavaScript 生成内容更快。
- 搜索引擎优化（SEO）\
  网络爬虫可以直接索引页面内容，这对 SEO 有利。

### 缺点

- 开发限制\
  编写在服务器和客户端都能无缝运行的代码会有一些限制。
- 成本\
  需要服务器，这会产生运营成本。

更多详情，请参见[官方文档](https://nuxt.com/docs/guide/concepts/rendering#universal-rendering)。

## 客户端渲染

你可以通过在 `nuxt.config` 中设置 `ssr: false` 来启用客户端渲染。

```ts
// nuxt.config.ts
export default defineNuxtConfig({
  ssr: false
})
```

使用客户端渲染，应用程序在浏览器中渲染。\
浏览器下载并解析所有 JavaScript 代码，其中包含构建 UI 的指令，然后生成 HTML 元素。

客户端渲染的主要优点和缺点如下：

### 优点

- 开发速度\
  你只需要考虑应用程序在浏览器中的工作方式，而不必担心服务器集成。
- 成本效益\
  不需要服务器，因此基础设施成本较低。
- 离线能力\
  由于所有代码都在浏览器中运行，即使没有互联网连接，应用程序也可以继续工作。

### 缺点

- 性能\
  用户必须等待浏览器下载、解析和执行 JavaScript，这可能会影响用户体验。
- 搜索引擎优化（SEO）\
  索引和更新客户端渲染的内容需要时间，这比服务器渲染的 HTML 对 SEO 的友好度较低。

## 混合渲染

Nuxt 允许你使用路由规则为每个路由指定不同的缓存规则和渲染模式。

这是通过 `nuxt.config` 中的 `routeRules` 选项配置的。

更多详情，请参考[官方文档](https://nuxt.com/docs/guide/concepts/rendering#hybrid-rendering)。

```ts
export default defineNuxtConfig({
  routeRules: {
    // 主页在构建时预渲染
    '/': { prerender: true },
    // 博客列表页面按需生成，在后台重新验证，在 CDN 上缓存 1 小时（3600 秒）
    '/blog': { isr: 3600 },
    // 博客文章页面按需生成一次，直到下次部署前，在 CDN 上缓存
    '/blog/**': { isr: true },
    // 管理仪表板仅在客户端渲染
    '/admin/**': { ssr: false },
  }
})
```

## 挑战

设置客户端渲染并验证 Vue.js 代码仅在浏览器中运行。

要做到这一点：

1. 在 `nuxt.config` 中设置 `ssr: false`。
2. 在 `app.vue` 中将 `count` 状态记录到控制台。
3. 确认终端中没有输出。
4. 打开浏览器开发工具并验证控制台显示输出。

接下来，设置混合渲染并确认你可以为每个路由分配不同的缓存规则和渲染模式。

要做到这一点：

1. 在 `app.vue` 中使用 `NuxtPage` 组件渲染页面。
2. 在 `/pages/index.vue` 和 `/pages/foo.vue` 的 `script setup` 中添加控制台输出（任何消息都可以）。
3. 在 `nuxt.config` 中设置 `routeRules`，为 `/` 和 `/foo` 应用不同的缓存和渲染设置。\
   这次，为 `/foo` 设置 `ssr: false`。
4. 访问 `/` 并确认控制台输出同时出现在服务器和浏览器中。
5. 访问 `/foo` 并确认控制台输出仅出现在浏览器中。

:ButtonShowSolution{.bg-faded.px4.py2.mb3.rounded.border.border-base.hover:bg-active.hover:text-primary.hover:border-primary:50}

:::note
要验证渲染行为，重要的是不仅要检查控制台输出，还要使用浏览器的"网络"选项卡检查请求行为。

使用通用渲染，由于 HTML 在服务器上生成，你会在网络响应中看到一个完全填充的 `<div id="__nuxt">`。\
使用客户端渲染，HTML 最初将为空，然后由 JavaScript 填充。\
（JavaScript 将作为单独的下载请求可见）
:::
