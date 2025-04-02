---
ogImage: true
---

# 数据获取

构建实用应用程序时，数据获取是一个基本功能。\
数据获取指的是从 API 或数据库检索数据。

Nuxt 提供了有用的函数，如 `useFetch`、`useAsyncData` 和 `$fetch`，以便方便地处理数据获取。

简而言之：

- `useFetch` 是在组件的 setup 函数中处理数据获取的最简单方法。
- `$fetch` 非常适合基于用户交互进行网络请求。
- `useAsyncData` 与 `$fetch` 一起工作，提供更精细的控制。

https://nuxt.com/docs/getting-started/data-fetching

其中，`useFetch` 是最容易使用的。实际上，它是 `useAsyncData` 和 `$fetch` 的便捷包装器。

以下是使用方法：

```vue
<script setup lang="ts">
const { data, pending, error, refresh, clear } = await useFetch('/api/modules')
</script>
```

具体来说，它提供了以下功能：

- 在服务器和客户端上运行\
  由于 `useFetch` 在服务器和客户端都可以工作，即使在通用渲染期间也可以轻松获取数据。
- 数据缓存\
  当在服务器上调用 API 时，数据会传输到客户端，防止在客户端重复获取。
- 类型化的请求 URL 和响应\
  通过在 `server` 目录中实现 API，请求 URL 和响应类型会自动推断。

更多详情，请参阅[官方文档](https://nuxt.com/docs/api/composables/use-fetch)。

如果需要更精细的控制，可以使用 `useAsyncData` 或 `$fetch` 进行更高级的数据获取。

https://nuxt.com/docs/api/composables/use-async-data

https://nuxt.com/docs/api/utils/dollarfetch

## 挑战

1. 检查 API 是否工作
   在 `server/api/todos/index.ts` 中添加第四个待办事项，然后点击刷新按钮验证数据是否更新。

2. 检查类型推断
   在 `server/api/todos/index.ts` 中向 Todo 添加 `completed` 属性，并确认 `useFetch` 类型相应更新。

:ButtonShowSolution{.bg-faded.px4.py2.mb3.rounded.border.border-base.hover:bg-active.hover:text-primary.hover:border-primary:50}
