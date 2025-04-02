---
ogImage: true
---

# 自动导入

自动导入也是 Nuxt 的核心概念之一。

https://nuxt.com/docs/guide/concepts/auto-imports

自动导入是一项允许组件、组合式函数和 [Vue.js API](https://vuejs.org/api/) 在整个应用程序中被自动导入和使用的功能，无需显式导入。\
与传统的全局声明不同，Nuxt 保留了类型信息、IDE 自动完成和提示，同时在生产代码中仅包含实际使用的内容。

得益于 Nuxt 的目录结构约定，`components/`、`composables/` 和 `utils/` 可以被自动导入。\
在这个例子中，在 `components` 目录中定义的 `Counter.vue` 组件和在 `composables` 目录中定义的 `useCounter.ts` 都是在没有显式导入的情况下使用的。\
在 `app.vue` 中使用了 Counter 组件，而在 `Counter.vue` 中使用了 `useCounter()`。

此外，Nuxt 提供了几个组件、组合式函数和工具函数。\
一个例子是在[路由](/concepts/routing)部分介绍的 `NuxtLink` 组件。\
其他例子包括用于数据获取的 `useFetch()` 组合式函数，用于访问运行时配置的 `useRuntimeConfig()`，以及用于页面导航的 `navigateTo()` 工具函数。\
由于还有很多其他内容，请参阅 Nuxt 官方文档中关于 [Components](https://nuxt.com/docs/api/components)、[Composables](https://nuxt.com/docs/api/composables) 和 [Utils](https://nuxt.com/docs/api/utils) 部分的完整列表。

Nuxt 还支持显式导入，可以使用 `#imports` 进行。

```ts
import { computed, ref } from '#imports'

const count = ref(1)
const double = computed(() => count.value * 2)
```

可以在 `nuxt.config.ts` 中选择不使用自动导入功能。\
在这种情况下，将需要像上面那样进行显式导入。

```ts
// nuxt.config.ts
export default defineNuxtConfig({
  imports: {
    autoImport: false
  }
})
```

## 挑战

尝试在 `utils/double.ts` 文件中实现一个可自动导入的函数。

你可以创建任何函数，但作为示例，让我们实现一个返回给定数字两倍的 `double()` 函数。\
一旦你实现了该函数，在 `app.vue` 的模板部分使用它来在屏幕上显示加倍的值。

:ButtonShowSolution{.bg-faded.px4.py2.rounded.border.border-base.hover:bg-active.hover:text-primary.hover:border-primary:50}
