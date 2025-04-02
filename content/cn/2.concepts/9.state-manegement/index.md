---
ogImage: true
---

# 状态管理

在 Vue.js 中，状态管理指的是在应用程序中管理响应式状态。\
[Vue.js 官方文档：状态管理](https://vuejs.org/guide/scaling-up/state-management)

当在多个组件之间共享状态时，Vue.js 允许使用响应式 API 进行简单的状态管理。\
[Vue.js 官方文档：使用响应式 API 进行简单状态管理](https://vuejs.org/guide/scaling-up/state-management#simple-state-management-with-reactivity-api)

然而，正如在 [SSR 注意事项](https://vuejs.org/guide/scaling-up/state-management#ssr-considerations) 中提到的，在 Nuxt 中使用 SSR 可能会导致[某些问题](https://vuejs.org/guide/scaling-up/ssr#cross-request-state-pollution)。

虽然 Vue.js 官方文档介绍了一个名为 [Pinia](https://pinia.vuejs.org/) 的状态管理库，但 Nuxt 提供的 `useState()` 组合式函数也是解决方案之一。\
（当然，[在 Nuxt 中使用 Pinia](https://nuxt.com/docs/getting-started/state-management#usage-with-pinia) 也是可行的。）

## useState()

[useState() 组合式函数](https://nuxt.com/docs/api/composables/use-state) 提供了一种简单的方式来管理 SSR 友好的状态并在组件之间共享。\
`useState()` 是一个 SSR 友好的 `ref()`，用于定义共享状态。\
如前所述，在 SSR 中使用 Vue.js 的响应式 API（如 `ref()`）进行跨组件状态管理可能会导致问题。\
因此，在 Nuxt 中，最佳实践是避免在 `<script setup>` 或 `setup()` 函数**外部**使用 `ref()` 定义状态，而是使用 `useState()`。

在本操作环境的示例中，状态使用 `"count"` 作为键在 `CounterA` 和 `CounterB` 组件之间共享。\
注意，当点击 `CounterA` 渲染的按钮时，`CounterB` 中的状态也会更新。

更多详情，请参阅 [Nuxt 官方文档：状态管理](https://nuxt.com/docs/getting-started/state-management)。

:::note
因为 `useState()` 中的数据将被序列化为 JSON，所以重要的是它不包含任何不能被序列化的内容，例如类、函数或符号。
:::
